---
tags: ["ai-security", "guardrails", "red-team", "sandboxing", "interview-prep"]
priority: critical
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/18-strix"]
created: 2026-09-07
source: "_research/core-ai-security-defenses.md"
---

# Defense-in-Depth Architecture

> No single defense is sufficient. The robust pattern is to compose many defenses, each catching the failures the others miss. The composition itself is a design artifact — it must be deliberately architected, regularly tested, and continuously improved

No single defense is sufficient. The robust pattern is to compose many defenses, each catching the failures the others miss. The composition itself is a design artifact — it must be deliberately architected, regularly tested, and continuously improved.

#### 10.1 The composition

A canonical defense-in-depth architecture for an LLM application, ordered by where in the stack the defense lives:

```
┌──────────────────────────────────────────────────────────────────────┐
│                          USER / ATTACKER                              │
└──────────────────────────────────────────────────────────────────────┘
                                 │
                                 ▼
┌──────────────────────────────────────────────────────────────────────┐
│  Layer 1 — EDGE / NETWORK                                             │
│  - WAF, DDoS protection, rate limiting                                │
│  - Bot detection, CAPTCHAs                                            │
│  - Per-IP/per-user rate caps                                          │
│  - Geo-blocking where appropriate                                     │
└──────────────────────────────────────────────────────────────────────┘
                                 │
                                 ▼
┌──────────────────────────────────────────────────────────────────────┐
│  Layer 2 — INPUT NORMALIZATION                                        │
│  - Unicode normalization (NFKC)                                       │
│  - Strip zero-width chars, control sequences, escape sequences        │
│  - Decode encodings (base64, percent, hex) before classification      │
│  - Length cap per input                                               │
└──────────────────────────────────────────────────────────────────────┘
                                 │
                                 ▼
┌──────────────────────────────────────────────────────────────────────┐
│  Layer 3 — INPUT CLASSIFIERS (parallel, vote)                         │
│  - Prompt-injection classifier (e.g., Llama Guard 3, Azure PS)        │
│  - Content harm classifier (e.g., OpenAI Moderation)                  │
│  - Topic / domain classifier (denied topics)                          │
│  - PII detector (block on PII, anonymize)                             │
│  - Jailbreak-specific classifier (DAN, role-play, encoding)           │
└──────────────────────────────────────────────────────────────────────┘
                                 │
                                 ▼
┌──────────────────────────────────────────────────────────────────────┐
│  Layer 4 — RETRIEVAL                                                  │
│  - Source allowlist                                                   │
│  - Document sanitization (strip HTML, scripts, hidden text)           │
│  - Trust labeling per chunk                                           │
│  - Anomaly scoring (perplexity, embedding distance)                   │
│  - Citation grounding check                                           │
└──────────────────────────────────────────────────────────────────────┘
                                 │
                                 ▼
┌──────────────────────────────────────────────────────────────────────┐
│  Layer 5 — LLM CALL                                                   │
│  - System prompt (least-privilege, role-pinned)                       │
│  - Tool allowlist (closed set, schema-validated)                      │
│  - Per-tool scope (path, recipient, table, URL)                       │
│  - Structured output (JSON Schema enforced)                           │
└──────────────────────────────────────────────────────────────────────┘
                                 │
                                 ▼
┌──────────────────────────────────────────────────────────────────────┐
│  Layer 6 — OUTPUT VALIDATION                                          │
│  - Schema validation (Pydantic / Zod / JSON Schema)                   │
│  - Output classifier (separate from LLM)                              │
│  - Groundedness check (for RAG)                                       │
│  - Action allowlist + scope check (for agents)                        │
│  - Human-in-the-loop for high-stakes actions                          │
└──────────────────────────────────────────────────────────────────────┘
                                 │
                                 ▼
┌──────────────────────────────────────────────────────────────────────┐
│  Layer 7 — EXECUTION SANDBOX (for code-execution agents)              │
│  - Per-task microVM (Firecracker) or container (gVisor)                │
│  - Network egress allowlist                                           │
│  - Read-only filesystem, scratch /tmp                                 │
│  - Resource ceilings (CPU, memory, wall-clock)                        │
│  - Per-session credentials, short TTL                                 │
└──────────────────────────────────────────────────────────────────────┘
                                 │
                                 ▼
┌──────────────────────────────────────────────────────────────────────┐
│  Layer 8 — DOWNSTREAM (APIs, services, data stores)                   │
│  - Per-user, per-action scoped credentials                            │
│  - Service-to-service auth (mTLS, OIDC)                               │
│  - Database row-level security, table-level allowlists                │
│  - Outbound call allowlist                                            │
└──────────────────────────────────────────────────────────────────────┘
                                 │
                                 ▼
┌──────────────────────────────────────────────────────────────────────┐
│  Layer 9 — OBSERVABILITY                                              │
│  - Structured logging of every LLM call                               │
│  - Anomaly detection (refusal rate, prompt length, tool patterns)     │
│  - Canary tokens in system prompt                                     │
│  - Eval-set regression alarms                                         │
│  - Rate and pattern alarms                                            │
│  - Audit log retention (90+ days)                                     │
│  - Kill switch                                                       │
└──────────────────────────────────────────────────────────────────────┘
```

