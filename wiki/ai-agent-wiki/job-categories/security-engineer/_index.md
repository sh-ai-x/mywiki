---
tags: ["security", "job-category", "facet", "security-engineer"]
related: ["ai-agent-wiki/job-categories/_index", "ai-agent-wiki/knowledge/core-ai-security/_index", "ai-agent-wiki/knowledge/strix/_index", "ai-agent-wiki/career-coaching", "ai-agent-wiki/job-hunting-priority"]
created: 2026-09-10
priority: high
job-hunting: true
---

# Security Engineer (facet)

> **You're a Security Engineer if**: your day is threat models, control reviews, incident response, compliance audits, red-team engagements, or detection engineering. You might be on a blue team, red team, GRC team, or product security.

## What to read (priority-ordered)

### 🔴 Critical — must know

**Threat models:**
- [[knowledge/core-ai-security/essential/owasp-llm-top-10-2026|OWASP LLM Top 10 — 2026 Edition]] — current reference taxonomy; **Excessive Agency jumped to #3**
- [[knowledge/core-ai-security/essential/prompt-injection|Prompt Injection — Deep Dive]] — LLM01 in detail
- [[knowledge/core-ai-security/specialized/agent-specific-threats|Agent-Specific Threats]] — MCP / tool misuse (the 2026 frontier)

**Controls:**
- [[knowledge/core-ai-security/essential/guardrails|Guardrails]] — input filters + output validators + content classifiers
- [[knowledge/core-ai-security/essential/action-allowlisting|Action Allowlisting / Least-Privilege for Agents]] — OWASP LLM08 mitigation
- [[knowledge/core-ai-security/practical/defense-in-depth-architecture|Defense-in-Depth Architecture]] — 7-layer pattern (the foundational mental model)

### 🟠 High — should know

- [[knowledge/core-ai-security/essential/red-team-methodology|Red-Teaming Methodology]] — Garak / PyRIT / promptfoo
- [[knowledge/core-ai-security/essential/jailbreaks|Jailbreaks]] — DAN family + multi-turn crescendo
- [[knowledge/core-ai-security/practical/system-prompt-hardening|System Prompt Hardening]] — structure over content
- [[knowledge/core-ai-security/practical/retrieval-filtering|Retrieval Filtering (vs Indirect Prompt Injection)]]
- [[knowledge/core-ai-security/practical/sandboxing|Sandboxing]]
- [[knowledge/core-ai-security/practical/monitoring|Monitoring]]
- [[knowledge/core-ai-security/practical/owasp-ai-security-guide|OWASP AI Security & Privacy Guide]]
- [[knowledge/core-ai-security/specialized/mitre-atlas|MITRE ATLAS]] — tactic catalog

### 🟡 Medium — production-relevant

- [[knowledge/core-ai-security/essential/nist-ai-rmf|NIST AI RMF 1.0]]
- [[knowledge/core-ai-security/practical/inference-time-defenses|Inference-Time Defenses]]
- [[knowledge/core-ai-security/practical/training-time-defenses|Training-Time Defenses]]
- [[knowledge/core-ai-security/specialized/supply-chain|Supply Chain]]
- [[knowledge/core-ai-security/specialized/incident-timeline-2023-2026|Incident Timeline 2023-2026]]

## Operational tooling

- [[knowledge/strix/_index|Strix]] — autonomous AI pentest (3 leaves: threat coverage, CI integration, defense-signal patterns)

## Career resources

- [[career-coaching]] — junior-level career coaching (see §12 for security certifications: CISSP / OSCP / CKS — Global; 정보처리기사 / 정보보안기사 — Korean-context only)

## Related

- [[../_index|Job Categories hub]]
- [[../../career-coaching|Career Coaching]]
- [[../../job-hunting-priority|Job-Hunting Priority]]
- [[../../knowledge/core-ai-security/_index|Core AI Security knowledge base]]
- [[../../knowledge/strix/_index|Strix sub-hub]]
