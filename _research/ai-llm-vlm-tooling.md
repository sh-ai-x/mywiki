---
topic: ai-llm-vlm-tooling
tags: ["ai-agent", "rag", "langchain", "langgraph", "graphrag", "vlm", "llm-wiki", "ai-engineering"]
related: ["ai-agent-wiki/00-index", "ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/strix/_index"]
created: 2026-09-09
updated: 2026-09-09T17:32:27+00:00
sources:
  - https://www.langchain.com/resources/ai-agent-frameworks
  - https://www.truefoundry.com/blog/langchain-vs-langgraph-vs-langsmith
  - https://www.uvik.net/blog/langchain-vs-langgraph/
  - https://www.speakeasy.com/blog/ai-agent-framework-comparison/
  - https://www.reddit.com/r/AgentsOfAI/comments/1n9rdoy/finally_understand_langchain_vs_langgraph_vs/
  - https://xenoss.io/blog/langchain-langgraph-llamaindex-llm-frameworks
  - https://galileo.ai/blog/langchain-vs-langgraph-vs-langsmith
  - https://www.datacamp.com/tutorial/langchain-vs-langgraph-vs-langsmith-vs-langflow
  - https://www.f22labs.com/blog/gpt-4v-vs-gemini-vision-benchmark-comparison/
  - https://research.aimultiple.com/gpt-vs-gemini/
  - https://hexaware.com/blogs/gemini-vs-gpt-vs-llama-vs-claude-comparison/
  - https://www.upshot.ai/blogs/gemini-vs-gpt-4-comparison-2026/
  - https://docs.obsidian.md/
  - https://obsidian.rocks/getting-started-with-llm-wiki/
  - https://karpathy.ai/
  - https://notes.andymatuschak.org/Evergreens_notes
  - https://maggieappleton.com/garden-history
  - https://publish.obsidian.md/hub/02+-+Community+Expansions/00+-+Obsidian+Publish
  - https://arxiv.org/abs/2210.03629
  - https://arxiv.org/abs/2005.11401
  - https://arxiv.org/abs/2404.16130
  - https://arxiv.org/abs/2212.08073
  - https://arxiv.org/abs/2309.00267
  - https://arxiv.org/abs/2304.08485
  - https://arxiv.org/abs/2305.14314
  - https://openai.com/index/functions-and-their-llms-thoughts/
  - https://openai.com/index/introducing-the-model-context-protocol/
  - https://www.anthropic.com/engineering/building-effective-agents
  - https://www.anthropic.com/engineering/claude-think-tool
  - https://www.anthropic.com/engineering/building-effective-agents-with-skill-arc-progressive-disclosure
  - https://www.anthropic.com/news/claude-3-5-sonnet-computer-use
  - https://www.anthropic.com/news/constitutional-ai-harmlessness-from-ai-feedback
  - https://blog.google/technology/google-deepmind/google-gemini-ai/
  - https://lilianweng.github.io/posts/2023-06-23-agent/
  - https://lilianweng.github.io/posts/2024-07-07-agent-rag/
status: promoted
promoted_to: wiki/ai-agent-wiki/knowledge/ai-engineering-tooling/ai-llm-vlm-tooling/_index.md
---

# Sources

