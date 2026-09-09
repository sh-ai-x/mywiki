---
tags: ["ai-engineering", "rag", "langchain", "langgraph", "graphrag", "vlm", "interview-prep"]
priority: critical
related: ["ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/_index", "ai-agent-wiki/ai-engineering-tooling/_index", "ai-agent-wiki/00-index"]
created: 2026-09-09
updated: 2026-09-09
source: "_research/ai-llm-vlm-tooling.md"
job-hunting: true
---

# Decision shortcuts

> Decision shortcuts

- **Just prototyping**: LangChain + LangSmith free tier + Chroma. Skip GraphRAG.
- **Stateful production agent**: LangGraph + LangSmith + PostgreSQL checkpointer + a vector DB.
- **Document-heavy enterprise app**: VLM (Gemini 2.0 Pro for accuracy / Flash for cost) + LlamaIndex + pgvector.
- **Multi-hop Q&A over a knowledge base**: GraphRAG + LangChain orchestration.
- **Personal / team knowledge**: Obsidian vault + obsidian-organize plugin. The LLM-Wiki pattern scales to ~1000 notes before needing a different substrate.

## Related

- [[ai-llm-vlm-tooling/_index|ai-llm-vlm-tooling sub-hub]] — all ai-llm-vlm-tooling leaf notes
- [[knowledge/ai-engineering-tooling/_index|ai-engineering-tooling hub]] — top-level hub
- [[ai-agent-wiki/00-index|AI Agent Wiki Index]] — master catalog
