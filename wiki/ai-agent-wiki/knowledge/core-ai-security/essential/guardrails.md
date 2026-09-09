---
tags: ["guardrails", "ai-security", "red-team", "sandboxing", "interview-prep"]
priority: critical
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/18-strix"]
created: 2026-09-07
source: "_research/core-ai-security-defenses.md"
---

# Guardrails (input filters, output validators, content classifiers)

> Guardrails are the first line of defense for any LLM application. They are most useful as a *layered* set of checks — input classifiers, output classifiers, and topic/format constraints — rather than as a single silver-bullet model. The principle: classify or constrain at the boundary of the LLM 

Guardrails are the first line of defense for any LLM application. They are most useful as a *layered* set of checks — input classifiers, output classifiers, and topic/format constraints — rather than as a single silver-bullet model. The principle: classify or constrain at the boundary of the LLM call, then trust the LLM only with structured, validated inputs and outputs.

#### 1.1 Off-the-shelf content classifiers

**OpenAI Moderation API.** The `omni-moderation-latest` model is free and accepts both text and image (up to 20 MB; no audio). It classifies input and output independently across `hate`, `harassment`, `self-harm`, `sexual`, and `violence`, returning a `flagged` boolean plus per-category scores. Two call modes: standalone `/v1/moderations` or inline with a Responses/Chat Completions request. Design heuristic: run moderation on **both** input (to filter user-supplied prompts) and output (to catch model regressions or jailbreak-induced leakage). Free, no rate limit published, no SLA — do not depend on it for mission-critical filtering, but ideal as one layer in a multi-layered pipeline. Old `text-moderation-*` models are deprecated; `omni-moderation-latest` is the only forward-compatible endpoint as of 2026.

**Perspective API.** Jigsaw/Google's machine-learned comment-toxicity scorer that historically returned scores for `TOXICITY`, `SEVERE_TOXICITY`, `IDENTITY_ATTACK`, `INSULT`, `PROFANITY`, `THREAT`. As of 2025–2026, Google has **sunsetted** the public API — service ends after 2026 with no migration support. Listed here for completeness because many older pipelines still reference it; new deployments should not depend on it. The de facto replacement for community/forum moderation is now the Perspective-derived models inside Google Jigsaw's `cjadams/conversational-safety` HuggingFace models or vendor-specific offerings.

**ShieldGemma.** Google DeepMind's open safety classifier family at 2B / 9B / 27B parameters, built on Gemma 2. Trained as a downstream filter on Gemma 2 outputs across four harm categories (dangerous content, harassment, hate speech, sexually explicit). Designed for on-device or self-hosted deployment; input is text, output is per-category probability. Useful for organizations that want to host their own classifier without sending content to a third-party moderation API. Notable for being openly licensed and quantized for edge use; weakest of the three model sizes for nuanced multi-turn context, strongest for high-throughput inference.

**Llama Guard 3 (Meta, via the PurpleLlama project).** An 8B LLM-based input-output safeguard model, fine-tuned to classify against an 11-category safety taxonomy aligned with the MLCommons AI Safety Benchmark v0.5: Violence and Hate, Sexual Content, Criminal Planning, Guns and Illegal Weapons, Regulated or Controlled Substances, Self-Harm, and Cyber Threats. Accepts both user prompts (as input) and model responses (as output) and returns a structured verdict ("safe" / "unsafe" plus category codes). Key design choice: it is itself an LLM, so it can be instructed to follow domain-specific policies via a system prompt. Outperforms many off-the-shelf classifiers on adversarial inputs because the LLM-base generalizes to novel phrasings.

