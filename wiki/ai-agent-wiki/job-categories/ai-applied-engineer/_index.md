---
tags: ["ai-applied-engineer", "job-category", "facet", "applied-llm", "production"]
related: ["ai-agent-wiki/job-categories/_index", "ai-agent-wiki/knowledge/agent-engineering/_index", "ai-agent-wiki/knowledge/ai-engineering-tooling/_index", "ai-agent-wiki/career-coaching"]
created: 2026-09-10
priority: medium
job-hunting: true
---

# AI Applied Engineer (facet)

> **You're an AI Applied Engineer if**: you ship LLM-powered products to end users. Less about foundation-model research, more about prompt engineering, tool-use design, RAG pipelines, and production guardrails. You might be at a SaaS company, an internal-tools team, or a startup.

This is the **product-focused** cousin of [[../ai-engineer/_index|AI Engineer]]. The two overlap heavily; AI Applied Engineer just biases toward "ship the LLM feature" rather than "build the agent infrastructure."

## What to read (priority-ordered)

### 🔴 Critical — must know

- [[knowledge/ai-engineering-tooling/ai-llm-vlm-tooling/rag-retrieval-augmented-generation-the-rag-in-the-topic|RAG]] — every production LLM app needs retrieval
- [[knowledge/core-ai-security/essential/owasp-llm-top-10-2026|OWASP LLM Top 10 — 2026 Edition]] — the threat model for LLM apps
- [[knowledge/core-ai-security/essential/prompt-injection|Prompt Injection — Deep Dive]] — LLM01
- [[knowledge/core-ai-security/essential/guardrails|Guardrails]] — input/output filters are table stakes
- [[knowledge/core-ai-security/practical/defense-in-depth-architecture|Defense-in-Depth Architecture]] — the L7 layer pattern
- [[knowledge/ai-engineering-tooling/ai-llm-vlm-tooling/the-2026-agent-framework-landscape-is-consolidating-around-t|Agent Frameworks]] — pick LangChain / LangGraph / OpenAI Agents SDK appropriately

### 🟠 High — should know

- [[knowledge/agent-engineering/agentops-workbench/orchestration-langgraph|Orchestration — LangGraph, HITL, Checkpointing]] — for multi-step agents
- [[knowledge/core-ai-security/practical/system-prompt-hardening|System Prompt Hardening]]
- [[knowledge/core-ai-security/practical/retrieval-filtering|Retrieval Filtering (vs Indirect Prompt Injection)]]
- [[knowledge/core-ai-security/essential/jailbreaks|Jailbreaks]] — know how they fail
- [[knowledge/agent-engineering/agentops-workbench/evaluation|Evaluation Methodology]] — every production change needs an eval

### 🟡 Medium — production-relevant

- [[knowledge/ai-engineering-tooling/ai-llm-vlm-tooling/decision-shortcuts|Decision Shortcuts]]
- [[knowledge/ai-engineering-tooling/ai-llm-vlm-tooling/how-these-fit-together-the-ai-engineering-stack|How these fit together — the AI-engineering stack]]
- [[knowledge/agent-engineering/agentops-workbench/mcp-protocol|MCP — Protocol + Authorization]]
- [[knowledge/core-ai-security/practical/sandboxing|Sandboxing]] — for code-executing agents

## Career resources

- [[career-coaching]] — junior-level AI engineer track

## Related

- [[../_index|Job Categories hub]]
- [[../ai-engineer/_index|AI Engineer]] (broader, infra-focused cousin)
- [[../ai-native-developer/_index|AI-Native Developer]] (more generalist cousin)
- [[../../knowledge/agent-engineering/_index|Agent Engineering]]
- [[../../knowledge/ai-engineering-tooling/_index|AI Engineering Tooling]]
