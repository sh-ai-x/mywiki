# AI Agent Wiki — Change Log

## [2026-09-07] restructure | Core AI Security (root + 3 sub-hubs + 34 leaf notes)
Replaced flat 3-file layout (threats/defenses/frameworks as numbered leaf notes) with hierarchical 3-level structure: `ai-agent-wiki/core-ai-security/{threats,defenses,frameworks}/<section>.md`. Each research section is now its own leaf note with descriptive kebab-case filename (no numbers). 1 root hub + 3 sub-hubs + 34 leaf notes = 38 files total. Staged dossiers all point to their sub-hub's `_index.md` as `promoted_to`. wiki-map.md AI Dev Tools section updated to show the hierarchy.

## [2026-09-07] ingest | Core AI Security — Threats (14 leaf notes)
Two-hour research dossier (`_research/core-ai-security-threats.md`, 919 lines, 60+ sources) split into 14 leaf notes: executive-summary, owasp-llm-top-10, prompt-injection, jailbreaks, training-time-attacks, inference-time-attacks, adversarial-examples, supply-chain, agent-specific-threats, privacy-attacks, incident-timeline-2023-2026, emerging-threats-2026, detection-monitoring, recommended-reading. Threats sub-hub at `threats/_index.md`.

## [2026-09-07] ingest | Core AI Security — Defenses (10 leaf notes)
Two-hour research dossier (`_research/core-ai-security-defenses.md`, 934 lines, 31+ sources) split into 10 leaf notes: guardrails, system-prompt-hardening, retrieval-filtering, action-allowlisting, sandboxing, red-team-methodology, training-time-defenses, inference-time-defenses, monitoring, defense-in-depth-architecture. Defenses sub-hub at `defenses/_index.md`.

## [2026-09-07] ingest | Core AI Security — Frameworks (10 leaf notes)
Two-hour research dossier (`_research/core-ai-security-frameworks.md`, 812 lines, 28+ sources) split into 10 leaf notes: nist-ai-rmf, iso-iec-42001, eu-ai-act, mitre-atlas, owasp-ai-security-guide, owasp-llm-top-10, cisa-nsa-fbi-guidance, vendor-sdks, industry-overlays, implementation-playbook. Frameworks sub-hub at `frameworks/_index.md`.

## [2026-09-10] add_wiki | Per-section leaf promotion for the 3 career dossiers (hierarchical mode)
Three panes ran in parallel via herdr (w42:p2/p3/p4) to promote the career-coaching dossiers from single-hub summaries to per-section leaf trees. Total 41 new .md files written:

| Dossier | Sections | Leaves | Sub-hub | Total |
|---|---|---|---|---|
| `junior-dev-security-career-2026` | 13 | 13 | `_index.md` | 14 |
| `junior-ai-engineer-career-2026` | 13 | 13 | `_index.md` | 14 |
| `security-job-hunting-korea-2026` | 12 | 12 | `_index.md` | 13 |

Each leaf note: H1 = section title (no leading number), TL;DR distilled from the first non-heading/non-table sentence, full body content, `## Related` linking to sub-hub + 1-2 sibling sections. Each sub-hub: H1 + TL;DR + `## Leaf Notes` (with all `[[wikilinks]]`) + `## Source` (back to staged research) + `## Related` (cross-sibling). All staged files' `promoted_to:` updated to point at the new sub-hub (one pane did this automatically; I fixed the other two manually). Frontmatter `priority: high`, `job-hunting: true`, `interview-prep` implied via the career-coaching subtree.

The original `career-coaching.md` synthesis hub is unchanged and now serves as the **entry point** for the career subtree, with the per-dossier sub-hubs acting as the detailed reading lists. Together: 1 entry-point hub + 3 sub-hubs + 38 per-section leaves = 42 career-related files under `wiki/ai-agent-wiki/career-coaching/`.

## [2026-09-10] add_wiki | Stale promoted_to paths fixed after knowledge/ + notes/ move
Re-ran `/obsidian-organize:add_wiki` per the user's "research된 결과를 바탕으로" prompt. 6 of the 9 staged research files had `promoted_to:` paths that referenced the OLD `wiki/ai-agent-wiki/<topic>/` location; after the 2026-09-10 layout change, those topic subtrees live under `wiki/ai-agent-wiki/knowledge/<topic>/` (and the numbered `18-strix` note under `wiki/ai-agent-wiki/notes/`). Fixed:
- `core-ai-security-threats.md` → `knowledge/core-ai-security/threats/_index.md`
- `core-ai-security-defenses.md` → `knowledge/core-ai-security/defenses/_index.md`
- `core-ai-security-frameworks.md` → `knowledge/core-ai-security/frameworks/_index.md`
- `agentops-workbench.md` → `knowledge/agent-engineering/agentops-workbench/_index.md`
- `ai-llm-vlm-tooling.md` → `knowledge/ai-engineering-tooling/ai-llm-vlm-tooling/_index.md`
- `strix.md` → `notes/18-strix.md`

The 3 career-coaching dossiers (junior-dev-security / junior-ai-engineer / security-job-hunting-korea) all have `promoted_to: wiki/ai-agent-wiki/career-coaching.md` — still valid (single-hub synthesis pattern, no per-section leaves). Per-section leaf-note promotion is opt-in: run with `--hierarchical` (auto-enables at ≥ 5 sections) if per-section leaves are wanted. Each appended a "## Layout-fix note" body section explaining the path correction. No new leaf notes created — the 6 file edits are pure frontmatter + body-trailer fixes.

