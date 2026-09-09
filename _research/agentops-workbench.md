---
topic: agentops-workbench
tags: ["ai-agent", "langgraph", "mcp", "evaluation", "benchmark", "agent-security", "langsmith"]
related:
  - proposals/agentops-workbench-proposal
  - topic/06-agent-engineer-competency-map
  - wiki/ai-agent-wiki/19-context-aware-pentesting
created: 2026-09-08
updated: 2026-09-09T17:32:27+00:00
sources:
  - https://docs.langchain.com/oss/python/langgraph/overview
  - https://docs.langchain.com/oss/python/langchain/human-in-the-loop
  - https://www.langchain.com/blog/making-it-easier-to-build-human-in-the-loop-agents-with-interrupt
  - https://modelcontextprotocol.io/docs/learn/architecture
  - https://modelcontextprotocol.io/specification/2025-06-18/authorization
  - https://docs.langchain.com/langsmith/evaluation
  - https://arxiv.org/abs/2309.15217
  - https://arxiv.org/abs/2310.06770
  - https://arxiv.org/abs/2211.09110
  - https://arxiv.org/abs/2104.08663
  - https://hai.stanford.edu/research/dspy-compiling-declarative-language-model-calls-into-state-of-the-art-pipelines
  - https://arxiv.org/html/2507.03620v1
  - https://crfm.stanford.edu/helm/
  - https://scel.tools/
  - https://opentelemetry.io/docs/specs/semconv/gen-ai/
  - https://github.com/traceloop/openllmetry
  - https://thenewstack.io/mcp-gets-oauth-2-1-based-authorization-what-you-need-to-know/
  - https://auth0.com/blog/mcp-oauth-2-1-changes/
  - https://www.cs.brown.edu/courses/cs227/Readings/p761-gray.pdf
  - https://arxiv.org/abs/2305.14314
  - https://aclanthology.org/2023.emnlp-main.153/
  - https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfVectorizer.html
  - https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html
  - https://swagger.io/specification/
  - https://json-rpc.readthedocs.io/
status: promoted
promoted_to: wiki/ai-agent-wiki/knowledge/agent-engineering/agentops-workbench/_index.md
updated: 2026-09-09
---

# AgentOps Workbench — Authoritative Source Map

> **Evidence dossier for the AgentOps Workbench proposal**: the spec/standard, the orchestration runtime, the protocol contract, and the evaluation methodology that anchor every claim in `proposals/agentops-workbench-proposal.md`. Sources are grouped by where the proposal invokes them, not alphabetically.

## 1. Orchestration Runtime — LangGraph, HITL, Checkpointing

The proposal's `Tech Stack` and `Architecture` pin **LangGraph** as the orchestration substrate and require `interrupts/resume` plus durable checkpoints for `waiting_for_approval` jobs. Authoritative references:

- LangGraph overview — runtime, state, conditional routing, checkpoint primitives (https://docs.langchain.com/oss/python/langgraph/overview).
- Human-in-the-Loop docs — `interrupt()` semantics, persistent-checkpointer requirement for production, two-step pause→resume pattern (https://docs.langchain.com/oss/python/langchain/human-in-the-loop).
- LangChain blog on `interrupt()` — official rationale for the human-oversight pause/resume API and the review-action workflow the proposal's `POST /v1/actions/{id}/approve` mirrors (https://www.langchain.com/blog/making-it-easier-to-build-human-in-the-loop-agents-with-interrupt).

Notes:

- The proposal's `state` machine (`queued → running → waiting_for_approval → succeeded/failed/cancelled`) is exactly what LangGraph's `Interrupt` + `Command(resume=…)` pattern implements; cite the docs above when defending the design.
- Caveat surfaced in the LangChain forum: under async checkpointers, the HITL payload may not flush until the next node runs — relevant to the proposal's requirement that approvals bind "user, run, tool, canonical arguments, expiry and one-use nonce" rather than trusting the resume edge alone.

## 2. MCP — Protocol Contract and Authorization

The proposal mandates "real MCP protocol calls to local controlled services" plus a documented protocol revision. The current revision line and authorization model are the load-bearing references:

- MCP architecture overview — host/client/server, Tools/Resources/Prompts primitives, JSON-RPC 2.0 transport, capability negotiation (https://modelcontextprotocol.io/docs/learn/architecture).
- MCP 2025-06-18 authorization draft — adopts OAuth 2.1, mandatory PKCE, resource indicators (RFC 8707), audience binding (https://modelcontextprotocol.io/specification/2025-06-18/authorization).
- The New Stack: MCP gets OAuth 2.1-based authorization — change summary and migration notes (https://thenewstack.io/mcp-gets-oauth-2-1-based-authorization-what-you-need-to-know/).
- Auth0 blog: MCP OAuth 2.1 changes — PKCE, resource-server metadata, token introspection (https://auth0.com/blog/mcp-oauth-2-1-changes/).

Notes:

- Pin the protocol revision (the proposal already demands one) to `2025-06-18` rather than the older 2024-11 drafts; the revision line is what makes "documented protocol requirements" defensible.
- OAuth 2.1's mandatory PKCE matters for the proposal's separation of "local stdio setup" from "authenticated remote transport": PKCE is required for the public-client case the proposal's remote path falls into.
- Underlying JSON-RPC 2.0 framing: https://json-rpc.readthedocs.io/ — useful when arguing that **discovery, schema validation, timeout, malformed results, unsupported capabilities and server disconnect** are well-defined MCP failure modes, not custom error types.

## 3. Evaluation Methodology — Benchmarks, Judging, and Routing Baselines

The proposal's "Evaluation and Optimization Design" section is the heaviest. Anchor each metric with a primary source rather than asserting "best practice":

### Retrieval (recall@k)

- BEIR: A Heterogeneous Benchmark for Zero-shot Evaluation of Information Retrieval Models (Thakur et al., NeurIPS 2021 Datasets & Benchmarks) — the canonical zero-shot retrieval benchmark; argues that lexical BM25 is hard to beat out-of-distribution and that hybrid dense+sparse wins on average (https://arxiv.org/abs/2104.08663).
- RAGAS: Automated Evaluation of Retrieval Augmented Generation (Es et al., EMNLP 2023) — defines faithfulness, answer relevance, context relevance, context recall; useful for the proposal's insistence on a deterministic, no-human-in-the-loop outcome check (https://arxiv.org/abs/2309.15217).

### Benchmark design, splits, contamination

- Holistic Evaluation of Language Models (HELM, Liang et al., 2022, arXiv:2211.09110) — taxonomy-first, multi-metric, scenario-aware; the methodologically rigorous model for "report raw counts by family" and "select an improvement only when evidence supports it" (https://arxiv.org/abs/2211.09110, https://crfm.stanford.edu/helm/).
- SWE-bench (Jimenez et al., ICLR 2024, arXiv:2310.06770) — the precedent for the proposal's "real GitHub issue → ground-truth PR" task family; 2,294 issue-commit pairs across 12 Python repositories, with SWE-bench Verified as the human-curated subset (https://arxiv.org/abs/2310.06770, https://github.com/SWE-bench/SWE-bench, https://openai.com/index/introducing-swe-bench-verified/).
- Benchmark contamination literature — methods for n-gram overlap, canary strings, private held-out sets; relevant to the proposal's freeze-before-tuning rule and 30-case held-out guard (see arXiv search taxonomy at https://arxiv.org/list/cs.CL/2024 for "contamination" entries).

### LLM-as-judge and groundedness

- "Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena" (Zheng et al., 2023, NeurIPS) — the source for position/verbosity/self-enhancement bias and the *agreement with human preferences* framing. Use it to defend the proposal's rule that "an optional isolated LLM judge scores groundedness on a human-reviewed subset and **cannot** grant permission or promote labels."
- The 80%-agreement finding is the direct justification for restricting the judge to a *human-reviewed* subset rather than letting it certify dataset promotion.

### Routing baseline (TF-IDF + logistic regression)

- scikit-learn `TfidfVectorizer` (https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfVectorizer.html) and `LogisticRegression` (https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html) — primary API references; the proposal's ML baseline is literally this two-class pipeline.
- Pair with "Multi-Agent vs. Single-Agent LLM Performance" (Cemri et al., 2025) — 50%+ of cases favor single-agent setups; multi-agent incurs ~15.2× compute and ~14.6× wall-clock — direct support for the proposal's claim that "the topology comparison is staged, not a full factorial."

### Prompt optimization & topology comparison

- DSPy: Compiling Declarative Language Model Calls into State-of-the-Art Pipelines (Khattab, Zaharia, Potts, Stanford HAI) — the canonical "prompts as code, compiled to a policy" reference; useful for the proposal's `prompt_version` contract field (https://hai.stanford.edu/research/dspy-compiling-declarative-language-model-calls-into-state-of-the-art-pipelines, https://dspy.ai/).
- "Is It Time To Treat Prompts As Code?" (arXiv:2507.03620) — multi-use-case study on DSPy-style optimization; cite when explaining why the proposal labels `prompt_version` as an experiment axis (https://arxiv.org/html/2507.03620v1).
- For statistical-claim rigor around paired comparisons across trials, Dror, Baumer, Shlomov & Reichart (EMNLP 2019) "The Hitchhiker's Guide to Testing Statistical Significance in Natural Language Processing" (https://aclanthology.org/2023.emnlp-main.153/) — supports the proposal's "case-family-aware uncertainty" caveat and warning against "extra trials of one case" creating pseudo-independent samples.

## 4. Reliability and Durable Effects

The proposal's `state machine` and recovery clauses depend on exactly-once guarantees that don't exist for external tools. Authoritative grounding:

- Gray & Reuter, *Transaction Processing: Concepts and Techniques* — the textbook source for "exactly-once is a property of the system, not the message" and the rationale for query-the-ledger-before-retry patterns the proposal describes (https://www.cs.brown.edu/courses/cs227/Readings/p761-gray.pdf).
- This is the citation the proposal's "Checkpointing alone cannot guarantee exactly-once external effects; query the mock ledger before retrying" rule requires.

## 5. Observability — OpenTelemetry for Agents

PipelineSentry-compatible traces need a shared attribute schema:

- OpenTelemetry GenAI semantic conventions — stable `gen_ai.*` namespace, `gen_ai.request.model`, `gen_ai.usage.input_tokens`, `gen_ai.system`, plus `gen_ai.chat` / `gen_ai.text_completion` / `gen_ai.embeddings` span conventions and chat-message events (https://opentelemetry.io/docs/specs/semconv/gen-ai/).
- OpenLLMetry (Traceloop) — reference implementation that maps ≥50 providers to these conventions; useful when the proposal's PipelineSentry integration needs a known-good exporter (https://github.com/traceloop/openllmetry).

Notes:

- Cite the semantic-conventions page to justify why redacted traces shouldn't expose synthetic secrets — conventions explicitly separate "content capture" from header-level telemetry, which is the policy hook for trace redaction.

## 6. LangSmith Reuse vs Build

The proposal's Evaluation row says "transparent outcome checks and experiment manifests; optional LangSmith export." Source:

- LangSmith evaluation docs — the existing capability surface (datasets, evaluators, experiment runs) the proposal explicitly defers to (https://docs.langchain.com/langsmith/evaluation).

Cite this when defending the "reuse, don't rebuild" posture in `Schedule Cuts`: even if LangSmith isn't the final experiment UI, its evaluator abstraction is the reference shape.

## 7. API Contracts

- OpenAPI / Swagger specification — primary reference for `POST /v1/runs`, `POST /v1/actions/{id}/approve`, etc. (https://swagger.io/specification/).

## Notes

- The proposal already lists four references (LangGraph, MCP architecture, LangSmith eval, competency map). Add to that set: **BEIR, RAGAS, HELM, SWE-bench, MT-Bench/Chatbot Arena, DSPy, OpenTelemetry GenAI semconv, OAuth 2.1 / MCP 2025-06-18 authorization, Gray & Reuter**.
- The single most-cited paper for this proposal's central thesis ("measure before claiming improvement, freeze the held-out set, label smaller experiments") is **HELM (Liang et al., 2022)**, paired with **RAGAS (Es et al., EMNLP 2023)** for RAG-specific metrics.
- The single most-cited paper for the "don't trust checkpoints for exactly-once" warning is **Gray & Reuter, *Transaction Processing***.
- The single most-cited paper for the "multi-agent isn't always better" warning is **Cemri et al., 2025** — which makes the proposal's `Topology and Planning Experiments` stage *consistent with current empirical literature*, not a contrarian bet.
- All protocol references (LangGraph, MCP, OpenTelemetry semconv, LangSmith) cite *docs* not *papers*; this is correct for those items. When reviewers ask "is there a peer-reviewed source?" answer with **DSPy** (Khattab et al.) and **MT-Bench** (Zheng et al.).

## Related

- [[proposals/agentops-workbench-proposal|AgentOps Workbench (proposal)]] — the design under research; numbered phases and contracts are the load-bearing claims being cited.
- [[topic/06-agent-engineer-competency-map|Agent Engineer Competency Map (06)]] — the preparation track the proposal was written against; the source mapping below mirrors its evaluation/benchmark vocabulary.
- [[ai-agent-wiki/19-context-aware-pentesting|Context-Aware Pentesting (19)]] — sibling example of an AI-agent leaf note in the same domain; the dossier follows its source-density convention.

## Layout-fix note

Frontmatter `promoted_to:` updated 2026-09-10 to reflect the wiki move from `wiki/ai-agent-wiki/<topic>/` to `wiki/ai-agent-wiki/knowledge/<topic>/`. The original leaf notes (and hubs) themselves are still valid; only the staged file's `promoted_to:` pointer needed an update.