Each layer can independently block a request. The composition is intentionally redundant — if the input classifier misses a prompt injection, the retrieval layer or the output classifier should still catch it. If all three miss, the audit log captures the incident for post-hoc detection.

#### 10.2 Design principles

- **Defense in depth.** No single layer is sufficient. The composition must catch what each layer misses.
- **Fail closed.** When a classifier is uncertain, the default is to block. "Refuse" is safer than "let it through."
- **Out-of-band verification.** The LLM never gets to decide whether its own output is safe; a separate model or rule-based check does.
- **Code-enforced security boundaries.** Anything the LLM "decides" to do must be authorized by code that does not depend on the LLM.
- **Immutable logging.** Logs are write-once. An attacker who compromises the app cannot rewrite the history.
- **Kill switch.** Always possible to stop the system in seconds.

#### 10.3 Testing the composition

Test each layer in isolation (unit tests for classifiers) and the composition end-to-end (integration tests for the full request flow). A regression in any layer should fail CI. Run a full red-team engagement quarterly, with findings tracked in the same backlog as traditional security findings.

#### 10.4 Common compositions by deployment type

**Internal employee assistant (low stakes, low scale).**
- Layer 1: basic WAF.
- Layer 3: OpenAI Moderation on input.
- Layer 5: least-privilege system prompt + structured output.
- Layer 6: schema validation.
- Layer 9: structured logging, basic anomaly detection.

**Customer-facing chatbot (medium stakes, medium scale).**
- All of the above, plus:
- Layer 3: Llama Guard 3 + Azure Prompt Shields in parallel.
- Layer 6: separate output classifier.
- Layer 9: full anomaly detection + canary tokens.

**RAG over public web (high stakes, high scale).**
- All of the above, plus:
- Layer 4: full retrieval filtering (sanitize, trust label, anomaly score).
- Layer 6: groundedness check on every claim.
- Layer 9: source citation integrity monitoring.

**Agentic system that can send email / modify files (high stakes).**
- All of the above, plus:
- Layer 5: tight tool allowlist + per-tool scopes.
- Layer 6: human-in-the-loop for Tier 2+ actions.
- Layer 7: sandbox for any code execution.
- Layer 8: per-user, per-action credentials.
- Layer 9: full audit log + kill switch.

**Code-execution agent (very high stakes, low scale).**
- All of the above, plus:
- Layer 7: per-task microVM with strict egress allowlist.
- Layer 8: per-session credentials, never shared.
- Layer 9: rate limits, dollar caps, real-time on-call alert on anomalous tool calls.

#### 10.5 The full tooling summary

| Tool | Type | Owner | Primary use |
|---|---|---|---|
| OpenAI Moderation | API | OpenAI | Input/output harm classification |
| Perspective API | API (sunsetting) | Google/Jigsaw | Toxicity scoring (legacy) |
| ShieldGemma | Open model | Google | Self-hosted safety classifier (Gemma 2) |
| Llama Guard 3 | Open model | Meta | LLM-based input/output safeguard |
| NeMo Guardrails | OSS framework | NVIDIA | Programmable Colang-based rails |
| Azure AI Content Safety | Suite | Microsoft | Full guardrail stack incl. Prompt Shields |
| AWS Bedrock Guardrails | Suite | AWS | Cross-model guardrails for Bedrock |
| Garak | OSS scanner | NVIDIA | Vulnerability probing |
| PyRIT | OSS framework | Microsoft | Multi-turn attack orchestration |
| promptfoo | OSS eval/RT | Community | CI/CD-friendly red team |
| HarmBench | Benchmark | CAIS | Standardized red-team eval |
| JailbreakBench | Benchmark | Preamble / community | Jailbreak-specific eval |
| Constitutional AI | Method | Anthropic | Training-time harmlessness |
| GCG / AutoDAN / PAIR | Methods | Various | Adversarial suffix attacks (for testing) |
| SmoothLLM | Method | Robey et al. | Inference-time perturbation defense |
| CaMeL | Method | Microsoft Research 2025 | Dual-LLM indirect-injection defense |
| Firecracker | MicroVM | AWS | Per-task code-execution sandbox |
| gVisor | User-space kernel | Google | Container-level syscall filtering |
| MITRE ATLAS | Knowledge base | MITRE | Threat + mitigation catalog |

## Related

- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — all defenses leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these defenses
