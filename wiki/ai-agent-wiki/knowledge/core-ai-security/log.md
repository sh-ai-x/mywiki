# Core AI Security — Change Log

## [2026-09-08] research | OWASP LLM Top 10 — 2026 edition
Added new leaf note `essential/owasp-llm-top-10-2026.md` covering the 2026-08-03 release: same 10 categories with major reordering (Excessive Agency #6 → #3, Unbounded Consumption #10 → #6 with "denial of wallet" reframing, Misinformation #9 → #7, Improper Output Handling #5 → #10). 75% community vote / 25% incident data methodology (6,639 incidents reviewed — first weighted blend). New cross-references to NIST AI 600-1, MITRE ATLAS, CWE, and the OWASP Top 10 for Agentic Applications. The 2025 file is retained as a historical reference; both are linked in `essential/_index.md`.

## [2026-09-08] restructure | Strix sub-hub moved out of core-ai-security
Per design clarification: Strix is a sibling wiki of core-ai-security, not nested under it. Moved `core-ai-security/strix/` up one level to `wiki/ai-agent-wiki/strix/`. Updated `core-ai-security/_index.md` to reference Strix as a sibling. Wiki-map updated to show Strix as a top-level AI Dev Tools entry rather than a sub-tier of core-ai-security.

## [2026-09-08] restructure | importance-tier reorg + Strix sub-hub
Replaced the flat `threats/` + `defenses/` + `frameworks/` tri-split with an importance-tier layout: `essential/` (8 must-know), `practical/` (11 implementation patterns), `specialized/` (15 deep-dive references). Added a new `strix/` sub-hub with 3 new leaf notes (threat-coverage, ci-integration, as-a-defense-signal) covering Strix's role in the core-ai-security knowledge base. (Strix was later moved out — see above.)

## [2026-09-07] init | core-ai-security (root + 3 sub-hubs + 34 leaf notes)
First creation of the core-ai-security knowledge base from three two-hour research dossiers: threats (14 sections), defenses (10 sections), frameworks (10 sections). 38 files total under `wiki/ai-agent-wiki/core-ai-security/`.
