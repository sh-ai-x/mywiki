---
tags: ["job-hunting", "interview-prep", "ai-engineering", "ai-security", "priority", "hub"]
related: ["ai-agent-wiki/00-index", "ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/agent-engineering/_index", "ai-agent-wiki/ai-engineering-tooling/_index", "ai-agent-wiki/strix/_index"]
created: 2026-09-09
priority: critical
job-hunting: true
---

# 🚀 Job-Hunting Priority Hub

> **Synthesized reading order for AI/ML/Security/Agent engineering interviews** — distilled from the priority tags across all four subtrees (`core-ai-security`, `agent-engineering`, `ai-engineering-tooling`, `strix`). Start at 🟥 critical, work through 🟧 high as you have time. Every leaf in this hub has the `interview-prep` tag, so Dataview queries can pick them up automatically.

## Reading order (priority-sorted across all subtrees)

### 🟥 Critical — must know for every AI/ML/Agent interview

**Core AI Security (5 critical):**
- [[knowledge/core-ai-security/essential/owasp-llm-top-10-2026|OWASP LLM Top 10 — 2026 Edition]] — the current reference taxonomy; **Excessive Agency** jumped to #3
- [[knowledge/core-ai-security/essential/prompt-injection|Prompt Injection — Deep Dive]] — LLM01 in detail
- [[knowledge/core-ai-security/essential/guardrails|Guardrails]] — input filters, output validators, content classifiers
- [[knowledge/core-ai-security/essential/action-allowlisting|Action Allowlisting / Least-Privilege for Agents]] — OWASP LLM08 mitigation
- [[knowledge/core-ai-security/practical/defense-in-depth-architecture|Defense-in-Depth Architecture]] — 7-layer pattern

**Agent Engineering (3 critical):**
- [[knowledge/agent-engineering/agentops-workbench/orchestration-langgraph|Orchestration — LangGraph, HITL, Checkpointing]] — the production-grade runtime for stateful agents
- [[knowledge/agent-engineering/agentops-workbench/mcp-protocol|MCP — Protocol + Authorization]] — 2026 emerging standard
- [[knowledge/agent-engineering/agentops-workbench/evaluation|Evaluation Methodology]] — benchmarks + judging + routing

**AI Engineering Tooling (3 critical):**
- [[knowledge/ai-engineering-tooling/ai-llm-vlm-tooling/the-2026-agent-framework-landscape-is-consolidating-around-t|Agent Frameworks — LangChain vs LangGraph vs LangSmith]] — the three-role split
- [[knowledge/ai-engineering-tooling/ai-llm-vlm-tooling/rag-retrieval-augmented-generation-the-rag-in-the-topic|RAG]] — always-asked
- [[knowledge/ai-engineering-tooling/ai-llm-vlm-tooling/decision-shortcuts|Decision Shortcuts]] — interview cheat-sheet

### 🟧 High — should know; differentiates a strong candidate

**Core AI Security (11 high):**
- [[knowledge/core-ai-security/essential/owasp-llm-top-10|OWASP LLM Top 10 — 2025 Edition (historical)]]
- [[knowledge/core-ai-security/essential/jailbreaks|Jailbreaks]]
- [[knowledge/core-ai-security/essential/red-team-methodology|Red-Teaming Methodology]]
- [[knowledge/core-ai-security/essential/nist-ai-rmf|NIST AI RMF 1.0]] — the US governance baseline
- [[knowledge/core-ai-security/practical/sandboxing|Sandboxing]]
- [[knowledge/core-ai-security/practical/system-prompt-hardening|System Prompt Hardening]]
- [[knowledge/core-ai-security/practical/retrieval-filtering|Retrieval Filtering (vs Indirect Prompt Injection)]]
- [[knowledge/core-ai-security/practical/monitoring|Monitoring]]
- [[knowledge/core-ai-security/practical/owasp-ai-security-guide|OWASP AI Security & Privacy Guide]]
- [[knowledge/core-ai-security/specialized/agent-specific-threats|Agent-Specific Threats]] — MCP / tool misuse
- [[knowledge/core-ai-security/specialized/mitre-atlas|MITRE ATLAS]]

**Agent Engineering (2 high):**
- [[knowledge/agent-engineering/agentops-workbench/reliability-durable-effects|Reliability and Durable Effects]]
- [[knowledge/agent-engineering/agentops-workbench/observability-otel|Observability — OpenTelemetry for Agents]]

**AI Engineering Tooling (3 high):**
- [[knowledge/ai-engineering-tooling/ai-llm-vlm-tooling/how-these-fit-together-the-ai-engineering-stack|How these fit together — the AI-engineering stack]]
- [[knowledge/ai-engineering-tooling/ai-llm-vlm-tooling/concept-deep-dive-papers-blogs|Concept deep-dive — papers & blogs]] *(ReAct / RAG / LLaVA / Constitutional AI + Anthropic / OpenAI posts)*

### 🟨 Medium — production-relevant; nice to know

**Core AI Security (11 medium)**, **Agent Engineering (2 medium)**, **AI Engineering Tooling (2 medium)** — Dataview `tag:#interview-prep AND priority:"medium"` returns 15 leaves.

### 🟦 Low — specialist / deep-dive; only for security / research roles

8 leaves in `core-ai-security/specialized/` (`executive-summary`, `training-time-attacks`, `adversarial-examples`, `emerging-threats-2026`, `recommended-reading`, `vendor-sdks`, `industry-overlays`, `eu-ai-act`). Not interview-prep; only relevant for security-focused roles.

## How to use this hub

- **Day 1 of interview prep**: read all 🟥 critical in order. Aim for working knowledge — be able to whiteboard each one.
- **Day 3-5**: read 🟧 high. Aim for conversational fluency.
- **Day 7 (mock interviews)**: pull each 🟥 critical leaf, give yourself 10 minutes to whiteboard it from memory, compare to the TL;DR blockquote.
- **Day 14+**: skim 🟨 medium for breadth.

## Dataview queries for active study

```dataview
LIST
FROM ""
WHERE contains(tags, "interview-prep") AND priority = "critical"
SORT file.mtime DESC
```

```dataview
TABLE priority, file.cday
FROM ""
WHERE contains(tags, "interview-prep")
SORT priority ASC
```

## What's NOT in this hub

- **PKM / evergreen-notes / LLM-Wiki pattern deep dives** — useful for vault administration, not interview prep. Archived to `_archive/` subdirectories; see [[_archive/_index|archive hub]].
- **Paper-by-paper academic deep dives** — the `concept-deep-dive-papers-blogs` leaf at 🟧 high has the conceptual scaffolding (ReAct / RAG / LLaVA / Constitutional AI) without the paper-internals that aren't interview-asked.
- **Strix operational specifics** — the Strix sub-hub covers this; only relevant for security-testing roles.

## Related

- [[00-index|AI Agent Wiki Index]] — master catalog
- [[knowledge/core-ai-security/_index|Core AI Security]] — security knowledge base (priority-tagged)
- [[knowledge/agent-engineering/_index|Agent Engineering]] — agent engineering skills (priority-tagged)
- [[knowledge/ai-engineering-tooling/_index|AI Engineering Tooling]] — tools and concepts (priority-tagged)
- [[knowledge/strix/_index|Strix sub-hub]] — operational pentest tool
