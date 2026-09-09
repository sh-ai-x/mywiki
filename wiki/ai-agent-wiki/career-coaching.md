---
tags: ["career", "job-hunting", "junior", "swe", "security", "ai-engineer", "korea", "interview-prep", "global", "hub"]
related: ["ai-agent-wiki/00-index", "ai-agent-wiki/job-hunting-priority", "ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/agent-engineering/_index", "ai-agent-wiki/ai-engineering-tooling/_index"]
created: 2026-09-10
priority: high
job-hunting: true
global-first-filter: applied
---

# Career Coaching (junior-level, global-first with Korean context)

> **Career-coaching dossier for 신입 / junior candidates across three tracks** — classic SWE + security pro, AI engineer, and Korean security job-hunting. The user's refinement directive (2026-09-10) is applied throughout: **global standards as the baseline, Korean-market context only where it diverges**. Korean-only certifications (정보처리기사, 정보보안기사, ISMS-P 심사원) are marked but de-emphasized — they should NOT be the basis for a career decision if the user might one day work outside Korea.

The full research dossiers live in `_research/` — they're the source of record. This hub is the reading-list entry point.

## The 3 dossiers

| Dossier | Track | Sections | Size | When to read |
|---|---|---|---|---|
| [[_research/junior-dev-security-career-2026.md\|Junior SWE + Security Pro]] | Classic software + security engineering | 13 | 64 KB / 713 lines | Day 1 of interview prep — this is the broadest scope |
| [[_research/junior-ai-engineer-career-2026.md\|Junior AI Engineer]] | AI / ML / agent / LLM roles | 12 | 72 KB / 879 lines | If you're targeting AI engineering roles — add to Day 1 |
| [[_research/security-job-hunting-korea-2026.md\|Security Job-Hunting Korea]] | Korean security market + portfolio positioning | 14 | 67 KB / 833 lines | Day 5 — read alongside the classic-SWE dossier |

## The global-first principle (applied to all 3 dossiers)

> **Global standards are the baseline; Korean-market context is a layer, not the foundation.**

Every item across the 3 dossiers is now tagged:
- **`Global`** — universally recognized (CISSP, OSCP, Python, AWS Security Specialty, RAG, LangGraph, etc.)
- **`Korean-context`** — required in Korea but not globally valued (정보처리기사, ISMS-P, NCS 자기소개서, etc.)
- **`Both`** — valued in both (CISSP at Korean 금융 firms, certain tools, etc.)

The 신입 신입-career advice is built around **Global** items as the foundation, with **Korean-context** layered on top only if targeting Korea specifically.

## Cross-cutting signals — the dev-harness-kit portfolio

All 3 dossiers emphasize how the user's dev-harness-kit plugin marketplace (818 commits, MIT, Claude/Codex parity) translates to global job-market signals:

| dev-harness-kit artifact | Global market signal |
|---|---|
| Plugin marketplace structure | "Built a software marketplace with skill versioning" |
| Hierarchical research-promotion | "Built a content-tooling pipeline that auto-splits long docs" |
| TDD-gated security | "Built a CI-gate enforcing TDD before merge" |
| `security` skill (OWASP-style review) | "Built an OWASP Top-10-aware code review tool" |
| `review` skill (multi-dim LLM-as-judge) | "Built an LLM-as-judge review workflow" |
| `bootstrap` skill (vault scaffolding) | "Built an opinionated project-setup tool" |

**The single highest-ROI job-hunting action** (called out in pane C): translate the dev-harness-kit README, the add_wiki skill examples, and the marketplace listing into English. Most non-Korean reviewers will read the README first.

## 90-day action plan — global first, Korean layer at the end

### Days 1-30 — Global foundation (every 신입 should do this)
- Python + TypeScript fundamentals
- One cloud cert (AWS Cloud Practitioner or equivalent)
- OWASP Top 10 reading (the 2026 edition)
- Two security CTFs (TryHackMe / HackTheBox — **English-language writeups**)
- Publish one English-language technical writeup
- **dev-harness-kit README in English**

### Days 31-60 — Global portfolio + first certs
- CompTIA Security+ OR AWS Cloud Practitioner + AWS Security Specialty
- If red-team: OSCP path start (PEN-200)
- If blue-team: BTL1 / Splunk Free certs
- Two OSS contributions to a global project
- One conference talk proposal submitted to a global conference

### Days 61-90 — Korean-market layer (OPTIONAL, only if targeting Korea)
- 정보처리기사 / 정보보안기사 (Korean-cert, only if specifically needed)
- NCS 자기소개서 draft (Korean govt-application format)
- Connect with 5 Korean security engineers on LinkedIn
- Apply to **≥30 global + ≥20 Korean** employers in parallel

## Comp paths by ceiling (for reference)

| Path | 1 yr | 3 yr | 5 yr |
|---|---|---|---|
| Korean SI (안랩/시큐브/Penta) | 45-55M KRW | 55-70M | 70-90M |
| Korean FAANG-equiv (네/카/쿠/토) | 60-80M | 90-120M | 130-180M |
| Korean 중견/대기업 (삼성SDS, LG CNS) | 50-60M | 65-80M | 80-110M |
| **Global FAANG (US remote)** | $120-180K | $180-280K | $300-450K |
| **Global startup (US remote)** | $100-140K | $150-220K | $220-320K |
| **Global defense-adjacent (Anduril, Shield AI)** | $130-180K | $180-260K | $260-360K |

**Recommendation**: don't silo. Apply to both Korean and global in parallel. Same code, 3-4× the comp.

## Related

- [[job-hunting-priority]] — priority-sorted reading list of all interview-prep leaves
- [[00-index|AI Agent Wiki Index]] — master catalog
- [[knowledge/core-ai-security/_index|Core AI Security]] — security knowledge base
- [[knowledge/agent-engineering/_index|Agent Engineering]] — agent engineering skills
- [[knowledge/ai-engineering-tooling/_index|AI Engineering Tooling]] — tools and concepts
- [[knowledge/strix/_index|Strix sub-hub]] — operational pentest tool
