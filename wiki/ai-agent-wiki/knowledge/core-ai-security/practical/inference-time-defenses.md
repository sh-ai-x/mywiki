---
tags: ["ai-security", "guardrails", "red-team", "sandboxing"]
priority: medium
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/18-strix"]
created: 2026-09-07
source: "_research/core-ai-security-defenses.md"
---

# Inference-Time Defenses

> Inference-time defenses operate on the model's inputs and outputs at call time, without modifying the model weights. They are the most accessible layer for application developers (no fine-tuning infrastructure needed) and the most rapidly evolving — new techniques appear every quarter. The downsi

Inference-time defenses operate on the model's inputs and outputs at call time, without modifying the model weights. They are the most accessible layer for application developers (no fine-tuning infrastructure needed) and the most rapidly evolving — new techniques appear every quarter. The downside: every technique adds latency and compute cost, and most are partially bypassable by determined attackers. Use them as a layer, not a single defense.

#### 8.1 Output sanitization (the LLM02 defense)

Strip or escape dangerous substrings from the model output before handing it to downstream code interpreters, browsers, shell, or SQL — even if the prompt was safe, treat the output as untrusted. The LLM02 Insecure Output Handling risk is the second-most-common production vulnerability after indirect prompt injection. Specific patterns:

- **HTML / Markdown sanitization.** If the model output is rendered as HTML, run it through an HTML sanitizer (DOMPurify, Bleach) that strips `<script>`, `<iframe>`, `on*` attributes, `javascript:` URLs.
- **SQL escape.** Never concatenate model output into a SQL query. Use parameterized queries exclusively. If the model is supposed to produce SQL, validate the parse with a SQL parser (sqlglot, sqlparse) and reject anything that isn't a `SELECT` against a table on the allowlist.
- **Shell escape.** Same principle: never `os.system(model_output)`. If the model is supposed to invoke a shell, pass the command as a list of args to `subprocess.run([...], shell=False)`.
- **URL allowlist.** If the model emits URLs (e.g., for image generation or link rendering), check each URL against an allowlist of hostnames and against a redirect chain; do not follow redirects to unknown hosts.
- **Path canonicalization.** If the model emits file paths, canonicalize them and verify they are under the allowed base directory.
- **JSON schema validation.** If the model is supposed to emit JSON, validate against a strict JSON Schema; reject any object that doesn't match.

#### 8.2 Citation / grounding enforcement

For any RAG system, the LLM should be required to emit structured citations for every factual claim. A claim is *grounded* if it is supported by the cited retrieved source. Defenses:

- **Structured output.** Force the model to emit JSON with explicit citations: `{ "claim": "...", "citations": ["snippet_id_1", "snippet_id_2"] }`.
- **Citation verification.** After generation, run a separate model (Azure Groundedness detection, in-house NLI classifier, or a separate LLM-as-judge) to verify that each citation actually supports the claim. Unsupported claims are dropped or flagged.
- **Source attribution UI.** Show the user the cited source inline; let them click through. Users can spot hallucinated citations; this is also a regulatory requirement under the EU AI Act for high-risk systems.
- **Citation budget.** Reject any claim that cites more than N distinct sources; this prevents the LLM from "shoring up" weak claims with a long list of dubious references.

#### 8.3 Perplexity-based detection

Compute the per-token log-probability of the user prompt (and of retrieved chunks). Adversarial prompts — especially optimized suffixes from GCG, AutoDAN, and other attack-generation algorithms — often have anomalously low or high perplexity relative to the natural-language distribution.

- **SmoothLLM** (Robey et al. 2023, arXiv:2310.03671). Perturb the input (swap random characters, random words, paraphrasing) N times; run the model on each perturbed version; aggregate outputs by majority vote. Adversarial suffixes are highly sensitive to perturbation, so the perturbations produce diverse outputs while the natural prompt produces consistent outputs. A consistency drop is a strong attack signal.
- **PHD (Perplexity-based Hardness-aware Defense).** Compute the per-token log-probability of the user prompt; reject prompts whose perplexity is below a calibrated threshold (too "confident") or above another threshold (too unusual). Effective against GCG and similar attacks; less effective against semantic jailbreaks that are grammatical English.
- **Windowed perplexity.** Compute perplexity over the *last* K tokens of the prompt; this catches suffix attacks that append a long gibberish string to a natural prompt.

Caveat: perplexity alone is bypassable. An attacker can craft a natural-English prompt that achieves the same attack goal (semantic jailbreak); perplexity will not flag it. Use perplexity as one signal in a multi-signal classifier, not as a primary defense.

#### 8.4 Self-consistency and chain-of-verification

- **Self-consistency.** Sample N completions from the model (with temperature > 0); count the most common final answer. Adversarial prompts often produce unstable outputs; honest prompts produce consistent ones. Useful for math, factuality, and classification tasks.
- **Chain-of-verification (CoVe).** After the model produces a draft answer, ask it to generate verification questions about the answer, answer them independently, and revise the original answer based on the verification. Catches hallucinated facts and self-contradictions.
- **Constitutional filtering.** After generation, ask a separate model to critique the output against a written policy (the "constitution"); reject or rewrite outputs that fail. A practical application of Constitutional AI principles at inference time.

#### 8.5 Judge-model filtering

At inference, route the model's draft output through a *separate* judge model that scores harmfulness, helpfulness, instruction-adherence, and other quality dimensions. The judge:

- Should be a *different* model family than the application model (e.g., if your app uses GPT-4o, use Claude as the judge) to avoid correlated failures.
- Should be a strong model (frontier-class) so it can catch subtle issues.
- Should produce a structured verdict (`{ "safe": true|false, "score": 0.0-1.0, "reason": "..." }`).
- Should run *after* the structural defenses (schema validation, output sanitization) so the judge only sees well-formed output.
- Should be cheap enough to run on every request. A typical 8B classifier or a single judge-LLM call adds 100-500ms and $0.001-0.01 per request.

#### 8.6 Detection of jailbreak categories

Specialized techniques for specific jailbreak classes:

- **Encoding / obfuscation detection.** Detect base64, ROT13, leet-speak, and other encodings; either refuse or auto-decode before the main model call. Many "jailbreaks" published online are simply encoded harmful prompts that the safety classifier missed.
- **Multi-language detection.** Translate low-resource language input into English before the safety classifier; classifier coverage of low-resource languages is weak.
- **Token-splitting detection.** Detect prompts that split a harmful word across many tokens (e.g., "h o w  t o  m a k e  a  b o m b"); refuse.
- **Long-context attacks.** Cap the effective context window or apply attention-pattern analysis to detect "lost in the middle" attacks where the adversarial instruction is buried in a long document.

#### 8.7 Cost-aware defense

Inference-time defenses are bounded by latency and cost budgets. A typical production stack:

| Defense | Latency | Cost per request | Robustness |
|---|---|---|---|
| Input classifier (e.g., Llama Guard 3) | 50–200ms | $0.0001 | Moderate |
| LLM-as-judge (separate model) | 500–1500ms | $0.005 | High |
| SmoothLLM (5 perturbations) | 2–5x base call | 5x base | High (against suffixes) |
| Self-consistency (5 samples) | 5x base call | 5x base | Moderate |
| Full pipeline (classifier + judge + consistency) | 1–3s | $0.02–0.05 | High |

For high-stakes actions (Tier 3 in the agent reversibility taxonomy), run the full pipeline. For low-stakes (Tier 0), the input classifier may be enough. The cost discipline matters: defense that you can't afford to run on every request is a defense you won't run.

## Related

- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — all defenses leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these defenses
