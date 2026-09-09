---
tags: ["career", "job-hunting", "junior-swe", "junior-security", "portfolio", "dev-harness-kit", "resume", "interview-prep"]
related:
  - ai-agent-wiki/career-coaching/junior-dev-security-career-2026/_index
  - ai-agent-wiki/career-coaching/junior-dev-security-career-2026/required-technical-skills-junior-swe
  - ai-agent-wiki/career-coaching/junior-dev-security-career-2026/required-technical-skills-junior-security
  - ai-agent-wiki/career-coaching
  - ai-agent-wiki/job-hunting-priority
created: 2026-09-10
---

# Resume / portfolio positioning — dev-harness-kit

> **TL;DR**: The dev-harness-kit portfolio is unusually strong for a junior — it signals plugin-architecture fluency, TDD discipline, agent-orchestration chops, and security-review workflow. Frame it the same way for both SWE and security tracks: "shipped a production plugin marketplace", with sub-claims tied to each *hiring signal they produce*.

The user's assumed portfolio is [sh-ai-x/dev-harness-kit](https://github.com/sh-ai-x/dev-harness-kit), a Claude Code / Codex plugin marketplace with skills like `add_wiki`, `bootstrap`, `process_clippings`, `research`, `review`, `security`, `eval`, etc. This is a *unusually strong* junior portfolio — the positioning must make that visible.

**What the portfolio signals (frame these on the resume):**

- **Plugin-architecture fluency.** A working plugin marketplace requires: package manifest (plugin.json), skill bundle (SKILL.md + scripts), dual-runtime support (Claude Code + Codex), version compatibility matrix, install/uninstall lifecycle. Juniors typically don't have any of these — this is mid-level engineering competence.
- **TDD discipline.** `dev-kit:build-tdd` skill with a tdd-guard hook is a visible commitment to test-first development. The hook is enforced, not aspirational. Hiring managers reading the README understand this immediately.
- **Agent-orchestration chops.** Multiple skills orchestrated via the harness runner; sub-agent delegation; per-step verification loops. This is the 2026 differentiator — most juniors have *used* Claude Code; few have built infrastructure around it.
- **Security review workflow.** `dev-kit:security` skill that runs an 11-dimension OWASP / LLM01–LLM10 fan-out, then verifies findings before reporting. This is a security-aware portfolio, not just a coding one.
- **AI-EVAL discipline.** `dev-kit:evaluate` skill with rubric-driven LLM-as-judge that gates merges. The eval-as-gate pattern is the 2026 standard for AI-adjacent repos.
- **Maintenance + observability.** `dev-kit:docs-maintenance`, `dev-kit:token-analyzer`, `dev-kit:code-viz` — the *operational* engineering skills most juniors lack. The presence of these signals production-readiness mindset.
- **Documentation-as-product.** The skill bundle's `SKILL.md` convention is essentially documentation-portfolio in disguise. Every skill teaches a teammate (or an LLM agent) how to use it — clear writing, runnable examples, failure modes.

**How to position on a 1-page resume:**

- Pin the portfolio link under a prominent "Selected Work" block; not buried under "Skills".
- Lead the project description with the architectural choices that are unusual for a junior: "Built a dual-runtime plugin marketplace with TDD-enforced hooks, parallel-fan-out security review, and LLM-as-judge eval gates — applied to a 7-pane parallel research workflow that produced 18 staged research dossiers."
- Quantify: number of skills, number of commits, lines of code, number of test cases, eval pass-rate.
- Tie each architectural choice to the *hiring signal it produces*: TDD-enforced hooks → "writes code that someone else can maintain", security-review skill → "thinks adversarially about their own work", eval gates → "measures before claiming improvement" (the HELM through-line).

**Resume framing for the SWE track:**

> "Built and operate a Claude Code / Codex plugin marketplace (15+ skills, dual-runtime) covering TDD, AI-eval, security review, and code-visualization. The plugin architecture (plugin.json + SKILL.md + hooks) is the same shape used by enterprise Claude deployments; the codebase is structured to demonstrate production-readiness — every skill has tests, every change has a pre-commit review gate, every release has a deterministic eval-set run."

**Resume framing for the security track:**

> "Built a security-review skill for the Claude Code / Codex plugin marketplace that runs an 11-dimension fan-out of OWASP Top 10 + LLM01–LLM10 + supply-chain checks, then adversarially verifies findings before reporting. The skill is the operational backbone of a 7-pane parallel research workflow covering NIST AI RMF, EU AI Act, MITRE ATLAS, and OWASP AI Security & Privacy Guide. Demonstrates: security-as-engineering-discipline, AI-threat literacy, structured-review methodology."

**Both framings are the same portfolio, framed differently.** The security framing is *stronger* than the SWE framing because the market for junior security is more constrained than for junior SWE — fewer applicants, higher salary bands, and a clear certification path.

**Cover-letter anchor paragraph:**

> "My portfolio ([github.com/sh-ai-x/dev-harness-kit](https://github.com/sh-ai-x/dev-harness-kit)) is a Claude Code / Codex plugin marketplace with 15+ skills covering TDD, AI-eval, security review, and code visualization. I built it as production engineering, not a side project: every skill has tests, every change goes through a structured review gate, every release runs an eval suite. The most-relevant signal for this role is the `dev-kit:security` skill, which performs an 11-dimension fan-out review (OWASP Top 10 + LLM01–LLM10 + supply-chain) — built because I wanted to use AI agents to ship safer code, not just more code."

## Related

- [[_index|Junior SWE + Security Pro sub-hub]]
- [[required-technical-skills-junior-swe|Required technical skills for junior SWE 2026]]
- [[required-technical-skills-junior-security|Required technical skills for junior security pro]]
- [[../career-coaching|career-coaching major hub]]
- [[../../job-hunting-priority|job-hunting-priority]]
