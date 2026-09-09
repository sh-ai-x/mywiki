---
tags: ["ai-engineering", "llm-wiki", "ai-agent", "rag"]
related: ["ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/_index", "ai-agent-wiki/ai-engineering-tooling/_index", "ai-agent-wiki/ai-engineering-tooling/_index", "ai-agent-wiki/00-index"]
created: 2026-09-09
source: "_research/ai-llm-vlm-tooling.md"
---

# LLM-Wiki pattern — deep dive (appended 2026-09-09)

> The previous section (5) gave the high-level definition. This deep-dive extends

The previous section (5) gave the high-level definition. This deep-dive extends
with the operational rules that distinguish a working LLM-Wiki from a vault
that just *contains* LLM-related notes.

### The three laws

1. **One thesis per leaf.** Each note makes exactly one claim that a reader
   could not re-derive from the source docs alone. If a note covers two
   claims, split it.
2. **Every leaf has a TL;DR that survives the Obsidian preview cut.** Above
   the fold — the blockquote. Below the fold — the body. The TL;DR is the
   load-bearing piece; the body is the receipt.
3. **Every leaf has explicit `## Related` with `[[wikilinks]]`.** Graph
   edges are not emergent from co-occurrence; they are authored. A note
   without `## Related` is an isolated node — the LLM-Wiki pattern's
   whole value proposition dies when this discipline lapses.

### The Karpathy-style leaf shape

The pattern derives from [Karpathy's LLM-Wiki vision](https://karpathy.ai/)
and [Andy Matuschak's evergreen notes](https://notes.andymatuschak.org/Evergreens_notes):
small, dense, atomic, opinionated. Typical leaf size: 1–5 KB. Typical
section count: 3–6. Typical frontmatter: 3–7 flat tags, 2–5 related
paths, optional `source:` URL. The leaf does not aspire to be exhaustive;
the body is the *non-obvious* part.

### The Obsidian-specific layer

Three Obsidian behaviors make the pattern work in practice:

- **The local graph view** is built from the `[[wikilinks]]` in
  `## Related`. It's not just navigation — it's also the
  *retrieval surface* when the vault is indexed into a RAG pipeline.
- **Daily notes + MOC (Map of Content) notes** are the two
  index types. MOCs are themselves LLM-Wiki leaf notes that
  group other leaves by topic — see the canonical
  [Maggie Appleton "garden history" writeup](https://maggieappleton.com/garden-history)
  for the digital-garden lineage.
- **[Obsidian Publish](https://publish.obsidian.md/hub/02+-+Community+Expansions/00+-+Obsidian+Publish)**
  makes the vault publicly browsable without changing the local
  authoring flow — useful for shared team knowledge.

### Why this matters specifically for AI engineering

- **Decision logs** — every agent architecture decision (which
  framework, which retrieval pattern, which VLM) goes in as a leaf
  note. Future-you can `[[query]]` the vault instead of re-deriving.
- **Eval results** — every benchmark run, every ablation, every
  regression. The pattern's `related:` discipline makes "what was I
  comparing against" a one-click navigation.
- **Prompt versions** — each prompt iteration is a leaf, with
  `source:` pointing to the eval that justified it.
- **Incident writeups** — when an agent misbehaves in production,
  the post-mortem is a leaf note that the next incident responder
  can find.

### What NOT to put in an LLM-Wiki

- **Run logs / raw transcripts** — those go in a different substrate
  (log files, or a hermes-logs sub-vault). The wiki should be the
  *distilled* knowledge, not the source material.
- **Architectural diagrams as primary content** — a Mermaid diagram
  belongs as an inline section inside a leaf, not as its own note.
- **Code samples longer than ~50 lines** — link out to the source file
  instead.

### How to evaluate whether your wiki is working

Three operational signals:

1. **Retrieval rate** — how often, when you start a new task, do you
   open the wiki before opening a browser? Target: >80%.
2. **Link density** — `grep -c '\[\[' wiki/<domain>/` divided by total
   leaf count. Target: >4 links per leaf on average.
3. **TL;DR survival rate** — if you delete the body of every leaf and
   keep only the TL;DR blockquotes, do they still tell the story?
   If yes, the wiki is working. If no, the TL;DRs are summarizing
   the wrong thing.

### Tooling

- **`obsidian-organize`** (the plugin this vault uses) — formalizes
  the workflow as 5 skills: `research`, `add_wiki`, `process_clippings`,
  `bootstrap`, `remove_wiki`. Adds hierarchical mode (auto-promote
  multi-section research into per-section leaves + auto-generated
  `_index.md` hubs).
- **Dataview plugin** — SQL-like queries over the vault's
  frontmatter (`LIST FROM #ai-security WHERE contains(tags, "rag")`).
- **Templater plugin** — frontmatter templates per leaf type.
- **Smart Connections / Copilot** — semantic search across the vault,
  useful when `[[query]]` doesn't find what you remember writing.

### TL;DR for this section

A working LLM-Wiki is **dense, opinionated, and explicitly
connected** — the opposite of a dump of notes. The tooling
(obsidian-organize, Dataview, Templater) is necessary but not
sufficient; the discipline (one thesis per leaf, TL;DR up top,
authored edges in `## Related`) is what makes the vault useful
as long-term memory for an AI-engineering team.

## Related

- [[ai-llm-vlm-tooling/_index|ai-llm-vlm-tooling sub-hub]] — all ai-llm-vlm-tooling leaf notes
- [[knowledge/ai-engineering-tooling/_index|ai-engineering-tooling hub]] — top-level hub
- [[ai-agent-wiki/00-index|AI Agent Wiki Index]] — master catalog