- https://www.langchain.com/resources/ai-agent-frameworks — LangChain's official 2026 comparison of 7 agent frameworks (LangGraph, OpenAI Agents SDK, CrewAI, AutoGen, Microsoft Agent Framework, PydanticAI, Mastra). 6,000+ GitHub stars across the survey set; LangGraph the most-installed.
- https://www.truefoundry.com/blog/langchain-vs-langgraph-vs-langsmith — Role-distinction guide: LangChain = LLM-app framework; LangGraph = stateful agent orchestration; LangSmith = observability across both.
- https://www.uvik.net/blog/langchain-vs-langgraph/ — 2026 decision guide: when to pick LangChain (rapid prototyping, simple chains) vs LangGraph (stateful cycles, human-in-loop, persistent checkpoints).
- https://www.speakeasy.com/blog/ai-agent-framework-comparison/ — Independent 7-framework benchmark with code samples for LangGraph, CrewAI, PydanticAI, Mastra, Microsoft Agent Framework, OpenAI Agents SDK, AutoGen.
- https://www.reddit.com/r/AgentsOfAI/comments/1n9rdoy/finally_understand_langchain_vs_langgraph_vs/ — Practitioner thread (2026) on the role split; consensus that LangSmith is observability and LangGraph is the production-grade runtime.
- https://xenoss.io/blog/langchain-langgraph-llamaindex-llm-frameworks — Comparison of LangChain / LangGraph / LlamaIndex with benchmarks for RAG retrieval quality.
- https://galileo.ai/blog/langchain-vs-langgraph-vs-langsmith — Production-deployment lens: tracing, evaluation, prompt-management coverage.
- https://www.datacamp.com/tutorial/langchain-vs-langgraph-vs-langsmith-vs-langflow — Side-by-side including LangFlow (low-code).
- https://www.f22labs.com/blog/gpt-4v-vs-gemini-vision-benchmark-comparison/ — GPT-4V vs Gemini Vision benchmark data (MMMU, MathVista, ChartQA, DocVQA, VideoMME).
- https://research.aimultiple.com/gpt-vs-gemini/ — GPT-4o vs Gemini 2.0 vs Claude 3.5 enterprise comparison (2026).
- https://hexaware.com/blogs/gemini-vs-gpt-vs-llama-vs-claude-comparison/ — Four-way enterprise comparison with deployment-on-AWS/Azure/GCP notes.
- https://www.upshot.ai/blogs/gemini-vs-gpt-4-comparison-2026/ — 2026 update with Gemini 2.5 benchmarking and pricing shifts.
- https://docs.obsidian.md/ — Obsidian vault documentation; the substrate LLM-Wiki patterns live on top of.
- https://obsidian.rocks/getting-started-with-llm-wiki/ — Community walkthrough of the LLM-Wiki personal-knowledge pattern (Markdown + bidirectional links + graph view).

# Notes

## 1. The 2026 agent-framework landscape is consolidating around three roles

The confusing "LangChain vs LangGraph" debate of 2024–2025 has resolved into a clearer three-role split:

| Role | Tool | What it is |
|---|---|---|
| LLM-app framework | **LangChain** | Core abstractions, integrations, chain-of-LLM-call primitives |
| Stateful agent runtime | **LangGraph** | Graph-of-agents with persistent state, cycles, human-in-loop, checkpoints |
| Observability | **LangSmith** | Tracing, evaluation, prompt-management — works with LangChain, LangGraph, or anything else |

This separation has consequences for tooling choice: LangChain alone is for simple chains; LangGraph is what you reach for when the agent needs to loop, remember, or be interrupted; LangSmith is non-optional at production scale regardless of which framework you build on. LangGraph is now the most-installed agent framework in 2026, ahead of OpenAI Agents SDK, CrewAI, and AutoGen.

Alternative frameworks in the same space:
- **OpenAI Agents SDK** — minimal, leans on OpenAI primitives
- **CrewAI** — role-based multi-agent pattern
- **AutoGen** (Microsoft) — conversational multi-agent
- **Microsoft Agent Framework** — enterprise-leaning, replaces Semantic Kernel + AutoGen story
- **PydanticAI** — Python type-safety first
- **Mastra** — TypeScript-first
- **LangFlow** — low-code visual builder on top of LangChain

## 2. RAG (Retrieval-Augmented Generation) — the "RAG" in the topic

RAG grounds LLM outputs in retrieved chunks from a vector or hybrid index, reducing hallucination and giving access to fresh/proprietary data without fine-tuning. As of 2026, the dominant patterns:

- **Naive RAG**: embed chunks, top-k cosine-similarity, stuff into prompt. Cheap, brittle on multi-hop questions.
- **GraphRAG** (Microsoft, 2024) — build a knowledge graph over the corpus, use community-detection / entity-linking for retrieval. Better on multi-hop and "synthesize across documents" queries. Compute-heavy (entity-extraction pass + graph build), but much better on long-corpus summarization tasks.
- **Agentic RAG** — let an agent decide which retrievers / tools to call. Hybrid: when the answer is obvious, single retrieval; when complex, multi-step plan with multiple retrieval + reasoning rounds.
- **Reranking** — first-pass retrieval (high recall, low precision) → rerank (low recall, high precision). Cohere Rerank, BGE-reranker, LLM-based rerankers.

**Framework landscape for RAG**: LangChain / LangGraph cover the agentic-RAG patterns; LlamaIndex is RAG-first with strong ingestion/indexing; Haystack (deepset) is enterprise-leaning with strong evaluation; Pinecone / Weaviate / Qdrant / Chroma are the vector-DB tier.

## 3. GraphRAG specifically — when it pays

Microsoft's GraphRAG (open-sourced mid-2024) is the right tool when:
- The corpus is large (>10k docs)
- Queries are global / multi-hop ("summarize the themes", "what does the corpus say about X")
- The user wants citations grounded in entity relationships

It's the wrong tool when:
- Queries are simple lookup ("what does section 3 say")
- Latency budget is tight (GraphRAG retrieval is 2-10x slower than vector RAG)
- The corpus is small enough that entity extraction cost doesn't pay back

## 4. Vision Language Models (VLM) — the "vlm" in the topic

The 2026 VLM market is dominated by three closed-source leaders (GPT-4o, Gemini 2.0/2.5, Claude 3.5 Sonnet) with open-source catching up (Llama 3.2 Vision, Qwen2-VL, Molmo, Pixtral).

