---
tags: ["ai-engineering", "rag", "langchain", "langgraph", "graphrag", "interview-prep"]
priority: critical
related: ["ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/_index", "ai-agent-wiki/ai-engineering-tooling/_index", "ai-agent-wiki/00-index"]
created: 2026-09-09
updated: 2026-09-09
source: "_research/ai-llm-vlm-tooling.md"
job-hunting: true
---

# RAG (Retrieval-Augmented Generation) — the "RAG" in the topic

> RAG grounds LLM outputs in retrieved chunks from a vector or hybrid index, reducing hallucination and giving access to fresh/proprietary data without fine-tuning. As of 2026, the dominant patterns:

RAG grounds LLM outputs in retrieved chunks from a vector or hybrid index, reducing hallucination and giving access to fresh/proprietary data without fine-tuning. As of 2026, the dominant patterns:

- **Naive RAG**: embed chunks, top-k cosine-similarity, stuff into prompt. Cheap, brittle on multi-hop questions.
- **GraphRAG** (Microsoft, 2024) — build a knowledge graph over the corpus, use community-detection / entity-linking for retrieval. Better on multi-hop and "synthesize across documents" queries. Compute-heavy (entity-extraction pass + graph build), but much better on long-corpus summarization tasks.
- **Agentic RAG** — let an agent decide which retrievers / tools to call. Hybrid: when the answer is obvious, single retrieval; when complex, multi-step plan with multiple retrieval + reasoning rounds.
- **Reranking** — first-pass retrieval (high recall, low precision) → rerank (low recall, high precision). Cohere Rerank, BGE-reranker, LLM-based rerankers.

**Framework landscape for RAG**: LangChain / LangGraph cover the agentic-RAG patterns; LlamaIndex is RAG-first with strong ingestion/indexing; Haystack (deepset) is enterprise-leaning with strong evaluation; Pinecone / Weaviate / Qdrant / Chroma are the vector-DB tier.

## Related

- [[ai-llm-vlm-tooling/_index|ai-llm-vlm-tooling sub-hub]] — all ai-llm-vlm-tooling leaf notes
- [[knowledge/ai-engineering-tooling/_index|ai-engineering-tooling hub]] — top-level hub
- [[ai-agent-wiki/00-index|AI Agent Wiki Index]] — master catalog
