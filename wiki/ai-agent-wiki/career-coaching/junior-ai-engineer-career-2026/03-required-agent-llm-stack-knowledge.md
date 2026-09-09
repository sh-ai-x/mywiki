---
topic: junior-ai-engineer-career-2026/03
tags: ["career", "job-hunting", "junior", "ai-engineer", "agent", "llm", "rag", "stack", "interview-prep", "global-first"]
related: ["ai-agent-wiki/career-coaching/junior-ai-engineer-career-2026/02-required-ml-dl-foundations", "ai-agent-wiki/ai-engineering-tooling/_index", "ai-agent-wiki/agent-engineering/_index"]
source: "_research/junior-ai-engineer-career-2026.md#3"
created: 2026-09-10
priority: critical
job-hunting: true
global-first-filter: applied
---

# 3. Required agent/LLM stack knowledge

The 2026 AI-engineer interview loop has converged on a small set of tools and concepts. The list below is the consensus.

### 3.1 RAG — three patterns you must distinguish

| Pattern | When to use | Latency | Cost |
|---|---|---|---|
| **Naive RAG** | Top-k cosine over chunked docs; first 80% of prod traffic | 100–500 ms | Low |
| **Agentic RAG** | Agent decides when to retrieve; can loop / reflect | 1–10 s (multi-step) | Higher |
| **GraphRAG** (Microsoft) | Multi-hop queries over >10k docs; "summarize the themes" | 2–10× vector RAG | Expensive (entity extraction pass) |

Three interview traps:
1. *"We tried RAG and the answers are bad."* → 90% of the time the bug is *retrieval quality*, not generation quality. Fix: better chunking, hybrid retrieval (BM25 + vector), reranking (Cohere Rerank, BGE-reranker).
2. *"How do you know it's working?"* → you don't, unless you have an eval set with ground-truth answers. RAGAS is the canonical framework (https://docs.ragas.io/, accessed 2026-09-10).
3. *"Do we need GraphRAG?"* → almost always no, unless the queries are genuinely global. The Microsoft GraphRAG paper itself frames it as a long-corpus-summarization tool.

### 3.2 Tool-use protocols (MCP, function-calling)

- **Function-calling** (OpenAI 2024): the model emits structured args to pre-defined tool schemas; SDK converts to JSON; tools run; results re-enter the prompt. The OpenAI Agents SDK is built on this protocol.
- **MCP (Model Context Protocol)** (Anthropic, late 2024): a JSON-RPC-based standard for connecting an LLM to *external* tools and data sources. The model receives MCP-server-published tool schemas via a client; clients and servers are decoupled. Both Anthropic and OpenAI ship MCP clients as of 2025.
- Interview answer for "what is MCP?": *"A wire protocol that standardizes how agents discover and call external tools, so any MCP server can plug into any MCP-client LLM runtime — the HTTP of agent tooling."*

### 3.3 LangGraph vs. CrewAI vs. OpenAI Agents SDK

The 2026 split (per the `_research/ai-llm-vlm-tooling.md` §11 conceptual framework + the curated `ai-engineering-tooling/` job-hunting sub-hub):

| Framework | Mental model | Best for |
|---|---|---|
| **LangGraph** | Stateful graph; nodes are LLM calls / tools; edges are conditional; persistent checkpointer | Stateful agents with cycles, human-in-loop, retries |
| **CrewAI** | Role-based multi-agent; each "agent" has a role/backstory/tools; "tasks" are delegated | Simulating a small team; research-style workflows |
| **OpenAI Agents SDK** | Minimal; function-calling as first-class; built on the OpenAI Agents runtime | OpenAI-only stacks; small surfaces; rapid prototyping |

Default 2026 answer at most companies: **LangGraph** for stateful production; **OpenAI Agents SDK** for prototyping; **CrewAI** only when asked to do role-based multi-agent specifically.

### 3.4 Observability (LangSmith, Phoenix, Helicone)

- **LangSmith** — first-party LangChain ecosystem; tracing + eval + prompt management; works with LangChain / LangGraph / anything that calls an LLM API (you just configure HTTP transport).
- **Arize Phoenix** — open-source eval-focused; tied to the OpenTelemetry standard; popular with non-LangChain stacks.
- **Helicone** — vendor-neutral LLM gateway; logs every request transparently between your app and the provider; BYOK-friendly.

Interview answer for "which observability tool?": *"Pick once at company inception; migrate costs more than alternatives cost. LangSmith if you're in LangChain; Helicone if you want a transparent proxy; Phoenix if you want OSS and OpenTelemetry."*

### 3.5 Evaluation (RAGAS, DeepEval, promptfoo)

The 2026 evaluation landscape sorted itself into three tools (Source: https://aiml.qa/llm-evaluation-framework-benchmark-2026/, https://genai.qa/blog/promptfoo-vs-deepeval-vs-ragas/ — accessed 2026-09-10):

| Tool | Core specialty | Strength |
|---|---|---|
| **RAGAS** | RAG-specific metrics (faithfulness, answer relevance, context precision/recall, answer correctness) | The only tool that ships LLM-judged RAG metrics out of the box |
| **DeepEval** | Pytest-like Python-native eval; CI integration | CI/CD gates; broadest metric library (~50+ metrics) |
| **promptfoo** | CLI-first; prompt A/B; red-team / adversarial testing | Security evals; multi-model prompt comparison |

Junior-AI-engineer interview answer: *"Use RAGAS to measure retrieval quality (context recall/precision), DeepEval for CI-integrated regression gates, promptfoo for security red-team. All three are open-source."*

### 3.6 Foundation-model conceptual papers

From `_research/ai-llm-vlm-tooling.md` §11 (already curated), four paper classes and four blog posts are the interview baseline:

- **ReAct** (Yao et al., 2022, https://arxiv.org/abs/2210.03629) — the agent loop.
- **RAG** (Lewis et al., 2020, https://arxiv.org/abs/2005.11401) — parametric + non-parametric memory.
- **LLaVA** (Liu et al., 2023, https://arxiv.org/abs/2304.08485) — vision encoder + projection + LLM.
- **Constitutional AI** (Bai et al., 2022, https://arxiv.org/abs/2212.08073) — guardrails as a service.
- **Anthropic: Building Effective Agents** (Dec 2024, https://www.anthropic.com/engineering/building-effective-agents) — workflows vs. agents; six patterns.