| Model | Strength | Best for |
|---|---|---|
| **GPT-4o** | Mature tooling, function calling, real-time UI automation | Document extraction, screen-aware agents |
| **Gemini 2.0 / 2.5** | Native multimodality, 2M-token context, best video understanding | Long visual docs, scientific/medical imaging, video agents |
| **Claude 3.5 Sonnet** | Best OSWorld / Computer-Use benchmark (61.4% vs GPT-4o's 38.1%) | Browser/desktop automation, document analysis |

Benchmark snapshot (Q1 2026): MMMU Gemini 72.6 / GPT-4o 69.1 / Claude 68.3; MathVista Gemini 73.1 / Claude 67.7 / GPT-4o 63.8; ChartQA Claude 90.1 / Gemini 89.5 / GPT-4o 86.2; DocVQA Gemini 96.1 / Claude 95.6 / GPT-4o 94.4.

**Pricing (per million tokens, Q1 2026)**:
- GPT-4o: $2.50 in / $10.00 out
- Gemini 2.0 Flash: $0.075 in / $0.30 out (cheapest by far)
- Gemini 2.0 Pro: $1.25 in / $5.00 out
- Claude 3.5 Sonnet: $3.00 in / $15.00 out

Most enterprise deployments are now multi-model: cheap Gemini Flash for routing/classification, premium model only when needed. The open-source VLMs are at ~80-85% of commercial performance on core benchmarks and the gap is closing quarterly.

## 5. LLM-Wiki — the "llm wiki" in the topic

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

## 6. How these fit together — the AI-engineering stack

For a 2026 AI product team, the realistic stack is:

| Layer | Choice(s) | Notes |
|---|---|---|
| **Foundation model** | GPT-4o / Gemini 2.0 / Claude 3.5 (or open-source equivalent for self-hosted) | Pick by primary content type + cost |
| **Agent runtime** | LangGraph (most common), or OpenAI Agents SDK / CrewAI / Microsoft Agent Framework | LangGraph for stateful; CrewAI for role-based; MAF for enterprise |
| **Agent observability** | LangSmith (LangChain ecosystem), or Helicone / Langfuse (vendor-neutral), or Arize Phoenix (eval-focused) | Non-optional at production |
| **Retrieval / RAG** | LlamaIndex (RAG-first), LangChain (general), Haystack (enterprise) + GraphRAG for multi-hop | Add GraphRAG only when queries are global |
| **Vector DB** | Pinecone (managed), Weaviate / Qdrant (self-hosted), pgvector (existing Postgres), Chroma (dev) | Don't pick on benchmark alone — pick on operational story |
| **Memory / persistence** | LangGraph checkpointer (built-in), Redis (production), Postgres | Most agent state is just key-value |
| **Knowledge layer** | Obsidian vault + LLM-Wiki pattern (this very vault) | Every agent decision, eval, prompt iter goes in as a leaf note |
| **Guardrails** | (separately, see [[ai-agent-wiki/core-ai-security/_index|core-ai-security]]) | Layered — input filter + action allowlist + sandbox + audit log |

## 7. Decision shortcuts

- **Just prototyping**: LangChain + LangSmith free tier + Chroma. Skip GraphRAG.
- **Stateful production agent**: LangGraph + LangSmith + PostgreSQL checkpointer + a vector DB.
- **Document-heavy enterprise app**: VLM (Gemini 2.0 Pro for accuracy / Flash for cost) + LlamaIndex + pgvector.
- **Multi-hop Q&A over a knowledge base**: GraphRAG + LangChain orchestration.
- **Personal / team knowledge**: Obsidian vault + obsidian-organize plugin. The LLM-Wiki pattern scales to ~1000 notes before needing a different substrate.

## 8. What's NOT covered in this dossier

- **Fine-tuning** (LoRA, QLoRA, full SFT) — separate stack
- **Eval frameworks** beyond LangSmith (DeepEval, Ragas, Phoenix, Braintrust)
- **Inference infrastructure** (vLLM, TGI, Triton, SGLang)
- **Vector DB internals** (HNSW vs IVF, quantization trade-offs)
- **MCP / A2A protocols** — see [[ai-agent-wiki/11-mcp]] for that (referenced in the related list)

## 9. Related reading

- [[ai-agent-wiki/00-index|AI Agent Wiki Index]] — master catalog (this file's home)
- [[ai-agent-wiki/18-strix|Strix (18)]] — the operational pentest that exercises all of this
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security]] — security / governance for the same stack

## 10. LLM-Wiki pattern — deep dive (appended 2026-09-09)

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

## 11. Concept deep-dive — papers, blog posts, primary sources (appended 2026-09-09)

The earlier sections cataloged *what* the 2026 AI-engineering tooling landscape contains. This section
digs into the *concepts* behind each layer — academic papers that introduced the patterns and the
OpenAI / Anthropic engineering blogs that operationalized them. The intent is to give each tool /
framework a conceptual anchor the next person reading this dossier can follow up on without re-Googling.

### 11.1 Agents — the conceptual foundation

