---
tags: ["ai-engineering", "ai-agent", "rag", "vlm", "safety", "papers", "interview-prep"]
priority: high
related: ["ai-agent-wiki/ai-engineering-tooling/ai-llm-vlm-tooling/_index", "ai-agent-wiki/ai-engineering-tooling/_index", "ai-agent-wiki/00-index"]
created: 2026-09-09
source: "_research/ai-llm-vlm-tooling.md#11"
job-hunting: true
---

# Concept deep-dive — papers, blog posts, primary sources

> Promoted from `[[_research/ai-llm-vlm-tooling.md]]` §11. The earlier sections cataloged *what* the 2026 AI-engineering tooling landscape contains. This note is the conceptual anchor — papers that introduced each pattern, plus the OpenAI / Anthropic engineering blogs that operationalized them. Read end-to-end on day one of any AI-engineering interview prep.

## 11.1 Agents — the conceptual foundation

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

The blog's most-quoted advice: *start simple, add complexity only when it demonstrably improves outcomes.* A 200-line script using the Anthropic SDK often beats a framework-heavy implementation.

**OpenAI's framing**: [**Function-calling design notes**](https://openai.com/index/functions-and-their-llms-thoughts/) (OpenAI, Aug 2024). The function-calling API is the foundation OpenAI Agents SDK sits on. Key concepts: tool descriptions are the agent's only window into available actions; give the model enough tokens to "think" before acting; keep response formats close to naturally occurring text (avoid line-counting, JSON-escaping overhead).

**Why this matters**: when an AI engineer says "agent framework", they're really saying "a particular opinion on how to express the ReAct loop in code." LangGraph encodes it as a stateful graph; CrewAI encodes it as roles; OpenAI's SDK encodes it as a function-calling protocol. They're all ReAct underneath.

**Deep dive further**:

- [**Lilian Weng — LLM Powered Autonomous Agents**](https://lilianweng.github.io/posts/2023-06-23-agent/) — survey-style blog post that's the single best concise overview of the agent components (planning, memory, tool use).
- [**Sparks of Artificial General Intelligence: Early experiments with GPT-4**](https://arxiv.org/abs/2305.14314) (Bubeck et al., Microsoft, 2023) — the "GPT-4 is an AGI" paper; the academic source for many of the agent-capability claims the 2024–2026 vendor docs build on.

## 11.2 RAG — the seminal paper and its descendants

**The seminal paper**: [**Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks**](https://arxiv.org/abs/2005.11401) (Lewis et al., Facebook AI, 2020). The original RAG paper. Concept: a pre-trained seq2seq generator (BART) conditioned on latent documents retrieved from a dense vector index (DPR). The paper's empirical claim: combining a parametric model with a non-parametric memory beats either alone on knowledge-intensive tasks. Every modern RAG system — LangChain RAG, LlamaIndex, Haystack, the cloud-managed Vertex AI RAG Engine — is a descendant of this paper.

**Key conceptual claim**: RAG is the *cheapest* way to give a model access to fresh / proprietary / domain-specific data without fine-tuning. The trade-off is retrieval-quality dependence (garbage in, garbage out). The community has spent 2021–2026 iterating on the retrieval-quality half: better chunking, hybrid retrieval (BM25 + vector), reranking, agentic retrieval, query rewriting, HyDE, GraphRAG.

**GraphRAG**: [**From Local to Global: A Graph RAG Approach to Query-Focused Summarization**](https://arxiv.org/abs/2404.16130) (Edge et al., Microsoft Research, Apr 2024). Microsoft's contribution: when queries are global ("summarize the themes") rather than local ("what does section 3 say"), build an entity-relationship graph over the corpus, run community detection, then generate summaries per community. The trade-off is compute (entity extraction + graph build is expensive) for accuracy on long-corpus, multi-hop questions.

**Why this matters**: in 2026, "naive RAG" (top-k cosine) handles ~70% of production queries; the remaining 30% need either reranking, agentic retrieval, or GraphRAG. Knowing which one to apply to which query class is the entire game.

**Deep dive further**:

- [**Lilian Weng — Agentic RAG**](https://lilianweng.github.io/posts/2024-07-07-agent-rag/) — survey of agentic patterns layered on top of RAG: routing, planning, multi-step retrieval, reflection on retrieval quality.
- OpenAI's [Model Context Protocol (MCP)](https://openai.com/index/introducing-the-model-context-protocol/) — not strictly RAG but the protocol for how agents pull structured context into their prompts; Anthropic and OpenAI both ship MCP clients/servers in 2025–2026.

## 11.3 VLMs — the conceptual arc from CLIP to GPT-4o

**The bridging paper**: [**LLaVA: Visual Instruction Tuning**](https://arxiv.org/abs/2304.08485) (Liu et al., Apr 2023). The conceptual breakthrough that made modern VLMs tractable: connect a CLIP vision encoder to an open LLM via a simple projection layer, then fine-tune on visual instruction-following data synthesized by GPT-4 from COCO captions. The result: a 13B-parameter VLM that matches GPT-4 on visual instruction-following benchmarks at a fraction of the cost.

The LLaVA pattern — *vision encoder + projection + LLM, fine-tuned on GPT-4-synthesized visual instructions* — became the template for every open-source VLM that followed: LLaVA-1.5, MiniGPT-4, InstructBLIP, Qwen-VL, Idefics, Molmo, Pixtral. The closed-source leaders (GPT-4V/GPT-4o, Gemini 2.0, Claude 3.5 Sonnet) trained their vision encoders from scratch alongside the LLM (true native multimodality) rather than bolting on a CLIP — but the LLaVA pattern dominates the open-source ecosystem.

**Why this matters for AI engineering**: any team building a vision-capable agent in 2026 will pick from this genealogy. The conceptual choice is *open-source bolt-on* (LLaVA pattern, cheap, fine-tunable) vs *closed-source native* (GPT-4o / Gemini / Claude, expensive, no fine-tuning, best accuracy).

## 11.4 Safety / alignment — the concepts that built guardrails

**Constitutional AI**: [**Constitutional AI: Harmlessness from AI Feedback**](https://arxiv.org/abs/2212.08073) (Bai et al., Anthropic, Dec 2022; [announcement](https://www.anthropic.com/news/constitutional-ai-harmlessness-from-ai-feedback)). Two-stage training: (1) supervised stage where the model critiques and revises its own outputs against a written *constitution* of principles, (2) RLAIF stage where the model generates preference pairs for harmlessness training. The conceptual contribution: most of human-feedback labeling for harmlessness can be replaced by AI feedback against a written ruleset. This makes harmlessness training *scalable* in a way pure RLHF was not.

**RLAIF**: [**RLAIF vs. RLHF: Scaling Reinforcement Learning from Human Feedback with AI Feedback**](https://arxiv.org/abs/2309.00267) (Lee et al., Google, Sep 2023). The empirical follow-up: RLAIF can match RLHF on summarization and helpfulness tasks. The conceptual claim is general: wherever you have a principle and a verifiable evaluation, you can replace human labelers with AI labelers.

**Why this matters for AI engineering**: the guardrails layer in your defense-in-depth stack — output classifiers, content filters, safety monitors — is conceptually downstream of these papers. Your [OpenAI Moderation API](https://platform.openai.com/docs/guides/moderation) is RLAIF in production. Your [Azure Prompt Shields](https://learn.microsoft.com/en-us/azure/ai-services/content-safety/concepts/jailbreak-detection) are constitutional-AI-style principle-matching against known jailbreak patterns. **The guardrails layer in 2026 is essentially "Constitutional AI as a service."**

## 11.5 The LLM-Wiki pattern — the theoretical framing

**Evergreen notes as a concept**: Andy Matuschak's [Evergreen Notes Should be Concept-Oriented and Densely-Linked](https://notes.andymatuschak.org/Evergreens_notes). The theoretical foundation: notes that are *concept-oriented* (one concept per note) and *densely-linked* (every note has many `[[wikilinks]]` to others) form a thinking tool, not just a memory. The concepts that emerge from the link graph are themselves discoveries.

**Digital gardens**: Maggie Appleton's [A Brief History & Ethos of the Digital Garden](https://maggieappleton.com/garden-history). The visual / structural lineage from hand-annotated books → Zettelkasten → blogs → wikis → **digital gardens** → LLM-Wikis. The LLM-Wiki is the digital garden with an LLM at the center: the LLM helps you plant, prune, and find the cross-links that make the garden *useful* rather than just *growing*.

**Karpathy on LLMs as a knowledge tool**: see [karpathy.ai](https://karpathy.ai/) (his personal notes — the original "LLM-Wiki" pattern in the wild). The framing: your LLM-Wiki is *the* knowledge substrate an AI-engineering team uses — for decision logs, eval results, prompt versions, incident writeups. The whole toolchain (LangChain / LangGraph / LlamaIndex / Haystack) exists to *populate and query* this substrate.

**Why this matters**: LLM-Wiki is not a personal-knowledge-management fad. It is the canonical substrate for AI-engineering teams in 2026. The `obsidian-organize` plugin (v0.5.0) formalizes it: `research` stages raw material, `add_wiki` promotes to Karpathy-style leaf notes, `process_clippings` distills raw `Clippings/`, hierarchical mode auto-splits multi-section research into per-section leaves + auto-generated `_index.md` hubs.

> Note: this section (11.5) is **archived** for the job-hunting filter — but the references remain the canonical PKM/PKM-foundation reading list. See `_archive/ai-llm-vlm-tooling-llm-wiki.md` and `_archive/llm-wiki-pattern-deep-dive-appended-2026-09-09.md`.

## 11.6 OpenAI / Anthropic blog posts worth reading end-to-end

These four are the conceptual backbone for an AI engineer in 2026:

1. [**Anthropic: Building Effective Agents**](https://www.anthropic.com/engineering/building-effective-agents) (Dec 2024). The workflows-vs-agents taxonomy. The six patterns. The "ACI" concept (invest as much in agent-computer interfaces as in human-computer interfaces). Read first.
2. [**OpenAI: Function-calling design notes**](https://openai.com/index/functions-and-their-llms-thoughts/) (Aug 2024). The function-calling protocol as the foundation for agents. The principle that tool descriptions are the agent's only window into its world.
3. [**Anthropic: Building effective agents with Skill ARC (progressive disclosure)**](https://www.anthropic.com/engineering/building-effective-agents-with-skill-arc-progressive-disclosure). The pattern of *progressive disclosure* — the agent sees only the tools it needs at each step, not the full library. Critical for token-economy.
4. [**Anthropic: Claude thinks tool**](https://www.anthropic.com/engineering/claude-think-tool). The pattern of explicitly invoking a *think* tool mid-conversation to force structured reasoning before tool use. A direct descendant of ReAct, but tool-mediated.

Plus, for the AI security layer:

- [**Anthropic: Claude computer use beta**](https://www.anthropic.com/news/claude-3-5-sonnet-computer-use) (Oct 2024). The conceptual breakthrough: an LLM that *sees* a screen and *clicks*. Foundational to OSWorld benchmarks, to the OWASP LLM03 Excessive Agency threat, and to Strix-style pentest tooling.

## 11.7 Putting it together — the conceptual stack

If you internalize the four paper classes (ReAct / RAG / LLaVA / Constitutional AI) plus the four blog posts (Anthropic agents / OpenAI function-calling / Anthropic skill-ARC / Anthropic computer-use), you have the conceptual scaffolding to:

- *Understand* any new agent framework in minutes (it's a ReAct loop, one of six patterns, in some packaging)
- *Evaluate* any new RAG claim (is it naive / GraphRAG / agentic? what's the retrieval-quality bet?)
- *Pick* a VLM for a new product (open-source bolt-on vs closed-source native, trade-offs as above)
- *Understand* why guardrails exist (Constitutional AI / RLAIF as a service)
- *Apply* the LLM-Wiki pattern (evergreen notes + digital garden + LLM-at-the-center)

That is the goal of this section. The next person to onboard onto the AI-engineering team should read this section end-to-end on day one.

## Related

- [[ai-llm-vlm-tooling/_index|ai-llm-vlm-tooling sub-hub]] — all ai-llm-vlm-tooling leaf notes
- [[the-2026-agent-framework-landscape-is-consolidating-around-t|Agent framework landscape]] — §11.1 applied
- [[rag-retrieval-augmented-generation-the-rag-in-the-topic|RAG]] — §11.2 applied
- [[vision-language-models-vlm-the-vlm-in-the-topic|VLM]] — §11.3 applied
- [[ai-agent-wiki/core-ai-security/_index|core-ai-security]] — §11.4 guardrails applied
- [[knowledge/ai-engineering-tooling/_index|ai-engineering-tooling hub]] — top-level hub
- [[ai-agent-wiki/00-index|AI Agent Wiki Index]] — master catalog

## Source

- Original §11 of [[_research/ai-llm-vlm-tooling.md]] — staged research dossier.
