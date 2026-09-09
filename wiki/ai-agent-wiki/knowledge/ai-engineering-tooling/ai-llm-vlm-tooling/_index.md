---
tags: ["ai-engineering", "ai-llm-vlm-tooling", "tooling", "sub-hub", "job-hunting"]
priority: high
related: ["ai-agent-wiki/ai-engineering-tooling/_index", "ai-agent-wiki/00-index"]
created: 2026-09-09
updated: 2026-09-09
source: "_research/ai-llm-vlm-tooling.md"
job-hunting: true
---

# Ai Llm Vlm Tooling — Sub-Hub (job-hunting-filtered)

> Sub-hub of [[../_index|ai-engineering-tooling]], **curated for job-hunting**: only the leaves that map to topics an AI / LLM engineering interview actually asks about. PKM / meta leaves archived to `_archive/`. 6 surviving leaves + 1 promoted concept-deep-dive = 7 total.

## Leaf Notes (priority-ordered)

### Critical (read these first)

- 🟥 [[the-2026-agent-framework-landscape-is-consolidating-around-t|The 2026 agent-framework landscape is consolidating around three roles]] — LangChain vs LangGraph vs LangSmith, OpenAI Agents SDK, CrewAI, AutoGen, Microsoft Agent Framework. **Asked in nearly every LLM-eng interview.**
- 🟥 [[rag-retrieval-augmented-generation-the-rag-in-the-topic|RAG (Retrieval-Augmented Generation)]] — naive RAG, GraphRAG, agentic RAG, reranking; framework landscape. **Asked in every LLM-eng interview.**
- 🟥 [[decision-shortcuts|Decision shortcuts]] — cheat-sheet: which stack for which use-case. **Interview gold.**

### High

- 🟧 [[how-these-fit-together-the-ai-engineering-stack|How these fit together — the AI-engineering stack]] — the layered stack (foundation model, agent runtime, observability, RAG, vector DB, memory, knowledge, guardrails).
- 🟧 [[concept-deep-dive-papers-blogs|Concept deep-dive — papers, blog posts, primary sources]] *(promoted from `_research/` §11)* — ReAct, RAG, LLaVA, Constitutional AI papers; Anthropic / OpenAI foundational blog posts. **Read this end-to-end on day one of interview prep.**

### Medium

- 🟨 [[graphrag-specifically-when-it-pays|GraphRAG specifically — when it pays]] — interview answer is usually "don't bother unless multi-hop / >10k docs."
- 🟨 [[vision-language-models-vlm-the-vlm-in-the-topic|Vision Language Models (VLM)]] — benchmark table + decision rule (routing, not pick-one).

## Surviving leaf count: 7 (was 10; 4 archived, 1 promoted)

## Archived to `_archive/` (kept for reference, not interview-prep)

- `_archive/ai-llm-vlm-tooling-llm-wiki.md` — PKM-flavored, not interview-relevant.
- `_archive/whats-not-covered-in-this-dossier.md` — meta-content, not interview-relevant.
- `_archive/related-reading.md` — already duplicated in every leaf.
- `_archive/llm-wiki-pattern-deep-dive-appended-2026-09-09.md` — PKM philosophy; primary reading list is now folded into [[concept-deep-dive-papers-blogs]] §11.5.

## Source

Full research dossier: [[_research/ai-llm-vlm-tooling.md]]

## Sources

- https://www.langchain.com/resources/ai-agent-frameworks
- https://www.truefoundry.com/blog/langchain-vs-langgraph-vs-langsmith
- https://www.uvik.net/blog/langchain-vs-langgraph/
- https://www.speakeasy.com/blog/ai-agent-framework-comparison/
- https://www.reddit.com/r/AgentsOfAI/comments/1n9rdoy/finally_understand_langchain_vs_langgraph_vs/
- https://xenoss.io/blog/langchain-langgraph-llamaindex-llm-frameworks
- https://galileo.ai/blog/langchain-vs-langgraph-vs-langsmith
- https://www.datacamp.com/tutorial/langchain-vs-langgraph-vs-langsmith-vs-langflow
- https://www.f22labs.com/blog/gpt-4v-vs-gemini-vision-benchmark-comparison/
- https://research.aimultiple.com/gpt-vs-gemini/
- https://hexaware.com/blogs/gemini-vs-gpt-vs-llama-vs-claude-comparison/
- https://www.upshot.ai/blogs/gemini-vs-gpt-4-comparison-2026/
- https://arxiv.org/abs/2210.03629 (ReAct)
- https://arxiv.org/abs/2005.11401 (RAG original)
- https://arxiv.org/abs/2404.16130 (GraphRAG)
- https://arxiv.org/abs/2304.08485 (LLaVA)
- https://arxiv.org/abs/2212.08073 (Constitutional AI)
- https://arxiv.org/abs/2309.00267 (RLAIF)
- https://www.anthropic.com/engineering/building-effective-agents
- https://openai.com/index/functions-and-their-llms-thoughts/

## Related

- [[knowledge/ai-engineering-tooling/_index|ai-engineering-tooling hub]] — parent major-hub
- [[ai-agent-wiki/00-index|AI Agent Wiki Index]] — master catalog
