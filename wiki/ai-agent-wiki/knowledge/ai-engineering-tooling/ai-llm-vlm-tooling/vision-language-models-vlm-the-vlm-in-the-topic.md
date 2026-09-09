---
tags: ["ai-engineering", "vlm", "tooling"]
priority: medium
related: ["ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/_index", "ai-agent-wiki/ai-engineering-tooling/_index", "ai-agent-wiki/00-index"]
created: 2026-09-09
updated: 2026-09-09
source: "_research/ai-llm-vlm-tooling.md"
job-hunting: true
---

# Vision Language Models (VLM) — the "vlm" in the topic

## Benchmark snapshot (Q1 2026)

| Model | MMMU | MathVista | ChartQA | DocVQA | Best for |
|---|---|---|---|---|---|
| **Gemini 2.0/2.5** | 72.6 | 73.1 | 89.5 | 96.1 | Long visual docs, scientific/medical imaging, video agents (2M-token ctx, native multimodality) |
| **Claude 3.5 Sonnet** | 68.3 | 67.7 | 90.1 | 95.6 | Browser/desktop automation (OSWorld 61.4% vs GPT-4o 38.1%), document analysis |
| **GPT-4o** | 69.1 | 63.8 | 86.2 | 94.4 | Document extraction, screen-aware agents (mature tooling, function calling) |

## Pricing (per million tokens, Q1 2026)

| Model | Input | Output |
|---|---|---|
| Gemini 2.0 Flash | $0.075 | $0.30 |
| Gemini 2.0 Pro | $1.25 | $5.00 |
| GPT-4o | $2.50 | $10.00 |
| Claude 3.5 Sonnet | $3.00 | $15.00 |

## Decision rule (interview answer)

> **If the interview asks "which VLM?", don't pick one — pick a routing pattern.**
> Most enterprise deployments are now multi-model: cheap Gemini Flash for routing/classification, premium model only when needed. The single-model answer is almost always wrong.

## Open-source (LLaVA pattern) — when to consider

Open-source VLMs (Llama 3.2 Vision, Qwen2-VL, Molmo, Pixtral, LLaVA-1.5) sit at ~80-85% of commercial performance on core benchmarks, with the gap closing quarterly. Consider self-hosting only when:

- Data leaves-the-trust-boundary is a blocker (HIPAA, GDPR, regulated workloads).
- Inference cost at scale justifies the ops overhead (typically >100M tokens/month).
- You need fine-tuning on a domain-specific visual corpus (rare; most teams just use prompt engineering).

## Related

- [[ai-llm-vlm-tooling/_index|ai-llm-vlm-tooling sub-hub]] — all ai-llm-vlm-tooling leaf notes
- [[knowledge/ai-engineering-tooling/_index|ai-engineering-tooling hub]] — top-level hub
- [[ai-agent-wiki/00-index|AI Agent Wiki Index]] — master catalog