## [2026-09-10] restructure | Job-categories facet + knowledge/ + notes/ layout change
Major layout reorganization per user request (process_clippings spirit applied to existing content):

- **Created `job-categories/` facet layer** with 5 sub-hubs: `security-engineer/`, `ai-engineer/`, `ai-applied-engineer/`, `ai-native-developer/`, `dev-tools-engineer/`. Each sub-hub is a curated facet-index over the existing knowledge/ leaves — no leaf duplication, just curated reading lists by job × topic category. Master hub at `job-categories/_index.md`.
- **Moved 4 existing topic subtrees into `knowledge/`**: `core-ai-security/`, `agent-engineering/`, `ai-engineering-tooling/`, `strix/`. ~70 leaf notes + 8 hubs relocated.
- **Moved numbered notes into `notes/`**: `19-context-aware-pentesting.md` (only the actually-existing numbered note; 17 and 18 were wiki-map references but never wrote files).
- **Updated 200+ wikilinks globally** — every reference to `core-ai-security/`, `strix/`, `agent-engineering/`, `ai-engineering-tooling/`, `18-strix`, `19-context-aware-pentesting` updated to the new `knowledge/...` and `notes/...` paths.
- **`wiki-map.md`** rewritten with the new 3-section structure: 🚀 Start here (job-categories + career-coaching + job-hunting-priority), 🤖 AI Dev Tools (root-level numbered notes), 📚 Knowledge Base (the 4 topic subtrees), 🪵 System & Logs.

The new navigation: **job-first** via `job-categories/` facet, **topic-first** via `knowledge/` subtrees, **interview-prep** via `job-hunting-priority.md`. The user's career-coaching research (3 staged dossiers) is reachable both directly (via career-coaching hub) and via the relevant role-specific sub-hubs.

## [2026-09-10] ingest | Career Coaching — 3 dossiers (junior SWE+security / AI engineer / Korean security)
Three new staged research files at `_research/`:
- `junior-dev-security-career-2026.md` (64 KB / 713 lines / 12 sections + 1 global-first-filter)
- `junior-ai-engineer-career-2026.md` (72 KB / 879 lines / 11 sections)
- `security-job-hunting-korea-2026.md` (67 KB / 833 lines / 12 sections)
Researched in parallel via 3 herdr panes (w42:p2/p3/p4). User refinement applied: **global standards as the baseline, Korean-market context only where it diverges**. Each dossier ends with a §12/§13 "global-first filter" reclassifying every cert + skill as Global / Korean-context / Both. Korean-only certs (정보처리기사, 정보보안기사, ISMS-P 심사원) explicitly downplayed — the dev-harness-kit portfolio reframes for global signal-readers. Synthesized as a single hub at `wiki/ai-agent-wiki/career-coaching.md` with 90-day action plan + comp-path table. Wiki-map updated to show the new sibling.

## [2026-09-09] restructure | Job-hunting-focused reorganization (3 panes parallel)
Reorganized `wiki/ai-agent-wiki/` for AI/ML/Security/Agent engineering interview prep. Three panes ran in parallel via herdr (w42:p2/p3/p4): pane A curated `core-ai-security/` with `priority:` tags (5 critical / 11 high / 11 medium / 8 low) + `interview-prep` tags on critical/high; pane B promoted `_research/agentops-workbench.md` → new `agent-engineering/` subtree (7 leaves, 3 critical / 2 high / 2 medium); pane C curated `ai-engineering-tooling/` by dropping PKM-flavored leaves to `_archive/` (4 files) and extracting the §11 concept-deep-dive as a dedicated leaf (7 surviving leaves, 3 critical / 3 high / 2 medium). Created `job-hunting-priority.md` synthesis hub at the wiki root that orders all `interview-prep` leaves across subtrees by priority for active study. Wiki-map rewritten with the new 4-major-subtree topology + the job-hunting hub as the entry point. PKM / evergreen-notes / paper-deep-dive content archived, not deleted.

## [2026-09-09] ingest | AI Engineering Tooling (1 sub-domain + 10 leaf notes)
Two-hour research dossier (`_research/ai-llm-vlm-tooling.md`, 17.8 KB, 18 sources, status: promoted) distilled into a hierarchical leaf-note tree under `wiki/ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/`. Covers the 2026 AI-engineering landscape: agent frameworks (LangChain / LangGraph / LangSmith three-role split + alternatives), RAG patterns (naive / GraphRAG / agentic / reranking), VLMs (GPT-4o / Gemini 2.0 / Claude 3.5 benchmarks + pricing), and the LLM-Wiki personal-knowledge pattern. Wiki-map updated to show the new sibling under ai-agent-wiki.

## [2026-09-07] ingest | Context-Aware Pentesting (19)
Clipping (`Clippings/AI Penetration Testing & Autonomous Security.md`) distilled into a new leaf note. Adds the persistent threat-model layer released 2026-04-16 to [[notes/18-strix]] — closes the business-logic / IDOR blind spot flagged as the weakest coverage area. Back-links to 18, 17, 11, 00.

## [2026-09-07] init | log.md
Per-domain change log started. Future ingests append here.
