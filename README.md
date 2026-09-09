# mywiki

A personal knowledge base kept as an [Obsidian](https://obsidian.md) vault. Plain Markdown files, versioned with git, wired together with `[[wikilinks]]` so the Obsidian graph is the primary way to navigate.

The exact folders and notes change constantly — this README only describes **how things are stored and the rules that keep it consistent**, not the current contents.

## How it is stored

Everything is a Markdown file in the repo. No database, no build step. Obsidian reads the folder directly; GitHub is the backup and history.

```
Clippings/        raw web captures, dropped in by the Obsidian Web Clipper
  processed/      originals moved here once distilled into wiki notes
_research/         staged research files — one topic per file, source-heavy
topic/             hand-written working notes and indexes
wiki/              the durable knowledge base (see below)
wiki-map.md        root hub note — the center of the graph
```

### The `wiki/` tree

Distilled, long-lived notes live here, grouped by domain:

```
wiki/<domain>/<slug>.md                      flat leaf note
wiki/<domain>/<slug>/<section>.md            hierarchical: one leaf per section
wiki/<domain>/<slug>/_index.md               sub-hub for a hierarchical topic
wiki/<domain>/log.md                         append-only change log for that domain
```

A note is either a **leaf** (one idea, written to be read on its own) or a **hub / `_index`** (links out to related leaves). Hubs hold links and context; leaves hold the actual knowledge.

## The pipeline

New knowledge moves through fixed stages:

1. **Capture** → a page lands in `Clippings/` (or a topic starts life in `_research/`).
2. **Research** → sources are gathered into a single `_research/<topic>.md` file with a `sources:` list in the frontmatter.
3. **Promote** → the research file is distilled into leaf notes under `wiki/<domain>/`, in Karpathy-style LLM-wiki form (tight, self-contained, explain-out-loud).
4. **Archive** → the original clipping moves to `Clippings/processed/`; the research file is marked promoted. Nothing is deleted.
5. **Record** → the domain's `log.md` gets an entry, and `wiki-map.md` is updated if a new hub appeared.

Retiring a note reverses this: archive its research, remove back-links, drop it from the map.

## Rules

- **One idea per leaf.** If a note needs an "and" in its title, split it.
- **Every note has YAML frontmatter.** Leaves carry at least `tags:` and `created:`; research files carry `sources:`; many leaves also carry `priority:` and `related:`.
- **Link, don't nest deeply.** Connection is expressed with `[[wikilink]]`, not folder depth. A link to a note that doesn't exist yet is fine — it's a TODO in the graph.
- **`kebab-case.md` filenames**, no leading numbers on hierarchical leaves (numbers are only used for a few root-level ordered notes).
- **`_index.md`** is the reserved name for a hub inside a folder.
- **Logs are append-only.** `wiki-map.md` and `log.md` files are edited additively; existing leaves are not silently rewritten during an unrelated promotion.
- **Originals are archived, never deleted** (`Clippings/processed/`, `_archive/`).

## Not in git

- `proposals/` — draft portfolio proposals, kept local.
- `.dev-kit/` — scratch/trace state written by agent tooling; not part of the knowledge base.
- `.obsidian/workspace.json` — per-machine editor layout.

Other `.obsidian/` config (plugins, appearance, graph settings) **is** tracked so the vault behaves the same on any machine.