**Azure AI Content Safety.** A managed, multi-API suite rather than a single model. Capabilities relevant to LLM defense:
- *Prompt Shields* — detects both direct user-prompt jailbreak attempts and indirect attacks hidden in retrieved documents (the "document attack" mode). Distinguishes "user prompt attack" from "document attack" with separate response fields; threshold-tunable.
- *Groundedness detection* — flags LLM completions that diverge from user-supplied source material (anti-hallucination). Uses an internal NLI-style model.
- *Protected material text* — scans outputs for known text content (lyrics, articles, recipes, selected web content) to prevent regurgitation.
- *Protected material code* — same but for code (detects memorized public code).
- *Task adherence* — flags agent tool calls that are misaligned with the user's intent (premature/unintended actions). Critical for the LLM08 Excessive Agency defense.
- *Analyze text/image* — multi-severity classifiers (0–7) for the four canonical harm categories (sexual, violence, hate, self-harm) with separate harm-type routing.
- *Custom categories (standard)* — train your own custom category from labeled examples; useful for org-specific policy.
- *Custom categories (rapid)* — define a free-form description of the target pattern; no training data needed.

Auth via Microsoft Entra ID or managed identity; supports customer-managed keys (BYOK). Multi-region availability; English-only for some features (protected material, groundedness, custom categories). Integrate via the Content Safety Studio for tuning, or programmatically for production. Pre-built integration with Azure OpenAI Service and Azure AI Foundry for binding a content-filter policy per model deployment.

**AWS Bedrock Guardrails.** Cross-model guardrails applicable to all foundation models on Bedrock (Claude, Llama, Mistral, AI21, Cohere, Amazon Titan) and to Bedrock Agents, Knowledge Bases, and Flows. Six safeguard policies, all independently configurable:
- *Content filters* — block harmful content across hate, insults, sexual, violence, misconduct, prompt-attack categories.
- *Denied topics* — define topics (e.g., "medical advice", "competitor products") that the model must not discuss; uses a topic-detection model under the hood.
- *PII detection* — anonymize or block 30+ PII types (SSN, credit card, email, phone, address, etc.).
- *Contextual grounding* — verify LLM responses are grounded in retrieved sources and relevant to the user query; flags hallucination.
- *Word/image filters* — custom deny-lists for profanity, competitor names, etc.
- *Automated reasoning checks* — apply logical constraints to outputs (mostly applicable to math/code-style outputs).

Two safeguard tiers (Standard, Premium/Beta) trade latency, language support, and detection quality. Most policies are evaluated in-line before the LLM response is returned to the caller, adding tens of milliseconds of latency.

#### 1.2 Programmable guardrail frameworks

