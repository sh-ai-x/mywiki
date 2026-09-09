---
tags: ["ai-engineering", "ai-agent", "rag", "langchain", "langgraph", "graphrag", "interview-prep"]
priority: high
related: ["ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/_index", "ai-agent-wiki/ai-engineering-tooling/_index", "ai-agent-wiki/00-index"]
created: 2026-09-09
updated: 2026-09-09
source: "_research/ai-llm-vlm-tooling.md"
job-hunting: true
---

# How these fit together — the AI-engineering stack

> For a 2026 AI product team, the realistic stack is:

For a 2026 AI product team, the realistic stack is:

| Layer | Choice(s) | Notes |
|---|---|---|
| **Foundation model** | GPT-4o / Gemini 2.0 / Claude 3.5 (or open-source equivalent for self-hosted) | Pick by primary content type + cost |
| **Agent runtime** | LangGraph (most common), or OpenAI Agents SDK / CrewAI / Microsoft Agent Framework | LangGraph for stateful; CrewAI for role-based; MAF for enterprise |
| **Agent observability** | LangSmith (LangChain ecosystem), or Helicone / Langfuse (vendor-neutral), or Arize Phoenix (eval-focused) | Non-optional at production |
| **Retrieval / RAG** | LlamaIndex (RAG-first), LangChain (general), Haystack (enterprise) + GraphRAG for multi-hop | Add GraphRAG only when queries are global |
| **Vector DB** | Pinecone (managed), Weaviate / Qdrant (self-hosted), pgvector (existing Postgres), Chroma (dev) | Don't pick on benchmark alone — pick on operational story |
| **Memory / persistence** | LangGraph checkpointer (built-in), Redis (production), Postgres | Most agent state is just key-value |
| **Knowledge layer** | Obsidian vault + LLM-Wiki pattern (this very vault) | Every agent decision, eval, prompt iter goes in as a leaf note |
| **Guardrails** | (separately, see [[ai-agent-wiki/core-ai-security/_index|core-ai-security]]) | Layered — input filter + action allowlist + sandbox + audit log |

## Related

- [[ai-llm-vlm-tooling/_index|ai-llm-vlm-tooling sub-hub]] — all ai-llm-vlm-tooling leaf notes
- [[knowledge/ai-engineering-tooling/_index|ai-engineering-tooling hub]] — top-level hub
- [[ai-agent-wiki/00-index|AI Agent Wiki Index]] — master catalog
