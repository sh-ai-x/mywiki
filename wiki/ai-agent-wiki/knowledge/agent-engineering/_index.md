---
tags: ["ai-engineering", "agent-engineering", "agent-orchestration", "mcp", "evaluation", "interview-prep", "hub"]
related:
  - ai-agent-wiki/00-index
  - ai-agent-wiki/ai-engineering-tooling/_index
  - ai-agent-wiki/core-ai-security/_index
  - ai-agent-wiki/agent-engineering/agentops-workbench/_index
created: 2026-09-09
---

# Agent Engineering

> **The skills the AI-engineering job market pays for in 2026 — agent orchestration, MCP, evaluation, observability.** This major hub is the career-positioning view of the same engineering surface that lives as raw tooling under [[../knowledge/ai-engineering-tooling/_index|ai-engineering-tooling]]. Where the tooling tree catalogs the landscape, this tree catalogs what to *know deeply enough to defend in an interview*.

The leaf notes here are interview-first: every one was written to be rehearsed out loud in front of a hiring loop. The 7 leaves under [[agentops-workbench/_index|agentops-workbench]] were distilled from the source dossier in [[/_research/agentops-workbench.md|staged research]] and grouped by the question a hiring manager actually asks:

- "How do you orchestrate an agent?" → orchestration
- "How does it talk to tools?" → MCP
- "How do you know it's working?" → evaluation
- "What happens when it crashes mid-transaction?" → reliability
- "How do you debug a production agent?" → observability
- "What do you reuse vs build?" → LangSmith
- "How do you expose it to other systems?" → API contracts

## Sub-Trees

- [[agentops-workbench/_index|agentops-workbench]] — 7-leaf canonical preparation track for the AgentOps Workbench proposal; the same 7 skills an AI-engineering interviewer will probe.

## Per-Leaf Priority Map

| Priority | Leaf | Why it matters for the 2026 market |
|---|---|---|
| 🔴 critical | [[agentops-workbench/orchestration-langgraph|Orchestration — LangGraph, HITL, Checkpointing]] | LangGraph is the de facto orchestration runtime referenced in job descriptions; HITL + checkpointing is the interview default for stateful agents |
| 🔴 critical | [[agentops-workbench/mcp-protocol|MCP — Protocol Contract and Authorization]] | MCP is the 2026 standard for tool integration; OAuth 2.1 + PKCE + resource indicators is what every agent interview tests |
| 🔴 critical | [[agentops-workbench/evaluation|Evaluation Methodology]] | "How do you know it works?" is asked in every agent-eng interview; HELM, RAGAS, MT-Bench, and LLM-as-judge are the canonical answers |
| 🟠 high | [[agentops-workbench/reliability-durable-effects|Reliability and Durable Effects]] | Production-relevant; differentiates senior candidates; "exactly-once" framing is what Gray & Reuter gave us |
| 🟠 high | [[agentops-workbench/observability-otel|Observability — OpenTelemetry for Agents]] | OTel GenAI semantic conventions are the shared attribute schema for production agents; differentiates you from candidates who only know logs |
| 🟡 medium | [[agentops-workbench/langsmith-reuse-vs-build|LangSmith — Reuse vs Build]] | Vendor-specific decision; less often asked but useful as a concrete "reuse, don't rebuild" example |
| 🟡 medium | [[agentops-workbench/api-contracts|API Contracts]] | OpenAPI / JSON-RPC are table stakes for backend roles; rarely the *focus* of an agent interview |

## Source Research

- [[_research/agentops-workbench.md|staged research dossier]] — 22 primary sources covering LangGraph, MCP 2025-06-18 authorization, HELM, RAGAS, SWE-bench, MT-Bench, DSPy, OpenTelemetry GenAI semconv, OAuth 2.1, Gray & Reuter.

## How to Use This Wiki

- **Preparing for an interview loop?** Walk the leaves in priority order: 🔴 first, then 🟠, then 🟡. Each leaf ends with a `## Sources` block you can cite from memory.
- **Defending a design decision?** The leaf's `## Related` block links to the canonical references — useful when the interviewer asks "what's the source for that?"
- **Connecting to security?** Cross to [[../knowledge/core-ai-security/_index|core-ai-security]] when the question shifts from "does it work?" to "is it safe?" — especially [[../knowledge/core-ai-security/essential/owasp-llm-top-10-2026|OWASP LLM Top 10 2026]] (LLM03 Excessive Agency covers the same surface as the orchestration + MCP leaves here).

## Related

- [[../00-index|AI Agent Wiki Index]] — master catalog
- [[../knowledge/ai-engineering-tooling/_index|ai-engineering-tooling]] — landscape view (sibling sub-tree)
- [[../knowledge/core-ai-security/_index|core-ai-security]] — security / governance for the same stack (sibling sub-tree)
- [[../knowledge/strix/_index|Strix]] — operational backbone that exercises the whole wiki
- [[agentops-workbench/_index|agentops-workbench sub-hub]] — the 7-leaf preparation track