**NeMo Guardrails (NVIDIA, Apache 2.0).** A runtime + policy framework rather than a single classifier. Architecture (per NVIDIA's docs):
- *Application integration layer* — your app calls NeMo Guardrails instead of the LLM directly.
- *Policy configuration* — declarative `rails.yaml` (general behavior) and Colang scripts (dialog flows) define what the model may do.
- *Runtime orchestration* — the Guardrails server intercepts every input, consults policies, and either passes, rewrites, or blocks the message; same on output.
- *External systems* — connect to actions, retrieval, or third-party APIs as first-class Colang actions.

Five canonical rail types:
- *Input rails* — filter or rewrite user input.
- *Output rails* — filter or rewrite model output.
- *Dialog rails* — steer the conversation through a defined state machine.
- *Retrieval rails* — filter retrieved documents before they reach the LLM (indirect prompt injection defense).
- *Execution rails* — intercept tool calls.

The Colang language expresses guardrails as a finite-state dialogue program, which is unusual among guardrail libraries — it suits agents that follow predictable flows but is heavyweight for free-form chat. Llama Guard 3 is the default safety model but any local or API classifier can be plugged in.

#### 1.3 Custom classifiers

When off-the-shelf classifiers don't fit the policy (e.g., internal compliance jargon, domain-specific harassment, financial advice constraints), train a custom classifier. Patterns:

- **Fine-tune a small encoder.** Take a DeBERTa-v3-base or RoBERTa-base, fine-tune on a few thousand labeled examples of in-policy vs. out-of-policy outputs; deploy on CPU with sub-10ms latency. Cost is $1–5K in labeling + compute for most domains.
- **LLM-as-classifier with structured output.** Use the application LLM (or a separate judge LLM) to score the input/output against a written policy; require JSON-schema response. Higher latency, higher cost, but no training data and trivially editable.
- **Embedding-based anomaly detection.** Embed a corpus of "known good" outputs; score new outputs by cosine distance to the centroid. Cheap and useful as a triaging signal; not robust to adversarial phrasing.
- **Few-shot pattern matchers.** Maintain a list of regexes / fuzzy-match templates for known-bad patterns (credit-card numbers, SQL fragments, competitor names). Use as a hard-blocklist; combine with a classifier for unknown patterns.

A common mistake is to use a single LLM-judge for both policy enforcement and the application task — the same model that is being tested is the one measuring its own safety. Mature deployments use a *separate* model (different provider, ideally different family) as the judge to avoid correlated failures.

#### 1.4 Layered guardrail architecture

The robust pattern is a pipeline where each stage can independently block:

```
user input
   │
   ├── input classifier #1 (e.g., Azure Prompt Shields or Llama Guard 3)
   │       block on direct jailbreak / prompt injection
   │
   ├── input classifier #2 (e.g., OpenAI Moderation)
   │       block on harassment / sexual / violence / self-harm
   │
   ├── rewriter / canonicalizer
   │       normalize unicode, strip zero-width chars, drop control sequences
   │
   ├── application-specific blocklist
   │       block on PII patterns, competitor names, denied topics
   │
   ▼
[ LLM call with system prompt + structured output schema ]
   │
   ├── output schema validator (Pydantic / Zod / JSON Schema)
   │       block on schema mismatch (the most common failure mode)
   │
   ├── output classifier (separate from LLM-as-judge when possible)
   │       block on policy violation
   │
   ├── groundedness check (only if RAG)
   │       block on unsupported claims
   │
   ├── action allowlist + scope check (if agentic)
   │       block on disallowed tool call
   │
   ▼
final response to user
```

Key design rules: (a) every block is logged with the classifier, score, and rule that fired; (b) blocks return a generic, non-leaky error to the user (don't reveal which guardrail triggered); (c) the LLM never sees the raw user input before at least one input classifier has run; (d) the LLM's output is *never* returned to the user without at least one output classifier + schema validation.

#### 1.5 Common failure modes in guardrails

- **Threshold tuning:** too low = many false positives (user friction); too high = many false negatives (bypass). Calibrate on a representative slice of production traffic; review with a labeled set every quarter.
- **Multilingual gap:** classifiers trained predominantly on English are weak on Chinese, Arabic, low-resource languages, and code-mixed text. Test in every language you serve.
- **Modality gap:** text classifiers miss jailbreaks embedded in images, audio, or PDFs. Use a multi-modal classifier (or a separate OCR step before the text classifier) for any input that may contain non-text content.
- **Adversarial suffix bypass:** research shows that GCG-style optimized suffixes can drive classifier scores low while preserving harm. The defense is layered defenses (LLM-as-judge + classifier + human review for high-risk actions), not a single classifier.
- **Classifier drift:** production traffic evolves; the classifier's false-negative rate creeps up. Run eval-set regression alarms (see §9) on a daily schedule.

#### 1.6 Choosing a stack

| Need | Recommendation |
|---|---|
| Free, no infra | OpenAI Moderation API |
| Self-hostable, multi-modal | ShieldGemma (Gemma 2 base) or Llama Guard 3 |
| Managed, broad policy | Azure AI Content Safety or AWS Bedrock Guardrails |
| Programmable dialog flows | NeMo Guardrails |
| Domain-specific policy | Fine-tuned DeBERTa or LLM-as-judge with structured output |
| Defense in depth | Combine ≥2 from different families |

## Related

- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — all defenses leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these defenses
