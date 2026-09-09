---
tags: ["ai-security", "nist-rmf", "iso-42001", "eu-ai-act"]
priority: low
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/00-index"]
created: 2026-09-07
source: "_research/core-ai-security-frameworks.md"
---

# Vendor SDKs and APIs

> **Moderation API.** `omni-moderation-latest` — free endpoint; multi-modal text + image classification; categories: hate, harassment, self-harm, sexual, violence. Used as the foundational input/output filter in most OpenAI-based applications

#### 8.1 OpenAI

**Moderation API.** `omni-moderation-latest` — free endpoint; multi-modal text + image classification; categories: hate, harassment, self-harm, sexual, violence. Used as the foundational input/output filter in most OpenAI-based applications.

**OpenAI Safety best practices.** Public guidance recommending layered guardrails (moderation + system prompt + output validation), structured outputs to constrain tool calls, jailbreak-resistance via evals, and human-in-the-loop for high-stakes actions.

**OpenAI model cards.** Each released model has a system card describing the safety evaluations, the categories tested, the failure modes found, and the mitigations applied. Increasingly required reading for procurement.

**Function calling / structured outputs.** JSON Schema-constrained output that the SDK refuses to emit if the model output doesn't match. The most reliable defense against LLM02 Insecure Output Handling.

#### 8.2 Anthropic

**Constitutional AI.** Training-time harmlessness via self-critique against a written constitution (see defenses file §7.2).

**Responsible Scaling Policy (RSP).** Anthropic's commitment to only train or deploy models above certain capability thresholds after independent evaluation and demonstrated safety. RSP has graduated levels (ASL-2, ASL-3, ASL-4); each level has specific safety requirements.

**System cards.** Each major Claude release has a published system card describing evaluations, refusals, red-team findings, and the claimed RSP level.

**Tool use.** Claude's tool-use framework accepts a JSON Schema description of each tool; the SDK enforces the schema.

**Prompt caching.** Allows reuse of large system prompts across many requests, reducing cost and latency.

#### 8.3 Google

**ShieldGemma.** Open safety classifier family (2B/9B/27B) built on Gemma 2; downstream filter for dangerous content, harassment, hate speech, sexually explicit.

**Gemini API safety features.** Built-in safety filters across harm categories with adjustable thresholds; configurable blocklists; structured output; function calling.

**Google AI Studio / Vertex AI.** Managed environments with built-in safety tuning, content filtering, and evaluation tooling.

**Model cards.** Each Gemini release has a published model card with safety evaluations.

#### 8.4 Microsoft Azure

**Azure AI Content Safety.** The canonical Microsoft guardrail suite (detailed in the defenses file). Includes Prompt Shields (jailbreak / injection detection), Groundedness detection, Protected material, Task adherence, and harm-category classifiers.

**Azure AI Foundry / Azure OpenAI Service.** Pre-built integration with Content Safety; per-model-deployment content-filter policies; Defender for AI services for runtime threat detection.

**Copilot Studio / M365 Copilot.** Enterprise-grade AI assistant products with built-in content safety, audit logging, and admin controls.

**Model catalog.** Azure AI Foundry hosts models from OpenAI, Anthropic, Meta, Mistral, AI21, Cohere, and others — all with Content Safety integration.

#### 8.5 AWS Bedrock Guardrails

**Bedrock Guardrails.** Cross-model guardrails applicable to all foundation models on Bedrock (Claude, Llama, Mistral, AI21, Cohere, Amazon Titan). Six safeguard policies: content filters, denied topics, PII detection, contextual grounding, word/image filters, automated reasoning. Applies to model inference, agents, knowledge bases, and flows. Two tiers (Standard, Premium/Beta) trade latency, language support, and quality.

**Bedrock Agents.** Managed agent framework with built-in guardrail integration, KB retrieval, and code interpretation.

**Bedrock Knowledge Bases.** Managed RAG with built-in guardrails; can apply the same Guardrail policy to both retrieval and inference.

#### 8.6 Comparison

| Vendor | Strength | Weakness |
|---|---|---|
| OpenAI | Best developer ergonomics; mature moderation API | Closed model, closed safety training details |
| Anthropic | Strongest published safety commitments (RSP); Constitutional AI | Smaller model catalog |
| Google | Open model options (ShieldGemma, Gemma); strong research | Safety features less unified across surfaces |
| Microsoft Azure | Most comprehensive managed offering; Defender integration | Heavy Azure ecosystem dependency |
| AWS Bedrock | Cross-model guardrails; tight agent/KB integration | Less mature than Azure |

The right vendor depends on existing cloud commitments, regulatory requirements, and the specific safety features needed. Multi-vendor deployments (e.g., Claude for the application, OpenAI for moderation) are increasingly common as a defense-in-depth measure.

## Related

- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — all frameworks leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these frameworks
