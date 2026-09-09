---
tags: ["prompt-injection", "jailbreak", "adversarial"]
priority: medium
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/18-strix"]
created: 2026-09-07
source: "_research/core-ai-security-threats.md"
---

# Detection & Monitoring

> Detection coverage is uneven across attack classes — best for training-time and supply-chain (because signatures exist), worst for indirect prompt injection (because it is content-dependent)

Detection coverage is uneven across attack classes — best for training-time and supply-chain (because signatures exist), worst for indirect prompt injection (because it is content-dependent).

| Attack class | Detection approach | State of tooling (2026) |
|---|---|---|
| Direct prompt injection | Heuristic regex, intent classifiers (PromptShield, Lakera Guard, Rebuff) | Moderate — adversarial robustness still weak |
| Indirect prompt injection | Provenance tags, "data vs instruction" delimiters, dual-LLM pattern | Weak — no general solution |
| Jailbreaks (GCG, DAN, Crescendo) | Perplexity filters, judge models, HarmBench | Strong — open benchmarks + automated judges |
| Data poisoning | Dataset integrity hashes, activation clustering, Neural Cleanse | Moderate — requires dataset access |
| Backdoors (weight-level) | Neural Cleanse, STRIP, ABS, Tabor | Moderate — academic tools, slow |
| Membership inference | Output calibration, DP-SGD, confidence rounding | Strong — well-understood mitigations |
| Training-data extraction | Output filtering, PII scrubbers, exposure auditing | Moderate — false positives trade off |
| Adversarial examples | Adversarial training, randomized smoothing, certified defenses | Strong for vision; weak for LLMs |
| Supply-chain RCE | Picklescan, safetensors, Sigstore signing | Strong — community standard emerging |
| Agent tool misuse | Per-tool allow/deny, action budgets, audit logs | Moderate — depends on agent framework |
| MCP tool poisoning | Description sanitization, signature verification, version pinning | Weak — early days |

Defense-in-depth is universally recommended: assume any single layer will be bypassed.

### 13.1 Detection tooling landscape (2026)

| Tool / Vendor | Class | Notes |
|---|---|---|
| **Lakera Guard** | IPI / jailbreak detection | Commercial API; used by Fortune 500 for input scanning |
| **PromptShield (Microsoft)** | IPI / jailbreak detection | Released as part of Azure AI Content Safety |
| **Rebuff** | Open-source IPI detection | Multi-layer: heuristics + LLM self-check + canary tokens |
| **Picklescan** | Supply-chain pickle scanning | Static analysis for malicious pickle payloads[^jrog-pickle] |
| **Model Signing (Sigstore / cosign)** | Model provenance | Cryptographic attestation for model weights |
| **HarmBench / JailbreakBench** | Red-team evaluation | Standardized attack strings + judges |
| **MITRE ATLAS Navigator** | Threat intelligence | ATT&CK-style mapping of AI/ML TTPs[^mitre-atlas] |
| **HiddenLayer / JFrog / Snyk** | Supply-chain ML scanning | Continuous scanning of model hubs and registries |
| **NeMo Guardrails (NVIDIA)** | Agent runtime constraints | Programmable guardrails for LLM tool calls |
| **Constitutional AI (Anthropic)** | Output self-checking | Secondary model validates primary model outputs |
| **Azure AI Content Safety** | Output filtering | PII / harm filters applied to LLM responses |

### 13.2 Operational practices that move the needle

Empirical observations from the 2024–2026 incident corpus suggest these practices have the highest marginal impact:

1. **No secrets in prompts.** Treat the system prompt as public the moment it ships.
2. **Tool least-privilege.** Strip `exec`, `shell`, `write_file` from default tool sets. Add only with explicit human approval.
3. **Provenance-tag every retrieved chunk.** A retrieved-document tag visible to the model itself reduces (but does not eliminate) IPI success.
4. **Mandatory human-in-the-loop for irreversible tool calls.** Email-send, file-delete, payment, credential-rotation all require human confirmation.
5. **Red-team before every model upgrade.** Many regressions in safety properties are introduced by capability fine-tunes; test for jailbreak / IPI / overrefusal before each release.
6. **Audit-log every tool call with full input/output.** Replayable logs are the only reliable incident-response tool for agentic systems.
7. **Treat model hubs as package managers.** Same hygiene as npm / PyPI: hash-pin, scan, sign.

---

## Related

- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — all threats leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these threats
