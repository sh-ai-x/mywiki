---
tags: ["ai-engineering", "ai-engineering-tooling", "hub", "job-hunting"]
priority: high
related: ["ai-agent-wiki/00-index", "ai-agent-wiki/core-ai-security/_index"]
created: 2026-09-09
updated: 2026-09-09
job-hunting: true
---

# AI Engineering Tooling (job-hunting-filtered)

> Major-hub for the **ai-engineering-tooling** sub-tree. **Filtered for job-hunting relevance** — only the tools, patterns, and conceptual references that an AI / LLM engineering interview (or a hiring-loop whiteboard) actually pays for. Sibling of [[../knowledge/core-ai-security/_index|core-ai-security]].

## Job-hunting framing

The job market for AI / LLM engineers in Q3 2026 pays for working knowledge of:

1. **Agent frameworks** — LangChain vs LangGraph vs OpenAI Agents SDK vs CrewAI (the consolidated three-role split).
2. **RAG** — naive / GraphRAG / agentic / reranking; when to use which.
3. **The layered stack** — foundation model, agent runtime, observability, retrieval, vector DB, memory, guardrails.
4. **VLMs** — closed-source leaders, open-source bolt-on pattern, multi-model routing.
5. **Foundational concepts** — ReAct / RAG / LLaVA / Constitutional AI; Anthropic + OpenAI engineering blogs.
6. **Decision shortcuts** — which stack for which use-case, in one sentence each.

PKM, PKM philosophy, and meta-content have been archived.

## Sub-Domains (priority-ordered)

### 🟥 Critical — read first

- [[ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/the-2026-agent-framework-landscape-is-consolidating-around-t|Agent frameworks (LangChain / LangGraph / LangSmith)]]
- [[ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/rag-retrieval-augmented-generation-the-rag-in-the-topic|RAG]]
- [[ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/decision-shortcuts|Decision shortcuts]]

### 🟧 High

- [[ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/how-these-fit-together-the-ai-engineering-stack|How these fit together — the AI-engineering stack]]
- [[ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/concept-deep-dive-papers-blogs|Concept deep-dive — papers & blogs]] *(ReAct / RAG / LLaVA / Constitutional AI + Anthropic / OpenAI posts)*

### 🟨 Medium

- [[ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/graphrag-specifically-when-it-pays|GraphRAG — when it pays]]
- [[ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/vision-language-models-vlm-the-vlm-in-the-topic|VLM]]

### Sub-hub entry point

- [[ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/_index|ai-llm-vlm-tooling sub-hub]] — full leaf index for the above 7.

## What this hub is NOT

- **Not** a vendor-comparison shootout (those exist elsewhere; see Sources).
- **Not** a beginner's introduction to LLMs (assumes basic ML literacy).
- **Not** an LLM-Wiki PKM primer — the LLM-Wiki pattern is the *implementation substrate* for [[../_index|this entire vault]], but the curated PKM / philosophy leaves were archived for the job-hunting filter. The references are preserved in [[ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/_index|_archive/]].

## Source Research

- [[_research/ai-llm-vlm-tooling.md|staged research dossier]] — source of record for §11 (concept deep-dive), §10 (concept deep-dive appended 2026-09-09).

## Related

- [[../00-index|AI Agent Wiki Index]] — master catalog
- [[../knowledge/core-ai-security/_index|Core AI Security]] — security / governance for the same stack
- [[../knowledge/agent-engineering/_index|Agent Engineering]] *(new, see pane B)* — adjacent subtree in active curation
