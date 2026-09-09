---
tags: ["dev-tools-engineer", "job-category", "facet", "plugin-architecture", "claude-code", "mcp", "devx"]
related: ["ai-agent-wiki/job-categories/_index", "ai-agent-wiki/career-coaching", "ai-agent-wiki/job-hunting-priority"]
created: 2026-09-10
priority: medium
job-hunting: true
---

# Dev-Tools Engineer (facet)

> **You're a Dev-Tools Engineer if**: you build the infrastructure that other developers use. Plugin marketplaces, MCP servers, eval harnesses, CI tooling, agent orchestration layers. The dev-harness-kit repo (https://github.com/sh-ai-x/dev-harness-kit) is exactly this kind of work.

This is the most differentiated of the tracks — fewer jobs advertised under this exact title, but the skills transfer directly to:
- AI infrastructure teams (Anthropic, OpenAI, Cursor)
- DevX / Internal Tools teams at FAANG
- Open-source maintainer roles
- Plugin ecosystem builders (Stripe, Twilio, Vercel ecosystem teams)

## What to read (priority-ordered)

### 🔴 Critical — must know

- [[knowledge/agent-engineering/agentops-workbench/orchestration-langgraph|Orchestration — LangGraph, HITL, Checkpointing]] — how production agents actually run
- [[knowledge/agent-engineering/agentops-workbench/mcp-protocol|MCP — Protocol + Authorization]] — the model-context-protocol is the new plugin standard
- [[knowledge/agent-engineering/agentops-workbench/evaluation|Evaluation Methodology]] — how to measure whether your tooling actually helps

### 🟠 High — should know

- [[knowledge/agent-engineering/agentops-workbench/observability-otel|Observability — OpenTelemetry for Agents]]
- [[knowledge/agent-engineering/agentops-workbench/reliability-durable-effects|Reliability and Durable Effects]] — durable execution patterns
- [[knowledge/agent-engineering/agentops-workbench/langsmith-reuse-vs-build|LangSmith — Reuse vs Build]]
- [[knowledge/agent-engineering/agentops-workbench/api-contracts|API Contracts]]

### 🟡 Medium — production-relevant

- [[knowledge/agent-engineering/agentops-workbench/orchestration-langgraph|Orchestration patterns — state, persistence, retries]]
- [[knowledge/ai-engineering-tooling/ai-llm-vlm-tooling/the-2026-agent-framework-landscape-is-consolidating-around-t|Agent Frameworks — the 2026 landscape]]

## Portfolio positioning (the dev-harness-kit angle)

The dev-harness-kit (https://github.com/sh-ai-x/dev-harness-kit) is a **production-grade plugin marketplace** for Claude Code / Codex. It demonstrates:

| Artifact | Job-market signal |
|---|---|
| Plugin marketplace structure (`plugins/`) | "Built a software marketplace with skill versioning" |
| Skill authoring (`skills/add_wiki/SKILL.md`, etc.) | "Authored 5+ LLM-callable tools" |
| Plugin marketplace listings | "Built a developer-distribution channel" |
| TDD gates + worktree-guard | "Built CI enforcement of TDD discipline" |
| Multi-pane parallel research workflow | "Built an agent-orchestration tool for parallel work" |

Translating dev-harness-kit into a hiring signal — see [[career-coaching]] for the full narrative.

## Career resources

- [[career-coaching]] — the dev-harness-kit portfolio is the centerpiece of the AI-native career narrative

## Related

- [[../_index|Job Categories hub]]
- [[../ai-native-developer/_index|AI-Native Developer]] (overlapping)
- [[../../knowledge/agent-engineering/_index|Agent Engineering]]
