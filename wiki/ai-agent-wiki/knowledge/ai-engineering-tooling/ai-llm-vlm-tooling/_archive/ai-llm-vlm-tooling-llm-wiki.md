---
tags: ["ai-engineering", "rag", "llm-wiki"]
related: ["ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/_index", "ai-agent-wiki/ai-engineering-tooling/_index", "ai-agent-wiki/ai-engineering-tooling/_index", "ai-agent-wiki/00-index"]
created: 2026-09-09
source: "_research/ai-llm-vlm-tooling.md"
---

# LLM-Wiki — the "llm wiki" in the topic

> LLM-Wiki is a personal-knowledge-management pattern that combines an Obsidian vault (Markdown files + bidirectional links + graph view) with LLM-assisted ingestion, distillation, and querying. The canonical reference implementation is `hermes-wiki-super/`, and the `obsidian-organize` plugin (v0.5...

LLM-Wiki is a personal-knowledge-management pattern that combines an Obsidian vault (Markdown files + bidirectional links + graph view) with LLM-assisted ingestion, distillation, and querying. The canonical reference implementation is `hermes-wiki-super/`, and the `obsidian-organize` plugin (v0.5.0) formalizes the workflow:
- `research` — stage raw material with proper frontmatter
- `add_wiki` — promote staged research into Karpathy-style leaf notes (TL;DR blockquote, flat tags, related list, ## Related wikilinks)
- `process_clippings` — distill raw Clippings/ into leaf notes
- `remove_wiki` — retire a leaf note + clean up back-links

The supported layout (2026) is `wiki/<domain>/<slug>.md` for flat notes, or `wiki/<domain>/<slug>/<section>.md` + auto-generated `_index.md` hubs for multi-section research. Hierarchical mode auto-enables when a staged research has ≥ 5 numbered sections.

A wiki built this way gets:
- A dense Obsidian graph (every note has frontmatter `related:` + body `## Related` with [[wikilinks]])
- LLM-queryable: drop the vault into a RAG index, or use an LLM with file-system tools
- Karpathy-style leaf discipline: each note has one thesis, kept under ~5 KB, with a TL;DR that survives the Obsidian preview cut

The pattern matters for AI engineering specifically because:
- LLM agent logs, prompts, eval results, architecture decisions — all want to be notes, not Slack threads
- The same vault serves as both human-readable documentation AND an LLM's long-term memory via retrieval
- The `related:` discipline is what makes retrieval actually work (without explicit edges, vector search returns adjacent chunks that don't tell the story)

## Related

- [[ai-llm-vlm-tooling/_index|ai-llm-vlm-tooling sub-hub]] — all ai-llm-vlm-tooling leaf notes
- [[knowledge/ai-engineering-tooling/_index|ai-engineering-tooling hub]] — top-level hub
- [[ai-agent-wiki/00-index|AI Agent Wiki Index]] — master catalog
