---
tags: ["job-categories", "facet", "navigation", "hub", "job-hunting"]
related: ["ai-agent-wiki/00-index", "ai-agent-wiki/career-coaching", "ai-agent-wiki/job-hunting-priority"]
created: 2026-09-10
job-hunting: true
---

# Job Categories (facet)

> **Job-first navigation over the knowledge base** — pick the role you're targeting, get a curated reading list. The actual content lives in `knowledge/` (the topical subtrees); this hub is the index, not the source of truth. Job information (interview prep, salary, certifications) is in [[career-coaching]].

## The 5 roles

| Role | Reading time | What you're optimizing for |
|---|---|---|
| [[security-engineer/_index\|Security Engineer]] | 2-3 weeks | Threat models + controls. Defense-in-depth. Compliance. |
| [[ai-engineer/_index\|AI Engineer]] | 4-6 weeks | Agent runtimes + RAG + evaluation + observability. |
| [[ai-applied-engineer/_index\|AI Applied Engineer]] | 3-4 weeks | Production LLM apps. Prompting + tool-use + guardrails. |
| [[ai-native-developer/_index\|AI-Native Developer]] | 1-2 weeks | Using AI to ship faster. Plugin architecture. LLM-as-collaborator. |
| [[dev-tools-engineer/_index\|Dev-Tools Engineer]] | 2-4 weeks | Building plugin marketplaces, MCP servers, eval harnesses. The dev-harness-kit angle. |

## How to use this

- **Day 1 of prep**: read the role's `_index.md` — it's a curated facet index over the relevant knowledge base leaves.
- **Day 7**: cross-reference with [[job-hunting-priority]] for the priority-sorted interview-prep list (regardless of role).
- **Day 30**: cross-reference with [[career-coaching]] for the global-first certifications + 90-day plan.

## Cross-cutting resources (apply to all roles)

- [[career-coaching]] — junior-level career coaching dossier (3 staged research files in `_research/`)
- [[job-hunting-priority]] — priority-sorted reading list across all roles
- [[knowledge/core-ai-security/_index\|Core AI Security]] — security knowledge base (35 leaves)
- [[knowledge/agent-engineering/_index\|Agent Engineering]] — agent engineering skills (7 leaves)
- [[knowledge/ai-engineering-tooling/_index\|AI Engineering Tooling]] — tools and concepts (7 leaves)
- [[knowledge/strix/_index\|Strix sub-hub]] — operational pentest tool

## How this was built

Each role's `_index.md` is a **facet index** — a curated, hand-picked subset of leaves from the topical subtrees in `knowledge/`, organized by topic category. The leaves themselves are NOT duplicated; only the references are.

When the underlying leaves are updated, the facet indexes stay in sync through Obsidian's `[[wikilink]]` resolution.

## Related

- [[00-index|AI Agent Wiki Index]] — master catalog
- [[career-coaching]] — junior-level coaching dossier
- [[job-hunting-priority]] — priority-sorted reading list