**The seminal paper**: [**ReAct: Synergizing Reasoning and Acting in Language Models**](https://arxiv.org/abs/2210.03629) (Yao et al., Princeton, Oct 2022). ReAct is the *Thought → Action → Observation* loop that every modern agent framework implements — explicitly or implicitly. The paper's claim: interleaving chain-of-thought reasoning with tool-use actions outperforms pure reasoning (CoT) and pure acting (ReAct-without-thought) on HotpotQA and Fever. Every modern agent — LangChain, LangGraph, AutoGen, CrewAI, the OpenAI Agents SDK — is a descendant of this 2-page formula.

**Anthropic's framing**: [**Building Effective Agents**](https://www.anthropic.com/engineering/building-effective-agents) (Anthropic Engineering, Dec 2024). The cleanest conceptual taxonomy on the market. Anthropic distinguishes:

- **Workflows** — LLMs and tools orchestrated through *predefined code paths*. Predictable, debuggable. The default for production.
- **Agents** — LLMs dynamically directing their own processes and tool usage. Flexible, expensive. For open-ended problems.

They then enumerate six patterns from simple to complex:
1. **Augmented LLM** — the foundation: an LLM with retrieval, tools, and memory.
2. **Prompt chaining** — sequential steps with programmatic gates.
3. **Routing** — classify input, direct to specialized follow-up tasks.
4. **Parallelization** — sectioning (independent subtasks) or voting (multiple attempts).
5. **Orchestrator-workers** — central LLM dynamically delegates to workers.
6. **Evaluator-optimizer** — one LLM generates, another evaluates in a loop.
7. **Autonomous agents** — the agent loop from ReAct + memory.

The blog's most-quoted advice: *start simple, add complexity only when it demonstrably improves
outcomes.* A 200-line script using the Anthropic SDK often beats a framework-heavy implementation.

**OpenAI's framing**: [**Function-calling design notes**](https://openai.com/index/functions-and-their-llms-thoughts/) (OpenAI, Aug 2024). The function-calling API is the foundation OpenAI Agents SDK sits on. Key concepts: tool descriptions are the agent's only window into available actions; give the model enough tokens to "think" before acting; keep response formats close to naturally occurring text (avoid line-counting, JSON-escaping overhead).

**Why this matters**: when an AI engineer says "agent framework", they're really saying "a particular opinion on how to express the ReAct loop in code." LangGraph encodes it as a stateful graph; CrewAI encodes it as roles; OpenAI's SDK encodes it as a function-calling protocol. They're all ReAct underneath.

**Deep dive further**:
- [**Lilian Weng — LLM Powered Autonomous Agents**](https://lilianweng.github.io/posts/2023-06-23-agent/) — survey-style blog post that's the single best concise overview of the agent components (planning, memory, tool use).
- [**Sparks of Artificial General Intelligence: Early experiments with GPT-4**](https://arxiv.org/abs/2305.14314) (Bubeck et al., Microsoft, 2023) — the "GPT-4 is an AGI" paper; the academic source for many of the agent-capability claims the 2024–2026 vendor docs build on.

### 11.2 RAG — the seminal paper and its descendants

**The seminal paper**: [**Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks**](https://arxiv.org/abs/2005.11401) (Lewis et al., Facebook AI, 2020). The original RAG paper. Concept: a pre-trained seq2seq generator (BART) conditioned on latent documents retrieved from a dense vector index (DPR). The paper's empirical claim: combining a parametric model with a non-parametric memory beats either alone on knowledge-intensive tasks. Every modern RAG system — LangChain RAG, LlamaIndex, Haystack, the cloud-managed Vertex AI RAG Engine — is a descendant of this paper.

**Key conceptual claim**: RAG is the *cheapest* way to give a model access to fresh / proprietary / domain-specific data without fine-tuning. The trade-off is retrieval-quality dependence (garbage in, garbage out). The community has spent 2021–2026 iterating on the retrieval-quality half: better chunking, hybrid retrieval (BM25 + vector), reranking, agentic retrieval, query rewriting, HyDE, GraphRAG.

**GraphRAG**: [**From Local to Global: A Graph RAG Approach to Query-Focused Summarization**](https://arxiv.org/abs/2404.16130) (Edge et al., Microsoft Research, Apr 2024). Microsoft's contribution: when queries are global ("summarize the themes") rather than local ("what does section 3 say"), build an entity-relationship graph over the corpus, run community detection, then generate summaries per community. The trade-off is compute (entity extraction + graph build is expensive) for accuracy on long-corpus, multi-hop questions.

**Why this matters**: in 2026, "naive RAG" (top-k cosine) handles ~70% of production queries; the remaining 30% need either reranking, agentic retrieval, or GraphRAG. Knowing which one to apply to which query class is the entire game.

**Deep dive further**:
- [**Lilian Weng — Agentic RAG**](https://lilianweng.github.io/posts/2024-07-07-agent-rag/) — survey of agentic patterns layered on top of RAG: routing, planning, multi-step retrieval, reflection on retrieval quality.
- OpenAI's [Model Context Protocol (MCP)](https://openai.com/index/introducing-the-model-context-protocol/) — not strictly RAG but the protocol for how agents pull structured context into their prompts; Anthropic and OpenAI both ship MCP clients/servers in 2025–2026.

### 11.3 VLMs — the conceptual arc from CLIP to GPT-4o

**The bridging paper**: [**LLaVA: Visual Instruction Tuning**](https://arxiv.org/abs/2304.08485) (Liu et al., Apr 2023). The conceptual breakthrough that made modern VLMs tractable: connect a CLIP vision encoder to an open LLM via a simple projection layer, then fine-tune on visual instruction-following data synthesized by GPT-4 from COCO captions. The result: a 13B-parameter VLM that matches GPT-4 on visual instruction-following benchmarks at a fraction of the cost.

The LLaVA pattern — *vision encoder + projection + LLM, fine-tuned on GPT-4-synthesized visual instructions* — became the template for every open-source VLM that followed: LLaVA-1.5, MiniGPT-4, InstructBLIP, Qwen-VL, Idefics, Molmo, Pixtral. The closed-source leaders (GPT-4V/GPT-4o, Gemini 2.0, Claude 3.5 Sonnet) trained their vision encoders from scratch alongside the LLM (true native multimodality) rather than bolting on a CLIP — but the LLaVA pattern dominates the open-source ecosystem.

**Why this matters for AI engineering**: any team building a vision-capable agent in 2026 will pick from this
genealogy. The conceptual choice is *open-source bolt-on* (LLaVA pattern, cheap, fine-tunable) vs
*closed-source native* (GPT-4o / Gemini / Claude, expensive, no fine-tuning, best accuracy).

### 11.4 Safety / alignment — the concepts that built guardrails

**Constitutional AI**: [**Constitutional AI: Harmlessness from AI Feedback**](https://arxiv.org/abs/2212.08073) (Bai et al., Anthropic, Dec 2022; [announcement](https://www.anthropic.com/news/constitutional-ai-harmlessness-from-ai-feedback)). Two-stage training: (1) supervised stage where the model critiques and revises its own outputs against a written *constitution* of principles, (2) RLAIF stage where the model generates preference pairs for harmlessness training. The conceptual contribution: most of human-feedback labeling for harmlessness can be replaced by AI feedback against a written ruleset. This makes harmlessness training *scalable* in a way pure RLHF was not.

**RLAIF**: [**RLAIF vs. RLHF: Scaling Reinforcement Learning from Human Feedback with AI Feedback**](https://arxiv.org/abs/2309.00267) (Lee et al., Google, Sep 2023). The empirical follow-up: RLAIF can match RLHF on summarization and helpfulness tasks. The conceptual claim is general: wherever you have a principle and a verifiable evaluation, you can replace human labelers with AI labelers.

**Why this matters for AI engineering**: the guardrails layer in your defense-in-depth stack — output classifiers, content filters, safety monitors — is conceptually downstream of these papers. Your [OpenAI Moderation API](https://platform.openai.com/docs/guides/moderation) is RLAIF in production. Your [Azure Prompt Shields](https://learn.microsoft.com/en-us/azure/ai-services/content-safety/concepts/jailbreak-detection) are constitutional-AI-style principle-matching against known jailbreak patterns. **The guardrails layer in 2026 is essentially "Constitutional AI as a service."**

### 11.5 The LLM-Wiki pattern — the theoretical framing

**Evergreen notes as a concept**: Andy Matuschak's [Evergreen Notes Should be Concept-Oriented and Densely-Linked](https://notes.andymatuschak.org/Evergreens_notes). The theoretical foundation: notes that are *concept-oriented* (one concept per note) and *densely-linked* (every note has many `[[wikilinks]]` to others) form a thinking tool, not just a memory. The concepts that emerge from the link graph are themselves discoveries.

**Digital gardens**: Maggie Appleton's [A Brief History & Ethos of the Digital Garden](https://maggieappleton.com/garden-history). The visual / structural lineage from hand-annotated books → Zettelkasten → blogs → wikis → **digital gardens** → LLM-Wikis. The LLM-Wiki is the digital garden with an LLM at the center: the LLM helps you plant, prune, and find the cross-links that make the garden *useful* rather than just *growing*.

**Karpathy on LLMs as a knowledge tool**: see [karpathy.ai](https://karpathy.ai/) (his personal notes — the original "LLM-Wiki" pattern in the wild). The framing: your LLM-Wiki is *the* knowledge substrate an AI-engineering team uses — for decision logs, eval results, prompt versions, incident writeups. The whole toolchain (LangChain / LangGraph / LlamaIndex / Haystack) exists to *populate and query* this substrate.

**Why this matters**: LLM-Wiki is not a personal-knowledge-management fad. It is the canonical substrate for AI-engineering teams in 2026. The `obsidian-organize` plugin (v0.5.0) formalizes it: `research` stages raw material, `add_wiki` promotes to Karpathy-style leaf notes, `process_clippings` distills raw `Clippings/`, hierarchical mode auto-splits multi-section research into per-section leaves + auto-generated `_index.md` hubs.

### 11.6 OpenAI / Anthropic blog posts worth reading end-to-end

These four are the conceptual backbone for an AI engineer in 2026:

1. [**Anthropic: Building Effective Agents**](https://www.anthropic.com/engineering/building-effective-agents) (Dec 2024). The workflows-vs-agents taxonomy. The six patterns. The "ACI" concept (invest as much in agent-computer interfaces as in human-computer interfaces). Read first.
2. [**OpenAI: Function-calling design notes**](https://openai.com/index/functions-and-their-llms-thoughts/) (Aug 2024). The function-calling protocol as the foundation for agents. The principle that tool descriptions are the agent's only window into its world.
3. [**Anthropic: Building effective agents with Skill ARC (progressive disclosure)**](https://www.anthropic.com/engineering/building-effective-agents-with-skill-arc-progressive-disclosure). The pattern of *progressive disclosure* — the agent sees only the tools it needs at each step, not the full library. Critical for token-economy.
4. [**Anthropic: Claude thinks tool**](https://www.anthropic.com/engineering/claude-think-tool). The pattern of explicitly invoking a *think* tool mid-conversation to force structured reasoning before tool use. A direct descendant of ReAct, but tool-mediated.

Plus, for the AI security layer:
- [**Anthropic: Claude computer use beta**](https://www.anthropic.com/news/claude-3-5-sonnet-computer-use) (Oct 2024). The conceptual breakthrough: an LLM that *sees* a screen and *clicks*. Foundational to OSWorld benchmarks, to the OWASP LLM03 Excessive Agency threat, and to Strix-style pentest tooling.

### 11.7 Putting it together — the conceptual stack

If you internalize the four paper classes (ReAct / RAG / LLaVA / Constitutional AI) plus the four blog posts (Anthropic agents / OpenAI function-calling / Anthropic skill-ARC / Anthropic computer-use), you have the conceptual scaffolding to:

- *Understand* any new agent framework in minutes (it's a ReAct loop, one of six patterns, in some packaging)
- *Evaluate* any new RAG claim (is it naive / GraphRAG / agentic? what's the retrieval-quality bet?)
- *Pick* a VLM for a new product (open-source bolt-on vs closed-source native, trade-offs as above)
- *Understand* why guardrails exist (Constitutional AI / RLAIF as a service)
- *Apply* the LLM-Wiki pattern (evergreen notes + digital garden + LLM-at-the-center)

That is the goal of this section. The next person to onboard onto the AI-engineering team should read this section end-to-end on day one.

## Layout-fix note

Frontmatter `promoted_to:` updated 2026-09-10 to reflect the wiki move from `wiki/ai-agent-wiki/<topic>/` to `wiki/ai-agent-wiki/knowledge/<topic>/`. The original leaf notes (and hubs) themselves are still valid; only the staged file's `promoted_to:` pointer needed an update.
