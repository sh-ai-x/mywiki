---
tags: ["ai-engineering", "rag", "graphrag"]
priority: medium
related: ["ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/_index", "ai-agent-wiki/ai-engineering-tooling/_index", "ai-agent-wiki/00-index"]
created: 2026-09-09
updated: 2026-09-09
source: "_research/ai-llm-vlm-tooling.md"
job-hunting: true
---

# GraphRAG specifically — when it pays

> Microsoft's GraphRAG (open-sourced mid-2024) is the right tool when:

Microsoft's GraphRAG (open-sourced mid-2024) is the right tool when:
- The corpus is large (>10k docs)
- Queries are global / multi-hop ("summarize the themes", "what does the corpus say about X")
- The user wants citations grounded in entity relationships

It's the wrong tool when:
- Queries are simple lookup ("what does section 3 say")
- Latency budget is tight (GraphRAG retrieval is 2-10x slower than vector RAG)
- The corpus is small enough that entity extraction cost doesn't pay back

## Related

- [[ai-llm-vlm-tooling/_index|ai-llm-vlm-tooling sub-hub]] — all ai-llm-vlm-tooling leaf notes
- [[knowledge/ai-engineering-tooling/_index|ai-engineering-tooling hub]] — top-level hub
- [[ai-agent-wiki/00-index|AI Agent Wiki Index]] — master catalog
