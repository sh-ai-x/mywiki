---
tags: ["ai-engineering", "ai-agent", "langchain", "langgraph", "tooling", "interview-prep"]
priority: critical
related: ["ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/_index", "ai-agent-wiki/ai-engineering-tooling/_index", "ai-agent-wiki/00-index"]
created: 2026-09-09
updated: 2026-09-09
source: "_research/ai-llm-vlm-tooling.md"
job-hunting: true
---

# The 2026 agent-framework landscape is consolidating around three roles

> The confusing "LangChain vs LangGraph" debate of 2024–2025 has resolved into a clearer three-role split:

The confusing "LangChain vs LangGraph" debate of 2024–2025 has resolved into a clearer three-role split:

| Role | Tool | What it is |
|---|---|---|
| LLM-app framework | **LangChain** | Core abstractions, integrations, chain-of-LLM-call primitives |
| Stateful agent runtime | **LangGraph** | Graph-of-agents with persistent state, cycles, human-in-loop, checkpoints |
| Observability | **LangSmith** | Tracing, evaluation, prompt-management — works with LangChain, LangGraph, or anything else |

This separation has consequences for tooling choice: LangChain alone is for simple chains; LangGraph is what you reach for when the agent needs to loop, remember, or be interrupted; LangSmith is non-optional at production scale regardless of which framework you build on. LangGraph is now the most-installed agent framework in 2026, ahead of OpenAI Agents SDK, CrewAI, and AutoGen.

Alternative frameworks in the same space:
- **OpenAI Agents SDK** — minimal, leans on OpenAI primitives
- **CrewAI** — role-based multi-agent pattern
- **AutoGen** (Microsoft) — conversational multi-agent
- **Microsoft Agent Framework** — enterprise-leaning, replaces Semantic Kernel + AutoGen story
- **PydanticAI** — Python type-safety first
- **Mastra** — TypeScript-first
- **LangFlow** — low-code visual builder on top of LangChain

## Related

- [[ai-llm-vlm-tooling/_index|ai-llm-vlm-tooling sub-hub]] — all ai-llm-vlm-tooling leaf notes
- [[knowledge/ai-engineering-tooling/_index|ai-engineering-tooling hub]] — top-level hub
- [[ai-agent-wiki/00-index|AI Agent Wiki Index]] — master catalog
