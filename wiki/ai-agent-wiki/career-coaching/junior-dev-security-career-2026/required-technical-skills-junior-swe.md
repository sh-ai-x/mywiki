---
tags: ["career", "job-hunting", "junior-swe", "korea-2026", "technical-skills", "interview-prep"]
related:
  - ai-agent-wiki/career-coaching/junior-dev-security-career-2026/_index
  - ai-agent-wiki/career-coaching/junior-dev-security-career-2026/korean-swe-market-state
  - ai-agent-wiki/career-coaching/junior-dev-security-career-2026/coding-interview-prep-2026
  - ai-agent-wiki/career-coaching
  - ai-agent-wiki/job-hunting-priority
created: 2026-09-10
---

# Required technical skills for junior SWE 2026

> **TL;DR**: One strong general-purpose language (Python/TS/Go) + one frontend framework (Next.js default) + one cloud (AWS-heavy) + Docker/K8s + Git/CI + SQL + AI-tool fluency + one shipped portfolio artifact. Depth in one language + adjacent competence in a second beats polyglot breadth.

The 2026 junior signal stack is roughly: one strong general-purpose language + one frontend framework + one cloud platform + container basics + CI + SQL + one AI-tool fluency + one portfolio artifact that ships.

**Languages (pick a primary + one secondary):**

- **Python** — dominant for AI/data/backend services. Junior demand unchanged from 2024; expected at every AI-adjacent role.
- **TypeScript** — dominant for frontend + Node backend; mandatory at most startups.
- **Go** — high demand at infrastructure-heavy startups (Toss, 당근, Hyperconnect) and cloud-native roles. 신입 Go knowledge is a strong differentiator vs. the Java/TS-heavy pool.
- **Java/Kotlin** — still required at 대기업/금융 (카카오뱅크, 토스뱅크, KB국민카드, 신한은행, NHN). 신입 Java is fine; Kotlin is the differentiator.
- **Rust** — niche but growing; expected for systems work and at Web3-adjacent roles.

The strongest 신입 resumes in 2026 show a primary language (Python/Go/TS) + a deliberate secondary (one of Go/Rust/Kotlin). Multi-language polyglots with shallow depth are out — depth in one + adjacent competence in a second is in.

**Web frameworks (frontend):**

- **React** (still #1) + **Next.js** (App Router — server components, streaming SSR) is the 2026 default. 신입 Next.js experience (even a tutorial-grade project) is table stakes.
- **Vue** at Naver-line companies (Vue 3 + Nuxt).
- **Svelte / SolidJS** at a small number of startups; differentiator only.
- **React Native / Flutter** at mobile-only shops.

**Backend frameworks:**

- **Spring Boot (Java/Kotlin)** at 대기업/금융.
- **FastAPI / Django (Python)** at AI-adjacent and data-heavy shops.
- **NestJS / Express (TypeScript)** at TypeScript-first startups (Toss, 당근).
- **Gin / Echo / Fiber (Go)** at infrastructure-heavy startups.

**Cloud (pick one deep + know the others exist):**

- **AWS** — most common in postings (~70% of Korean cloud postings mention AWS first). Know S3, EC2, IAM, RDS, Lambda, VPC basics; know the Well-Architected Framework pillars.
- **GCP** — strong at AI/data shops (Looker, BigQuery, GKE).
- **Azure** — required for Microsoft-affiliated roles and any public-sector job.

AWS Solutions Architect Associate is the highest-ROI cloud cert for a junior SWE in 2026 (not the Security Specialty — that's for the security track).

**Containers + orchestration:**

- **Docker** is mandatory. Compose for local dev, multi-stage builds, layer caching, image size optimization — know the day-to-day.
- **Kubernetes** basics for mid-tier+ postings: pods, deployments, services, ingress, configmaps/secrets. K8s is no longer a "nice to have" — it's expected at any cloud-native role.
- **Helm** is a plus; **ArgoCD / Flux (GitOps)** is a differentiator.

**CI/CD + version control:**

- **Git** is non-negotiable. Trunk-based development, rebase vs. merge, interactive rebase, bisect for regressions. Junior candidates who can't cleanly resolve a merge conflict are eliminated at the live-coding stage.
- **GitHub Actions** (default for most), **GitLab CI** (heavy at Korean enterprise), **CircleCI / Buildkite** (a few).
- **Release engineering basics:** semantic versioning, changelogs, canary/blue-green deployments.

**Testing:**

- **Unit + integration testing** — must be able to write tests-first in the chosen primary language. Jest (TS), pytest (Python), Go's `testing` (Go), JUnit5 (Java).
- **Test pyramid awareness** — unit > integration > e2e; know when each is appropriate.
- **Property-based testing** (Hypothesis for Python, fast-check for TS) — a differentiator.
- **TDD** is the explicit discipline signal — see [dev-harness-kit](https://github.com/sh-ai-x/dev-harness-kit)'s `dev-kit:build-tdd` skill; juniors who can describe a TDD workflow out loud stand out.

**Databases:**

- **SQL (Postgres or MySQL)** — must be able to write a query with joins, CTEs, window functions; explain an EXPLAIN ANALYZE plan; design a normalized schema.
- **NoSQL (MongoDB / Redis)** — one document store + one cache. Don't claim deep expertise unless the resume supports it.
- **Vector DBs (Pinecone, Weaviate, pgvector)** — increasingly relevant at AI-adjacent shops; out of scope for pure SWE roles but a signal of "AI-fluent".
- **ORMs** — Prisma (TS), SQLAlchemy (Python), GORM (Go), JPA (Java). Know the gotchas (N+1, eager vs. lazy loading).

**AI-tool fluency (mandatory, not deep):**

- Know **one agentic coding tool** (Claude Code, Codex, Cursor, GitHub Copilot Workspace) deeply. Know when to use it and when *not* to. Know how to read its diff. Know the "explain before you accept" discipline.
- Know how to write **structured prompts** for code generation, code review, and test generation. The Claude Code / Codex plugin-marketplace portfolio at [dev-harness-kit](https://github.com/sh-ai-x/dev-harness-kit) is exactly this signal.
- **Do not** claim "AI engineer" skills unless the resume shows shipped AI work. "I use Cursor" is not an AI-engineering credential.

## Related

- [[_index|Junior SWE + Security Pro sub-hub]]
- [[korean-swe-market-state|Korean SWE market state (2026-Q3)]] — context for what employers ask
- [[coding-interview-prep-2026|Coding interview prep (2026)]] — how these skills show up in interviews
- [[../career-coaching|career-coaching major hub]]
- [[../../job-hunting-priority|job-hunting-priority]]
