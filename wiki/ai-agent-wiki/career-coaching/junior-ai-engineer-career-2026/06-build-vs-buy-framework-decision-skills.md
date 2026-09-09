---
topic: junior-ai-engineer-career-2026/06
tags: ["career", "job-hunting", "junior", "ai-engineer", "build-vs-buy", "framework-decision", "interview-prep", "global-first"]
related: ["ai-agent-wiki/career-coaching/junior-ai-engineer-career-2026/03-required-agent-llm-stack-knowledge"]
source: "_research/junior-ai-engineer-career-2026.md#6"
created: 2026-09-10
priority: medium
job-hunting: true
global-first-filter: applied
---

# 6. Build-vs-buy / framework decision skills

This section is the *trade-offs* test — the interviewer asks "we need X, do we use a tool or build it?"

### 6.1 LangGraph vs. in-house

**Use LangGraph when**: stateful agents, cycles, human-in-loop, persistent checkpointer. Most production agent work fits this. (Source: https://www.anthropic.com/engineering/building-effective-agents — Anthropic notes that "a 200-line script using the SDK often beats a framework-heavy implementation," but that advice is for *workflows*, not *agents*.)

**Build in-house when**: the requirement is so specific that LangGraph's abstractions get in the way; when latency budgeting at the LLM-call level is critical and the framework overhead is measurable; when the team has strong opinions on persistence / event-sourcing that conflict with LangGraph's checkpointing model.

### 6.2 Managed RAG vs. custom

**Use managed (Vertex AI RAG Engine, Bedrock Knowledge Bases, Pinecone + LangChain retrieval, AWS Kendra, Azure AI Search)** when: time-to-market matters, the team doesn't have vector-search expertise, scale is moderate (<10M vectors).

**Custom (your own chunking / embedding / retrieval / rerank pipeline)** when: you have a data-engineering team, you need fine-grained control over retrieval quality (often: 10–30% absolute recall gains matter), or you're doing high-stakes retrieval where the off-the-shelf recall is unacceptable.

The default 2026 answer: managed RAG first; optimize once the bottleneck is identified.

### 6.3 Fine-tuning vs. prompting vs. RAG

The 2026 framework (per Anthropic and OpenAI guidance, both echoed across multiple sources accessed 2026-09-10):

| If your problem is… | Use |
|---|---|
| General task, want rapid iteration | **Prompting** |
| Need access to fresh / proprietary knowledge | **RAG** |
| Need consistent output format / style / brand voice | **Fine-tuning** |
| Need a specialized reasoning pattern at low cost | **Fine-tune a small model on outputs from a large model** (distillation) |
| Need a model that runs offline / on-device / in a regulated env | **Fine-tune an OSS base** |

**Anti-patterns**: fine-tuning to "teach" knowledge (use RAG); RAG for behavior (fine-tune); fine-tuning when you haven't first tried prompting.
