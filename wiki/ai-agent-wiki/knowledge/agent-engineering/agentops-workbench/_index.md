---
tags: ["agent-engineering", "agentops", "agentops-workbench", "interview-prep", "sub-hub"]
related:
  - ai-agent-wiki/agent-engineering/_index
  - ai-agent-wiki/00-index
created: 2026-09-09
---

# AgentOps Workbench — Career Preparation Track

> **The 7 skills an AI-engineering interviewer probes in 2026** — distilled from the [[_research/agentops-workbench.md|22-source evidence dossier]] that backs the AgentOps Workbench proposal. Each leaf is rehearsable out loud: a question, the canonical answer, and the primary source the interviewer can ask you to defend.

The sub-hub exists for one reason: every leaf below is something an AI-engineering interviewer will test in some form. Treat it as a 7-day preparation schedule.

## The 7 Leaves

| # | Leaf | Priority | What the interviewer asks |
|---|---|---|---|
| 1 | [[orchestration-langgraph\|Orchestration — LangGraph, HITL, Checkpointing]] | 🔴 critical | "Walk me through how a stateful agent pauses for human approval and resumes." |
| 2 | [[mcp-protocol\|MCP — Protocol Contract and Authorization]] | 🔴 critical | "How does your agent talk to a tool? What auth model?" |
| 3 | [[evaluation\|Evaluation Methodology]] | 🔴 critical | "How do you know the agent is working?" |
| 4 | [[reliability-durable-effects\|Reliability and Durable Effects]] | 🟠 high | "What happens when the agent crashes mid-transaction?" |
| 5 | [[observability-otel\|Observability — OpenTelemetry for Agents]] | 🟠 high | "How do you debug a production agent at 3am?" |
| 6 | [[langsmith-reuse-vs-build\|LangSmith — Reuse vs Build]] | 🟡 medium | "What would you build vs reuse for experiment tracking?" |
| 7 | [[api-contracts\|API Contracts]] | 🟡 medium | "How would you expose this agent to other systems?" |

## Reading Order

1. **Day 1–2 (critical):** orchestration → MCP → evaluation. These three show up in every loop.
2. **Day 3 (high):** reliability → observability. Differentiate yourself from candidates who only know the framework docs.
3. **Day 4 (medium):** LangSmith → API contracts. Specific, narrow, but useful as concrete examples in the system-design round.

## The Shared Pattern

Across all 7 leaves, three ideas recur — these are the through-lines worth internalizing:

1. **State machines beat prompt chains.** Every interesting agent behavior is a graph with explicit states and transitions (LangGraph `Interrupt` + `Command(resume=...)`), not a single mega-prompt. Cite the LangGraph docs when defending this.
2. **Trust boundaries are code, not prompts.** MCP's separation of host/client/server, OAuth 2.1 + PKCE, schema-validated tool calls, sandboxed execution — the security model lives in code, not in the system prompt. Cite MCP 2025-06-18 authorization spec.
3. **Measure before claiming improvement.** HELM's "taxonomy-first, multi-metric, scenario-aware" framing; RAGAS for RAG; SWE-bench for code; MT-Bench for chat; a held-out frozen set before tuning. The single most-cited paper for this through-line is HELM (Liang et al., 2022).

## Source Research

- [[_research/agentops-workbench.md|stage research dossier]] — 22 sources, 7 main sections, distilled from the AgentOps Workbench proposal.

## Related

- [[../_index|Agent Engineering major hub]] — career-positioning view across all sub-trees
- [[../../00-index|AI Agent Wiki Index]] — master catalog
