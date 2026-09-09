---
topic: junior-ai-engineer-career-2026/08
tags: ["career", "job-hunting", "junior", "ai-engineer", "resume", "portfolio", "dev-harness-kit", "interview-prep", "global-first"]
related: ["ai-agent-wiki/career-coaching/junior-ai-engineer-career-2026/07-interview-signals-the-market-uses-2026"]
source: "_research/junior-ai-engineer-career-2026.md#8"
created: 2026-09-10
priority: critical
job-hunting: true
global-first-filter: applied
---

# 8. Resume / portfolio positioning for AI engineer roles

This is the section that makes the user's specific portfolio — `sh-ai-x/dev-harness-kit` — concrete.

### 8.1 What the portfolio actually demonstrates

`sh-ai-x/dev-harness-kit` is a Claude Code / Codex plugin marketplace that ships:
- An enforced-dev-workflow skills plugin (planning, TDD, debugging, review, security, CI).
- The `obsidian-organize` plugin: research, add_wiki, process_clippings, remove_wiki — promoting raw material into Karpathy-style leaf notes with hierarchical mode and auto-generated `_index.md` hubs.

(Source: https://github.com/sh-ai-x/dev-harness-kit, accessed 2026-09-10; `obsidian-organize` references via https://github.com/hashicorp/awesome-ai-plugins and adjacent ecosystem pages.)

What this demonstrates to a hiring panel:

1. **Plugin-marketplace architecture** — a real Claude Code / Codex plugin shipping the full delivery loop. This is the same architectural pattern as Cursor / Continue.dev / Cody at the API level; the resume can frame it as "built and shipped a production plugin marketplace" rather than "side project on GitHub."
2. **Karpathy-style LLM-Wiki tooling** — the `obsidian-organize` plugin formalizes the LLM-Wiki pattern (concept-oriented leaf notes, dense `[[wikilinks]]`, `## Related` per leaf, `_index.md` hubs). This maps directly to §7.3: technical-writing as a hiring signal.
3. **Agent-engineering system design** — the plugin orchestrates multiple sub-agents (planning, TDD, debugging, review) via the Claude Code / Codex plugin protocol. This is a graph-of-agents in code; it is precisely what the §3.3 framework section says you should be able to build.
4. **Security discipline** — the `dev-kit` plugin ships with a security review gate (`/dev-kit:security`) that runs OWASP-style checks. This maps to §5.3 (defense in depth) and to the AI security engineer role discussed in §1.

### 8.2 The positioning line — "demonstrated AI engineering skill, not a side project"

The single line that reframes the portfolio on a resume:

> **"Shipped `sh-ai-x/dev-harness-kit`, a Claude Code / Codex plugin marketplace (full delivery loop + Karpathy-style LLM-Wiki tooling) used to build this vault."**

Then list the sub-claims as bullets:

- *Plugin marketplace design* (Claude Code plugin protocol, Codex plugin protocol; versioned skill bundles; dual-runtime plugin layout).
- *Multi-agent orchestration* (graph-of-agents: plan / TDD / debug / review / security / CI agents; circular-fix loop; pre-commit hooks).
- *System-design signal* (`obsidian-organize` formalizes the LLM-Wiki pattern — concept-oriented, densely-linked notes; `## Related` edges; hub-and-spoke topology via `_index.md`).
- *Eval-harness integration* (the plugin ships with `/dev-kit:evaluate` and `/dev-kit:review`, mirroring RAGAS / DeepEval / promptfoo's role in §3.5).
- *Security discipline* (built-in security review gate, layered defense posture — maps to §5.3).

### 8.3 Curated vault as a second signal

The user also has the Obsidian vault at `/Users/sanghee/dev/mywiki/` with a `wiki/ai-agent-wiki/` subtree curated for *job-hunting relevance* (per pane C of the prior session). The vault itself demonstrates:

- **Systematic research** — staged files at `_research/` cite every claim with URL + access date.
- **Information architecture** — major hubs → sub-hubs → leaf notes; priority + `interview-prep` tags on the surviving leaves.
- **PKM discipline** — one thesis per leaf, TL;DR up top, `## Related` edges — exactly the LLM-Wiki pattern.

Pair this with the plugin: the *plugin builds the vault*, and the *vault is itself the artifact the plugin builds.* This self-referential structure is an interview story.

### 8.4 LinkedIn / resume phrasing (Korean market)

한국어 이력서에서의 한 줄:

> `sh-ai-x/dev-harness-kit` — Claude Code / Codex 플러그인 마켓플레이스 오픈소스 메인테이너 (멀티 에이전트 오케스트레이션 + LLM-Wiki 툴체인). GitHub에서 ⭐ 수와 실제 사용자 후증거 인용.
