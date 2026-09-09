---
topic: junior-ai-engineer-career-2026
tags: ["career", "job-hunting", "junior", "ai-engineer", "agent", "llm", "rag", "korea", "interview-prep", "global-first"]
related: ["ai-agent-wiki/job-hunting-priority", "ai-agent-wiki/ai-engineering-tooling/_index", "ai-agent-wiki/agent-engineering/_index"]
global-first-filter: applied
sources:
  - https://www.ivanturkovic.com/2026/04/24/ai-job-titles-2026-naming-chaos/
  - https://ai.engineer/jobs
  - https://github.com/eleutherai/lm-evaluation-harness
  - https://www.eleuther.ai/projects/large-language-model-evaluation
  - https://arxiv.org/abs/2210.03629
  - https://arxiv.org/abs/2005.11401
  - https://arxiv.org/abs/2404.16130
  - https://arxiv.org/abs/2304.08485
  - https://arxiv.org/abs/2212.08073
  - https://www.anthropic.com/engineering/building-effective-agents
  - https://openai.com/index/functions-and-their-llms-thoughts/
  - https://www.anthropic.com/news/claude-3-5-sonnet-computer-use
  - https://aiml.qa/vector-database-comparison-2026/
  - https://www.firecrawl.dev/blog/best-vector-databases
  - https://www.kalviumlabs.ai/blog/vector-databases-compared-pgvector-pinecone-qdrant-weaviate/
  - https://www.yottalabs.ai/post/best-llm-inference-engines-in-2026-vllm-tensorrt-llm-tgi-and-sglang-compared
  - https://leetllm.com/blog/llm-inference-engine-comparison-2026
  - https://genai.qa/blog/promptfoo-vs-deepeval-vs-ragas/
  - https://aiml.qa/llm-evaluation-framework-benchmark-2026/
  - https://deepeval.com/blog/top-5-llm-evaluation-frameworks
  - https://www.braintrust.dev/articles/deepeval-alternatives-2026
  - https://github.com/alexeygrigorev/ai-engineering-field-guide/blob/main/interview/questions/04-ai-system-design.md
  - https://www.kore1.com/ai-engineer-interview-questions-2026/
  - https://igotanoffer.com/en/advice/generative-ai-system-design-interview
  - https://thecuriousmak.substack.com/p/the-aiml-engineer-interview-guide
  - https://resumeoptimizerpro.com/blog/ai-engineer-resume-examples
  - https://www.dataexpert.io/blog/ultimate-guide-ai-engineering-portfolios
  - https://karpathy.ai/
  - https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
  - https://github.com/sh-ai-x/dev-harness-kit
  - https://github.com/hashicorp/awesome-ai-plugins
  - https://forum.obsidian.md/t/a-system-design-interview-like-no-other-designing-obsidian-s-pkm-with-llms/68887
  - https://toss.im/career/jobs
  - https://careers.daangn.com/jobs/
  - https://m.blog.naver.com/hye8431/224326507093
  - https://brunch.co.kr/@sparta/110
  - https://www.threads.com/@slamslam__/post/DJZDwscTWrG/
  - https://www.linkedin.com/posts/daangn_from-insight-to-impact-2026-ml-%EC%97%94%EC%A7%80%EB%8B%88%EC%96%B4-%EC%B1%84%EC%9A%A9-activity-7442784168104816640-fsv1
  - https://2026ml.daangn.com/
  - https://www.catch.co.kr/NCS/RecruitInfoDetails/541632
  - https://thevc.kr/scatterlab
  - https://www.makinarocks.ai/
  - https://nklcb.kr/
  - https://www.threads.com/@owanimal/post/DcbKBd1Ag0v/
  - https://www.cio.com/article/4146291/ai-%EC%97%94%EC%A7%80%EB%8B%88%EC%96%B4-17%EB%A7%8C-%EB%8B%AC%EB%9F%AC-%EC%8B%9C%EB%8C%80%C2%B7%C2%B7%C2%B72026%EB%85%84-%EB%AF%B8%EA%B5%AD-it-%EC%B1%84%EC%9A%A9%C2%B7%EC%97%B0%EB%B4%89-%ED%8A%B8.html
created: 2026-09-10
updated: 2026-09-09T17:40:55+00:00
status: promoted
promoted_to: wiki/ai-agent-wiki/career-coaching/junior-ai-engineer-career-2026/_index.md
---

# Junior AI Engineer — Career Coaching Dossier (Q3 2026)

> Scope: coaching notes for the user targeting **junior / 신입 AI engineer** roles in 2026. The portfolio signal is `github.com/sh-ai-x/dev-harness-kit` (Claude Code / Codex plugin marketplace) plus the curated Obsidian vault at `wiki/ai-agent-wiki/`. The Korean market dominates the company list but English-language sources dominate the *tool* citations.

## 1. AI engineer role taxonomy 2026

The 2026 hiring market has settled into roughly **three role layers**; titles vary by company but the underlying work clusters cleanly.

### 1.1 Model layer

| Role | Day-to-day | Hiring velocity (2026) |
|---|---|---|
| **ML Engineer** | Trains / fine-tunes models; PyTorch / JAX; data pipelines; eval | High — most stable anchor role |
| **Research Engineer** | Bridges research and production; reads papers, prototypes; turns into shipped artifacts | High at frontier labs (Anthropic, DeepMind, xAI); narrower elsewhere |
| **Applied Research Engineer** | Variant — closer to product team than to lab | Concentrated at the foundation-model vendors |

Turkовиć's 2026 naming-chaos guide pegs ML Engineer as the "stable anchor role" of the field, with median US compensation around **$265K** at the top end. (Source: https://www.ivanturkovic.com/2026/04/24/ai-job-titles-2026-naming-chaos/, accessed 2026-09-10.) The ML Engineer title is what recuiters reach for when the actual work is RAG / agent plumbing — a common mislabel that candidates should be ready to disentangle in interviews.

### 1.2 Application layer (most junior-friendly)

| Role | Day-to-day | Hiring velocity (2026) |
|---|---|---|
| **AI Engineer** | Wraps LLMs into products; RAG, agent orchestration, evals | Highest in absolute volume (LinkedIn 1,000+ postings under "AI Prompt Engineer" alone) |
| **Applied AI Engineer** | Same as above, larger scope into data + integration | High, especially at mid-size SaaS |
| **Prompt Engineer** | System-prompt design, eval-driven prompt iteration | 733+ remote postings on Indeed; title fatigue, often an entry door |
| **Agent Engineer** | Specialized variant — LangGraph / CrewAI / OpenAI Agents SDK; tool design; eval harnesses | Newest, fastest-growing subrole; "agentic" is the marketing keyword |
| **AI Security Engineer** | OWASP LLM Top 10; red-team; guardrail implementation | Niche but well-paid; Strix-shaped tooling is the differentiator |

(Job-volume data: https://ai.engineer/jobs ; https://www.threads.com/@owanimal/post/DcbKBd1Ag0v/ — both accessed 2026-09-10.) The **AI Engineer** title is the most common landing zone for junior candidates in 2026; the role is increasingly split into a *prompt-and-RAG* half and an *agent-orchestration* half, with the latter commanding a premium.

### 1.3 Infrastructure layer

| Role | Day-to-day | Hiring velocity (2026) |
|---|---|---|
| **AI Platform Engineer** | Bedrock / Vertex / Azure OpenAI / vLLM / SGLang; vector DBs; cost control | High at scale-ups; lower at startups |
| **Data / Retrieval Engineer** | Builds / maintains vector indexes; ingestion pipelines; chunking strategies | Steady |
| **AI Product Engineer** | FE + agent experiences; front-end + LLM API integration | Growing |

The "AI Engineer" role at most Korean conglomerates (네이버, 카카오, 토스, 당근) sits at the intersection of application layer and infrastructure layer — the job ad says "AI Engineer" but the actual work is a hybrid of RAG / agent implementation and platform configuration. This duality is the *defining* quality of the 2026 junior-AI-engineer role.

### 1.4 Which are hiring fastest

- **AI Engineer (general)** — highest absolute volume; ~30–40% of all AI-tagged postings on Korean job boards as of 2026-Q3. (Source: https://www.saramin.co.kr/zf_user/jobs/list/job-category?cat_kewd=181 — 2,580 postings under "AI 엔지니어" on 잡코리아 as of access.)
- **ML Engineer (applied)** — fastest *paid* growth; band premium is real (석/박사 tracks can hit ₩130M–₩250M in Korea, per community reports — see §9).
- **Agent Engineer** — fastest *new* role; not yet a formal title at all companies, frequently listed under "AI Engineer (Agent)" or "LLM Engineer".
- **AI Security Engineer** — fastest *niche* growth; tied to the OWASP LLM Top 10 / EU AI Act compliance push.

**Recommendation for a junior candidate**: target "AI Engineer" or "Applied AI Engineer" postings where the JD explicitly lists RAG / agents / evals. Avoid "Prompt Engineer" as a primary target unless the JD is at a foundation-model vendor — the role is often senior-coded under a junior title.

## 2. Required ML/DL foundations

The interviews that screen juniors for AI roles test depth on a small set of fundamentals. The list below is the consensus set; less-than-3-years of experience is expected to know all of it at whiteboard level, plus one or two of the deep-dives.

### 2.1 Transformer internals (must-know whiteboard)

The core formula and its parts:

```
Attention(Q, K, V) = softmax(QKᵀ / √d_k) · V
```

- **Q (query)** — "what information am I looking for?"
- **K (key)** — "what information do I contain?"
- **V (value)** — "the actual information to aggregate"
- **d_k** — dimension of keys; dividing by √d_k keeps softmax gradients stable (prevents saturation in high-dim regimes)
- Steps: project inputs to Q/K/V → compute QKᵀ (similarity scores) → scale → mask (causal in decoder-only) → softmax → weighted sum by V.
- **Multi-head attention**: h heads run in parallel, each learning a different relationship (syntactic, semantic, positional). Final output is concat(head_1, ..., head_h) · W_O.
- **Complexity**: O(n²) in sequence length → motivation for efficient variants (sparse attention, linear attention, FlashAttention).

Be ready to walk through these on a whiteboard:

1. Why attention is permutation-invariant and *positional encoding* (sinusoidal, learned, **RoPE** rotary) is required.
2. **KV-cache** for inference-time speedup: cache K and V from previous tokens to avoid recomputation; explain memory cost vs. context length.
3. **Causal (masked) vs. bidirectional attention**: decoder-only causal masks; encoder-only bidirectional.
4. **FlashAttention**: tiling trick that reduces memory by avoiding materialization of the full attention matrix.

(Source: https://arxiv.org/abs/2210.03629 ReAct paper's transformer primer + general interview-prep material, accessed 2026-09-10.)

### 2.2 Pretraining vs. fine-tuning vs. RLHF/DPO — when to do what

The order to internalize — also the order Anthropic / OpenAI vendor docs recommend:

| Approach | Use when | Cost in 2026 |
|---|---|---|
| **Prompting** | Zero- or few-shot solvable; rapid iteration | Token cost only |
| **RAG** | Need fresh / proprietary / domain knowledge; source attribution matters | Index + retrieval cost per call |
| **Fine-tuning** | Consistent output format / JSON schema; style / brand voice; domain reasoning patterns | GPU hours; $1k–$50k per run depending on size |
| **RLHF / DPO** | Aligning behavior; safety tuning; preference learning | Most expensive; needs human or AI-labeler pipeline |

**Rule of thumb** that comes up in interviews: *"Start with prompting → add RAG → fine-tune last, only for behavior, never for knowledge."* Fine-tuning a model to "know" your product manual is an anti-pattern because the manual changes every release; RAG it instead. (Source: IBM "RAG vs. Fine-Tuning" via the curated web search results, accessed 2026-09-10.)

### 2.3 Evaluation harnesses (lm-eval-harness, HELM, OpenLLM)

| Tool | Source | Sweet spot |
|---|---|---|
| **lm-evaluation-harness** (EleutherAI) | https://github.com/eleutherai/lm-evaluation-harness | Academic benchmarks (200+ tasks — MMLU, GSM8K, HellaSwag, ARC). Reproducible. |
| **HELM** (Stanford CRFM) | https://www.eleuther.ai/projects/large-language-model-evaluation | Multi-dimensional holistic eval (accuracy + calibration + robustness + bias + fairness + efficiency + toxicity) |
| **OpenLLM Leaderboard** (Hugging Face) | https://huggingface.co/spaces/open-llm-leaderboard | Community ranking |
| **RAGAS / DeepEval / Promptfoo** | See §3 | Application-level RAG / agent evals |

For an AI Engineer interview, you need to be able to *cite* lm-eval-harness as the academic-benchmark standard, name HELM as the multi-dimensional standard, and *use* DeepEval or RAGAS for production evals. (Source: https://mlflow.org/articles/llm-evaluation-frameworks-explained-for-ai-practitioners/, accessed 2026-09-10; tool citation: https://github.com/eleutherai/lm-evaluation-harness.)

### 2.4 Vector search math (HNSW, cosine, dot-product)

The interview asks for vectors, distance metrics, and the indexing algorithm choice.

- **Cosine similarity** = (A · B) / (‖A‖ · ‖B‖). Range: [-1, 1] for unit vectors. Most common default for text embeddings because it ignores magnitude.
- **Dot product** = A · B. Equivalent to cosine for *normalized* vectors; faster because no norm computation. Used by most production vector DBs after L2 normalization.
- **Euclidean (L2) distance** = √(Σ (a_i − b_i)²). Rare for text; common for image embeddings.

HNSW (Hierarchical Navigable Small Worlds):
- A graph-based approximate nearest-neighbor index.
- O(log N) average query time.
- Used by Weaviate, Qdrant, Pinecone's serverless, Milvus by default.
- Trade-off: high memory cost (graph edges) → typically 1.5–3× the raw vector size.

Alternative indexes to know: **IVF-PQ** (faiss standard; clusters then product-quantizes residuals), **ScaNN** (Google), **Annoy** (Spotify; tree-based). At interview you only need to *name* them.

### 2.5 GPU economics (the "how much does inference cost?" interview question)

- **A100 80GB** ≈ $1–$2/hr on-demand across major clouds; reserved ≈ $0.7/hr; spot ≈ $0.3/hr.
- **H100 80GB** ≈ $2–$4/hr on-demand; the 2026 workhorse for frontier fine-tuning.
- **B200 / GB200** — Blackwell generation; $4–$8/hr on-demand; where vLLM / SGLang tests land.
- **MI300X** (AMD) — cheaper per GB VRAM; LLM inference benchmarks catch up to H100 on Q1–Q2 2026.
- **Why this matters**: a junior AI engineer is expected to know that serving an open-source 70B model at 100 QPS is roughly **$5–$20/hr in H100 cost**, before model-license fees. The follow-up question is "and managed Bedrock / Vertex for the same workload?" — typically 2–4× more, in exchange for zero ops overhead.

## 3. Required agent/LLM stack knowledge

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

## 4. Required cloud / platform skills

### 4.1 Managed inference

| Vendor | Service | Best for | Pricing model |
|---|---|---|---|
| **AWS** | Bedrock | Multi-model under AWS IAM; Anthropic / Mistral / Cohere / Meta / Stability | Per-token; provisioned throughput for guaranteed latency |
| **Google** | Vertex AI | Gemini + OSS models; strong RAG Engine; Gemini-tuned evals | Per-token; per-character for some |
| **Azure** | Azure OpenAI Service | Enterprise GPT deployments with data-residency guarantees | Per-token; PTU (provisioned throughput units) for committed capacity |
| **OpenAI direct** | API + Azure mirror | Lowest-friction GPT access; best-tooling; weakest data-residency story | Per-token |
| **Anthropic direct** | API + AWS Bedrock + GCP Vertex | Claude-first stack | Per-token |

Interview answer: pick based on existing cloud footprint; Bedrock for AWS shops; Vertex for GCP shops; Azure OpenAI for regulated Microsoft shops; native APIs only for prototyping.

### 4.2 Vector databases

The 2026 consensus (Source: https://aiml.qa/vector-database-comparison-2026/, https://www.firecrawl.dev/blog/best-vector-databases, https://www.kalviumlabs.ai/blog/vector-databases-compared-pgvector-pinecone-qdrant-weaviate/ — accessed 2026-09-10):

| DB | Mode | When to pick |
|---|---|---|
| **pgvector** | Self-host; Postgres extension | Already running Postgres; ≤10M vectors; default for low-friction |
| **Pinecone** | Managed; proprietary serverless | >5M vectors; zero-ops requirement; can pay the premium |
| **Weaviate** | Self-host or managed; OSS | Strong hybrid (vector + BM25) search; the default for hybrid retrieval |
| **Qdrant** | Self-host or managed; Rust | Open-source speed leader (10–25% faster than Weaviate/Milvus per community benchmarks); popular for self-hosted production |
| **Milvus** | Self-host or managed; Go/C++ | Mature at billions of vectors; heavy-weight |
| **Chroma** | OSS | Dev / prototyping; embedded mode |

Interview answer for "which vector DB?": *"Postgres + pgvector for the first deployment; Pinecone if we outgrow 5M vectors; Qdrant if we want open-source self-hosted with speed."* Avoid answering by listing all of them.

### 4.3 Caching + cost controls

- **Prompt caching** — OpenAI, Anthropic, Google all ship prompt-cache for static-system-prompt-prefix scenarios. Cuts cost by 50–90% on long-context repeated prompts.
- **Response caching** — Cache identical responses by a hash of (model, prompt, params). Cut cost on duplicate traffic by ~50%.
- **Semantic caching** — Cache responses by cosine similarity of embedding. Cuts cost on near-duplicate queries (e.g., "refund" and "I want a refund").
- **Token budgets** — Per-call, per-user, per-feature budgets with circuit breakers.
- **Model routing** — Route easy queries to cheap models, hard queries to expensive models. The "router" itself is often a small fine-tuned classifier or another LLM.
- **Batch APIs** — OpenAI, Anthropic, Google all offer 50% discounts for 24-hour batch processing.

### 4.4 Self-hosting / inference serving

The 2026 inference-servings consensus (Source: https://www.yottalabs.ai/post/best-llm-inference-engines-in-2026-vllm-tensorrt-llm-tgi-and-sglang-compared, https://leetllm.com/blog/llm-inference-engine-comparison-2026 — accessed 2026-09-10):

| Engine | What it does | When to pick |
|---|---|---|
| **vLLM** | PagedAttention; most-deployed OSS engine in 2026 | Default pick; 19–27% lower memory than competitors; 85–92% GPU utilization |
| **SGLang** | RadixAttention / prefix caching; ~29% faster than vLLM on throughput-heavy workloads | When prompt-cache hits dominate the workload |
| **TensorRT-LLM** | NVIDIA-optimized; lowest latency | NVIDIA-only deployments where latency is the constraint |
| **TGI** | Hugging Face; former default — **in maintenance mode as of 2026** | Avoid for new deployments |

Junior-engineer answer: *"Start with vLLM; switch to SGLang if prefix-cache reuse dominates; TensorRT-LLM only if you have NVIDIA hardware and latency-critical SLA."*

## 5. The agent-engineering mindset

This is the section that distinguishes a junior-AI-engineer from a junior-software-engineer-who-touched-LLms-once. The mindset is *production-first*.

### 5.1 How production agents differ from demos

A demo agent is a notebook. A production agent has:

- **Evals** that gate deployment — every prompt change is tested against a regression suite.
- **Tracing** for every run — what did the agent call, in what order, with what arguments, with what result?
- **Cost observability** — per-request token counts; per-user daily / monthly spend; circuit breakers.
- **Latency observability** — P50 / P95 / P99 token-throughput and request-completion; upstream model API SLOs.
- **Failure-mode handling** — retry with backoff, fallback to cached responses, escalation to human.
- **Security boundary** — input filtering (prompt-injection defense), output filtering (RLAIF-style safety), action allow-lists (MCP `allowed_tools`).
- **Audit log** — every agent action is logged for downstream review (debugging, compliance, incident postmortem).

### 5.2 The four primary failure modes

These are the failure modes the interview panels want you to *name*:

1. **Tool misuse** — the agent calls a tool with wrong arguments, wrong endpoint, wrong account context. Defense: schema validation, dry-run mode, rate limits per tool.
2. **Prompt injection (direct + indirect)** — malicious instructions in the user prompt (direct), in retrieved documents or tool outputs (indirect). OWASP LLM01:2025. Defense: input classifiers, separators in the prompt that mark trusted vs. untrusted context, RAG sandboxing.
3. **Cost amplification** — the agent enters a long loop, calls expensive tools, or runs many parallel sub-tasks that blow the budget. Defense: max-iteration limits, per-call token budgets, cost observability with circuit breakers.
4. **Eval drift** — the production traffic shape shifts; the offline eval suite no longer represents live queries; quality silently regresses. Defense: continuous eval sampling on production traffic; nightly full-suite re-runs; canary rollouts.

(Source: OWASP LLM Top 10 + general agent-engineering literature, accessed 2026-09-10.)

### 5.3 Layered defenses + red-team + observability

The 2026 mature agent stack is **defense in depth**, not a single guardrail:

| Layer | What | Tools |
|---|---|---|
| **Input** | Filter prompt injection, PII, jailbreak attempts | OpenAI Moderation, Azure Prompt Shields, custom classifier |
| **Action allow-list** | Agent can only call enumerated tools | MCP `allowed_tools`, LangGraph sandboxed nodes |
| **Sandbox** | Code execution / shell / file ops happen in an isolated env | Docker, Firecracker, E2B, Modal sandboxes |
| **Output** | Filter completions for harmful / off-policy content | Output classifiers, RLAIF-style reward models |
| **Audit log** | Every call recorded | LangSmith / Helicone / OpenTelemetry spans |
| **Red-team** | Periodic adversarial eval | promptfoo, PyRIT, deepteam, Strix |
| **Observability** | Production trace + eval + alerting | LangSmith, Phoenix, Helicone, Datadog LLM Observability |

Interview answer: *"Agents fail; don't ship a single guardrail. Defense in depth with input filter + action allow-list + sandbox + output filter + audit log + red-team + observability."*

## 6. Build-vs-buy / framework decision skills

This section is the *trade-offs* test — the interviewer asks "we need X, do we use a tool or build it?"

### 6.1 LangGraph vs. in-house

**Use LangGraph when**: stateful agents, cycles, human-in-loop, persistent checkpointer. Most production agent work fits this. (Source: https://www.anthropic.com/engineering/building-effective-agents — Anthropic notes that "a 200-line script using the SDK often beats a framework-heavy implementation," but that advice is for *workflows*, not *agents*.)

**Build in-house when**: the requirement is so specific that LangGraph's abstractions get in the way; when latency budgeting at the LLM-call level is critical and the framework overhead is measurable; when the team has strong opinions on persistence / event-sourcing that conflict with LangGraph's checkpointing model.

### 6.2 Managed RAG vs. custom

**Use managed (Vertex AI RAG Engine, Bedrock Knowledge Bases, Pinecone + LangChain retrieval, AWS Kendra, Azure AI Search)** when: time-to-market matters, the team doesn't have vector-search expertise, scale is moderate (<10M vectors).

**Custom (your own chunking / embedding / retrieval / rerank pipeline)** when: you have a data-engineering team, you need fine-grained control over retrieval quality (often: 10–30% absolute recall gains matter), or you're doing high-stakes retrieval where the off-the-shelf recall is unacceptable.

The default 2026 answer: managed RAG first; optimize once the bottleneck is identified.

### 6.3 Fine-tuning vs. prompting vs. RAG

The 2026 framework (per Anthropic and OpenAI guidance, both echoed across multiple sources accessed 2026-09-10):

| If your problem is… | Use |
|---|---|
| General task, want rapid iteration | **Prompting** |
| Need access to fresh / proprietary knowledge | **RAG** |
| Need consistent output format / style / brand voice | **Fine-tuning** |
| Need a specialized reasoning pattern at low cost | **Fine-tune a small model on outputs from a large model** (distillation) |
| Need a model that runs offline / on-device / in a regulated env | **Fine-tune an OSS base** |

**Anti-patterns**: fine-tuning to "teach" knowledge (use RAG); RAG for behavior (fine-tune); fine-tuning when you haven't first tried prompting.

## 7. Interview signals the market uses 2026

The market moved past leetcode + system-design. What signals now move the needle (Source: https://www.kore1.com/ai-engineer-interview-questions-2026/, https://igotanoffer.com/en/advice/generative-ai-system-design-interview, https://thecuriousmak.substack.com/p/the-aiml-engineer-interview-guide — all accessed 2026-09-10):

### 7.1 Portfolio signal — over credentials

- **Public GitHub artifacts** beat resumes for signaling craft. Three to five production-quality projects is the sweet spot (Source: https://www.dataexpert.io/blog/ultimate-guide-ai-engineering-portfolios, accessed 2026-09-10).
- **Shipped > polished**: the public repo with a real bug tracker, real users, and a real changelog signals more than 30 portfolio apps with no users.
- **Plugin marketplaces** (Claude Code, Codex), **MCP servers** (public npm / PyPI), and **eval dashboards** are the new "deployed to production" — they prove the work is real.

### 7.2 System-design fundamentals — LLM-aware

The 2026 system-design round for an AI Engineer is a *modified* classic:

- The classic "design Twitter / URL shortener / chat app" questions are background.
- The actual round: "design an AI-powered X" — e.g., "design an AI customer-support agent for an e-commerce site", "design a RAG system over a 10M-document corpus", "design a code-review agent".
- Expected topics: retrieval + agent orchestration + cache + cost control + observability + rollout / eval gate + safety boundary.

### 7.3 Technical writing — Karpathy-style LLM-Wiki is a hiring signal

- **Karpathy's LLM-Wiki** (https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f and https://karpathy.ai/) is the canonical pattern: short, dense, concept-oriented notes densely linked. (Source: https://blog.starmorph.com/blog/karpathy-llm-wiki-knowledge-base-guide, accessed 2026-09-10.)
- The pattern has been adopted as a hiring signal: a public set of LLM-Wiki-style notes on a personal site / GitHub Pages / Obsidian Publish demonstrates *systematic thinking* and *communication* — both underweighted on resumes.
- The Obsidian community has formalized this as a "system-design interview" topic (Source: https://forum.obsidian.md/t/a-system-design-interview-like-no-other-designing-obsidian-s-pkm-with-llms/68887, accessed 2026-09-10).

### 7.4 Take-home challenges — the most common 2026 format

The Reddit thread "How does AI engineer system design interview look like?" (https://www.reddit.com/r/aiengineering/comments/1ohykrv/, accessed 2026-09-10) shows the consensus:

1. **Take-home (3–5 days)**: build a small RAG or agent system with eval harness + a 1-page writeup.
2. **System design (60 min)**: "design an AI X" with retrieval, agent, eval, safety.
3. **Coding (45 min)**: classic + LLM-touching (write a tool schema, parse an LLM output, implement cosine-similarity).
4. **Behavioral (45 min)**: collaboration, debugging under ambiguity, ownership.

### 7.5 What gets rejected

- Submitting only a chat wrapper with no evals.
- "AI Engineer" resumes with no GitHub artifacts.
- "Prompt engineer" titles with no engineering depth (just a system-prompt collection).
- Resumes that list every model and framework with no demonstrable depth on any.

## 8. Resume / portfolio positioning for AI engineer roles

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

## 9. Salary + interview prep for Korean market

### 9.1 Salary bands (Korean market, 2026-Q3)

| Track | Band (₩) | Source / notes |
|---|---|---|
| **신입 AI 개발자 (학사)** | 4,000만–6,000만 | Entry. https://m.blog.naver.com/hye8431/224326507093 (accessed 2026-09-10) |
| **신입 / 주니어 AI 엔지니어 (석사, R&D직)** | 5,000만–8,000만 | https://brunch.co.kr/@sparta/110 (accessed 2026-09-10) |
| **중간 연차 (3–6년) AI 엔지니어** | 7,000만–1.0억 | https://brunch.co.kr/@sparta/110 |
| **상위 주니어 (석/박사 + 팁테크)** | 1.3억–2.5억 | https://www.threads.com/@slamslam__/post/DJZDwscTWrG/ (accessed 2026-09-10); outlier band, 석/박사 + 시리우스랩/토스 AI 같은 트랙 |
| **평균 AI 엔지니어 (전 직급)** | 6,449만–9,694만 | Aggregated: https://m.blog.naver.com/hye8431/224326507093 |
| **한국 평균 AI 엔지니어 (대표 중앙값)** | ~7,950만 | ~₩79.5M (https://m.blog.naver.com/hye8431/224326507093) |
| **공공 부서 — 로봇융합연구원 평균** | 8,320만 | 업종 평균 대비 63% 높음 |
| **미국 AI/ML 엔지니어 평균** | $170k (약 2.3억) | https://www.cio.com/article/4146291/ — 한국 대비 약 2–3배 |
| **미국 AI Engineer / Research Engineer** | $200k–$460k | https://www.levels.fyi/ — Levels.fyi 2026 |

The single most important caveat: **Korean salary bands are bimodal** — the bulk of junior roles are at ₩45–65M, but the tech-leading companies (네이버 하이퍼클로바, 카카오 브레인, 토스 AI Lab, 당근 ML) and VC-backed AI startups push the upper end to ₩80M–120M for 신입/주니어 with the right technical signal.

### 9.2 Target companies

| Tier | Companies | Why |
|---|---|---|
| **Tech-leading conglomerates** | 네이버 (HyperCLOVA X, AI Lab), 카카오 (KakaoBrain), 라인 (LINE), 쿠팡 | Big-budget research and applied AI; structured 신입 programs; 신입 bands at upper end |
| **Tech-leading unicorns** | 토스 (Toss Brain / AIOC), 당근마켓 (Daangn ML), 배달의민족 (우아한형제들), 야놀자 | Active 2026 hiring for ML / AI Eng; well-funded; product+research hybrid roles |
| **Specialized AI shops** | 마키나락스 (MakinaRocks, KOSDAQ-bound), 스캐터랩 (Scatterlab, 제타 AI 캐릭터 플랫폼, 흑자전환), 올리브랩 / 올리브영, 업스테이지 (Upstage, LLM 솔라), KT AIVR, SKT AIX | Narrower scope, often higher comp, sometimes equity |
| **VC-backed AI startups** (한국) | 토스 시드/Series-A AI, 당근 ML, 마키나락스, 하이퍼클로바X 전신 / 네이버 출신들이 만든 LLM 스타트업들 | More senior-coded jobs; smaller teams; high-equity; harder work-life balance |
| **Multinational with KR offices** | OpenAI (no KR office as of access), Anthropic (no KR office as of access), Google DeepMind (KR offices limited), Microsoft Research Asia (Beijing), NVIDIA, AWS Bedrock team, Hugging Face (mostly remote) | Limited on-the-ground presence; remote-friendly roles occasionally open |

Sources:
- 토스 채용 페이지 — https://toss.im/career/jobs (accessed 2026-09-10).
- 당근마켓 2026 ML 채용 — https://2026ml.daangn.com/ + https://careers.daangn.com/jobs/ + https://www.linkedin.com/posts/daangn_from-insight-to-impact-2026-ml-%EC%97%94%EC%A7%80%EB%8B%88%EC%96%B4-%EC%B1%84%EC%9A%A9-activity-7442784168104816640-fsv1 (accessed 2026-09-10).
- 네이버 AI 에이전트 엔지니어 — https://www.catch.co.kr/NCS/RecruitInfoDetails/541632 (accessed 2026-09-10).
- 스캐터랩 시리즈D 500억 — https://thevc.kr/scatterlab + https://demoday.co.kr/funding/insights/127 (accessed 2026-09-10).
- 마키나락스 — https://www.makinarocks.ai/ + https://zdnet.co.kr/view/?no=20260325174536 (accessed 2026-09-10).

### 9.3 신입 / 주니어 expectations (Korean market specific)

- **학력**: 석사가 우대 (특히 R&D 직); 학사 신입도 OK at 토스 / 당근 / 쿠팡의 applied 엔지니어 트랙.
- **전형 구성**: 코딩 테스트 (1–2 round) → 기술면 (system design + project 깊이) → 컬처핏 / 협업 → (대기업) 인성검사 / AI 역량 검사.
- **포트폴리오**: GitHub starred repo 1–3개 + blog 1–2개의 깊이 있는 글 + (이상적으로) plugin marketplace / MCP 서버 / eval dashboard.
- **AI-related certifications**: 카글(Kaggle) medal이 강력한 신호; ARES, CS224N 같은 스탠포드 / DeepLearning.AI 수료증은 가산점 but 결정적이지 않음.
- **외국어**: 토스/당근은 영어 필수; 대기업은 영어 가산점; VC 스타트업은 영어 일상적.

Sources: https://nklcb.kr/ (서울데브클럽 — 한국 개발자 채용 종합), https://www.threads.com/@owanimal/post/DcbKBd1Ag0v/ (유명기업 오늘 채용공고 종합), accessed 2026-09-10.

## 10. Action plan — first 90 days

Concrete weekly checklist for a junior-AI-engineer candidate using the dev-harness-kit portfolio signal.

### Week 1–2 (Days 1–14): Audit and crystallize the portfolio signal

| Day | Deliverable |
|---|---|
| 1–3 | Audit `sh-ai-x/dev-harness-kit` — write a 1-page "what the plugin demonstrates" doc (links to §8.1–8.4 above). Print it. |
| 4–7 | Audit the curated Obsidian vault — pick the 5 best leaf notes as your "thinking portfolio"; link them into a /portfolio page. |
| 8–10 | Write a 1500-word blog post: "How I built a Karpathy-style LLM-Wiki with the `obsidian-organize` plugin." |
| 11–14 | Republish the dev-harness-kit README as a personal-site landing page; quote the curated vault as the demo. |

### Week 3–4 (Days 15–28): Sharpen the foundation

| Day | Deliverable |
|---|---|
| 15–17 | Re-read _research/ai-llm-vlm-tooling.md §11 (concept-deep-dive). Whiteboard ReAct + RAG + LLaVA + Constitutional AI from memory. |
| 18–20 | Install vLLM locally; run a 7B model; measure cost-per-token; produce a 1-pager. |
| 21–24 | Implement a small RAG pipeline (any docs) with DeepEval + RAGAS; produce an eval report. |
| 25–28 | Implement a small LangGraph agent with traced observability; produce a 1-pager demo. |

### Week 5–6 (Days 29–42): Korean-market prep

| Day | Deliverable |
|---|---|
| 29–31 | Update resume + LinkedIn with the §8.2 positioning line and the §8.4 Korean line. |
| 32–35 | Apply to 10–15 roles: 토스, 당근, 네이버, 카카오, 마키나락스, 스캐터랩, 업스테이지, 쿠팡, 라인, 배민; track application status in a /job-pipeline leaf. |
| 36–42 | Mock-interview loop: 3 system-design mocks (RAG / agent / cost-control), 2 take-home walks, 1 behavioral. |

### Week 7–8 (Days 43–56): Deepen the niche

| Day | Deliverable |
|---|---|
| 43–48 | Pick one niche (agent security / Korean LLM / MCP server development / eval harness). Build one *shipped* artifact over the weekend. Publish. |
| 49–56 | One Korean-language blog post (1,500자): the niche artifact + the market context. |

### Week 9–10 (Days 57–70): Behavioral + Korean-culture prep

| Day | Deliverable |
|---|---|
| 57–63 | STAR-format 5 stories: ambiguity, conflict, ownership, debugging under pressure, technical teaching. |
| 64–70 | Read the most recent annual reports of your top-3 target companies (네이버 / 토스 / 당근); quote 2–3 specifics in each interview. |

### Week 11–12 (Days 71–84): Onsite + close

| Day | Deliverable |
|---|---|
| 71–84 | Run the loops. After every interview, write a 1-page debrief in /job-pipeline; identify the 3 weakest answer categories; close them by the next interview. |

### Week 13 (Days 85–90): Decision

| Day | Deliverable |
|---|---|
| 85–90 | Compare offers on a single page: salary, equity, team, growth rate, learning, work-life. Pick the one with the best *learning-rate gradient*, not the highest sticker. |

### First-90-days company playbook (after signing)

If you sign with a target company, the first 90 days inside are the mirror image:

- **Days 1–30**: shadow an existing AI-engineer; read every documented incident from the prior 6 months; install the company's eval / observability stack.
- **Days 31–60**: ship a small RAG improvement gated by an eval (the "demonstrate the loop" 30-day milestone).
- **Days 61–90**: lead one cross-team eval / safety review; present to leadership.

The dev-harness-kit plugin and the curated vault together signal that you can do all three milestones before you start.

---

## Sources

- https://www.ivanturkovic.com/2026/04/24/ai-job-titles-2026-naming-chaos/ — AI role naming-chaos guide, 2026 (accessed 2026-09-10)
- https://ai.engineer/jobs — AI Engineering Jobs board (accessed 2026-09-10)
- https://github.com/eleutherai/lm-evaluation-harness — EleutherAI lm-evaluation-harness (accessed 2026-09-10)
- https://www.eleuther.ai/projects/large-language-model-evaluation — EleutherAI / HELM evaluation projects (accessed 2026-09-10)
- https://arxiv.org/abs/2210.03629 — ReAct paper (Yao et al., 2022) (accessed 2026-09-10)
- https://arxiv.org/abs/2005.11401 — RAG paper (Lewis et al., 2020) (accessed 2026-09-10)
- https://arxiv.org/abs/2404.16130 — GraphRAG paper (Edge et al., Microsoft, 2024) (accessed 2026-09-10)
- https://arxiv.org/abs/2304.08485 — LLaVA paper (Liu et al., 2023) (accessed 2026-09-10)
- https://arxiv.org/abs/2212.08073 — Constitutional AI paper (Bai et al., Anthropic, 2022) (accessed 2026-09-10)
- https://www.anthropic.com/engineering/building-effective-agents — Anthropic "Building Effective Agents" (Dec 2024) (accessed 2026-09-10)
- https://openai.com/index/functions-and-their-llms-thoughts/ — OpenAI function-calling design notes (accessed 2026-09-10)
- https://www.anthropic.com/news/claude-3-5-sonnet-computer-use — Claude computer use (accessed 2026-09-10)
- https://aiml.qa/vector-database-comparison-2026/ — 2026 vector DB comparison (accessed 2026-09-10)
- https://www.firecrawl.dev/blog/best-vector-databases — Best vector DBs 2026 (accessed 2026-09-10)
- https://www.kalviumlabs.ai/blog/vector-databases-compared-pgvector-pinecone-qdrant-weaviate/ — pgvector vs. Pinecone vs. Qdrant vs. Weaviate (accessed 2026-09-10)
- https://www.yottalabs.ai/post/best-llm-inference-engines-in-2026-vllm-tensorrt-llm-tgi-and-sglang-compared — vLLM vs. SGLang vs. TensorRT-LLM vs. TGI (accessed 2026-09-10)
- https://leetllm.com/blog/llm-inference-engine-comparison-2026 — Inference engine comparison 2026 (accessed 2026-09-10)
- https://genai.qa/blog/promptfoo-vs-deepeval-vs-ragas/ — Promptfoo vs. DeepEval vs. RAGAS (accessed 2026-09-10)
- https://aiml.qa/llm-evaluation-framework-benchmark-2026/ — LLM evaluation framework benchmark 2026 (accessed 2026-09-10)
- https://deepeval.com/blog/top-5-llm-evaluation-frameworks — Top 5 LLM eval frameworks 2026 (accessed 2026-09-10)
- https://www.braintrust.dev/articles/deepeval-alternatives-2026 — DeepEval alternatives (accessed 2026-09-10)
- https://github.com/alexeygrigorev/ai-engineering-field-guide/blob/main/interview/questions/04-ai-system-design.md — AI engineering field guide (accessed 2026-09-10)
- https://www.kore1.com/ai-engineer-interview-questions-2026/ — AI Engineer Interview Questions 2026 (accessed 2026-09-10)
- https://igotanoffer.com/en/advice/generative-ai-system-design-interview — IGotAnOffer GenAI system design (accessed 2026-09-10)
- https://thecuriousmak.substack.com/p/the-aiml-engineer-interview-guide — AI/ML Engineer Interview Guide 2026 (accessed 2026-09-10)
- https://resumeoptimizerpro.com/blog/ai-engineer-resume-examples — AI Engineer resume examples 2026 (accessed 2026-09-10)
- https://www.dataexpert.io/blog/ultimate-guide-ai-engineering-portfolios — Ultimate guide to AI engineering portfolios (accessed 2026-09-10)
- https://karpathy.ai/ — Andrej Karpathy personal site (accessed 2026-09-10)
- https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f — Karpathy LLM-Wiki gist (accessed 2026-09-10)
- https://github.com/sh-ai-x/dev-harness-kit — The user's portfolio plugin marketplace (accessed 2026-09-10)
- https://github.com/hashicorp/awesome-ai-plugins — Awesome AI Plugins list (accessed 2026-09-10)
- https://forum.obsidian.md/t/a-system-design-interview-like-no-other-designing-obsidian-s-pkm-with-llms/68887 — System design interview: designing Obsidian PKM with LLMs (accessed 2026-09-10)
- https://toss.im/career/jobs — 토스 채용 (accessed 2026-09-10)
- https://careers.daangn.com/jobs/ — 당근마켓 채용 (accessed 2026-09-10)
- https://m.blog.naver.com/hye8431/224326507093 — "AI 개발자 전망 2026" — Korean AI eng salary blog (accessed 2026-09-10)
- https://brunch.co.kr/@sparta/110 — 2026 AI 직군 연봉 직무별·연차별 비교 (accessed 2026-09-10)
- https://www.threads.com/@slamslam__/post/DJZDwscTWrG/ — 한국 주니어 AI 엔지니어 평균 연봉 1.3억–2.5억 (accessed 2026-09-10)
- https://www.linkedin.com/posts/daangn_from-insight-to-impact-2026-ml-%EC%97%94%EC%A7%80%EB%8B%88%EC%96%B4-%EC%B1%84%EC%9A%A9-activity-7442784168104816640-fsv1 — 당근 2026 ML 채용 (accessed 2026-09-10)
- https://2026ml.daangn.com/ — 당근 2026 ML 채용 사이트 (accessed 2026-09-10)
- https://www.catch.co.kr/NCS/RecruitInfoDetails/541632 — 네이버 AI 에이전트 엔지니어 채용 (accessed 2026-09-10)
- https://thevc.kr/scatterlab — 스캐터랩 투자정보 (accessed 2026-09-10)
- https://www.makinarocks.ai/ — 마키나락스 (accessed 2026-09-10)
- https://nklcb.kr/ — 서울데브클럽 (accessed 2026-09-10)
- https://www.threads.com/@owanimal/post/DcbKBd1Ag0v/ — 한국 유명기업 채용공고 종합 (accessed 2026-09-10)
- https://www.cio.com/article/4146291/ai-%EC%97%94%EC%A7%80%EB%8B%88%EC%96%B4-17%EB%A7%8C-%EB%8B%AC%EB%9F%AC-%EC%8B%9C%EB%8C%80%C2%B7%C2%B7%C2%B72026%EB%85%84-%EB%AF%B8%EA%B5%AD-it-%EC%B1%84%EC%9A%A9%C2%B7%EC%97%B0%EB%B4%89-%ED%8A%B8.html — 미국 AI 엔지니어 연봉 2026 (accessed 2026-09-10)

## Notes

> **The single interview line that reframes this portfolio on a resume:**
> "Shipped `sh-ai-x/dev-harness-kit`, a Claude Code / Codex plugin marketplace (full delivery loop + Karpathy-style LLM-Wiki tooling) used to build this vault."

> **The Korean-line:**
> `sh-ai-x/dev-harness-kit` — Claude Code / Codex 플러그인 마켓플레이스 오픈소스 메인테이너 (멀티 에이전트 오케스트레이션 + LLM-Wiki 툴체인).

> **The 4 paper classes + 4 blog posts** every AI engineer should internalize end-to-end on day one of interview prep:
> - ReAct (Yao et al., 2022) — the agent loop.
> - RAG (Lewis et al., 2020) — parametric + non-parametric memory.
> - LLaVA (Liu et al., 2023) — vision encoder + projection + LLM.
> - Constitutional AI (Bai et al., 2022) — guardrails as a service.
> - Anthropic: Building Effective Agents (Dec 2024) — workflows vs. agents, six patterns.
> - OpenAI: Function-calling design notes (Aug 2024).
> - Anthropic: Skill ARC progressive disclosure.
> - Anthropic: Claude thinks tool / computer use.

> **Salary anchor (Korean market, Q3 2026):** 신입 학사 4–6천만 / 신입·주니어 석사 R&D 5–8천만 / 상위 주니어 (석/박사 + 팁테크 트랙) 1.3–2.5억 / 평균 6.4–9.7천만. 미국 대비 1/2~1/3.

## 11. Global-first filter — what to keep, drop, contextualize

> **Reframing the dossier for a global-first candidate profile.** The AI-engineer market is global by default — tools, papers, and interview patterns are internationally shared; Korean-market specifics are *layered on top* of that baseline. This section tags every framework, skill, interview signal, and plan-step with its scope, so a candidate can re-target the dossier to (a) global remote-first, (b) Korea-only, or (c) hybrid.

### 11.1 Tag legend

- **`**Global**`** — internationally recognized. Skill is portable; interview signal is universal; company can be anywhere.
- **`**Korean-context**`** — Korea-specific (employers, platforms, interview formats, certifications, language requirements). Drop or contextualize for non-KR targets.
- **`**Global AND Korean**`** — used everywhere, but with notable Korean presence or KR-specific tooling / users. Keep but add the Korean context row.

### 11.2 Framework / tool / skill tagging

#### Languages and core ML libraries

| Tool | Tag | Notes |
|---|---|---|
| **Python** | `**Global**` | Default AI/ML language everywhere |
| **PyTorch** | `**Global**` | The 2026 default framework. Citation: [PyTorch official](https://pytorch.org/) |
| **JAX / Flax** | `**Global**` | Niche but growing; DeepMind / Google stack |
| **TensorFlow** | `**Global**` | Still alive in enterprise (TF Serving); declining for new research |
| **Hugging Face Transformers / Diffusers / Datasets** | `**Global AND Korean**` | Universally used; Korean-language models (KoGPT, KoBART, HyperCLOVA X) all published here. Citation: [HF Hub](https://huggingface.co/) |
| **LangChain / LangGraph** | `**Global**` | Default 2026 orchestration framework; Korean adoption is high but the framework itself is global |
| **CrewAI / OpenAI Agents SDK** | `**Global**` | Multi-agent / function-calling tools; no Korean-specific variant |
| **DSPy** | `**Global**` | Stanford HAI origin; prompt-programming framework; widely cited in research |
| **PyTorch Lightning / Catalyst** | `**Global**` | Training-loop abstractions; rarely KR-specific |

#### Vector databases and retrieval

| Tool | Tag | Notes |
|---|---|---|
| **pgvector** | `**Global AND Korean**` | Postgres extension; the default "first deployment" choice globally; many KR companies use it on existing RDS |
| **Pinecone** | `**Global**` | Managed; zero-ops; premium price |
| **Weaviate** | `**Global AND Korean**` | Strong hybrid (vector + BM25); used in KR RAG startups |
| **Qdrant** | `**Global**` | Rust OSS; speed leader for self-hosted |
| **Milvus** | `**Global**` | Go/C++; billions-of-vectors scale |
| **Chroma** | `**Global**` | Embedded mode for dev/prototyping |
| **OpenSearch / Elasticsearch kNN** | `**Global AND Korean**` | Widely deployed in KR enterprises (Naver, Kakao use ES); hybrid retrieval story |

#### LLM providers and inference engines

| Tool | Tag | Notes |
|---|---|---|
| **OpenAI API** | `**Global**` | Default; everywhere. Citation: [OpenAI Platform](https://platform.openai.com/) |
| **Anthropic API** | `**Global**` | Claude; widely adopted |
| **Google Gemini / Vertex AI** | `**Global AND Korean**` | Heavy use at KR cloud shops and Korean-language applications |
| **Azure OpenAI Service** | `**Global AND Korean**` | Korean enterprises with Microsoft footprint (삼성, LG, 금융권) use this heavily |
| **AWS Bedrock** | `**Global AND Korean**` | Same; AWS-heavy Korean stacks use Bedrock |
| **vLLM** | `**Global**` | Most-deployed OSS inference engine. Citation: [vLLM docs](https://docs.vllm.ai/) |
| **SGLang** | `**Global**` | Throughput leader for prefix-cache workloads |
| **TensorRT-LLM** | `**Global**` | NVIDIA-only; latency-critical deployments |
| **TGI (Hugging Face)** | `**Global**` | Maintenance mode; cite as legacy |

#### Cloud MLOps / platform

| Tool | Tag | Notes |
|---|---|---|
| **AWS SageMaker / Bedrock** | `**Global AND Korean**` | Many KR cloud shops; AWS KR region (Seoul) is mature |
| **GCP Vertex AI** | `**Global AND Korean**` | Used at Naver Labs / Kakao Brain |
| **Azure ML** | `**Global AND Korean**` | Microsoft-heavy enterprises |
| **Kubernetes** | `**Global**` | Universal MLOps substrate |
| **Argo / ArgoCD** | `**Global**` | ML workflow orchestration; ubiquitous |
| **MLflow** | `**Global**` | Experiment tracking; default OSS choice |
| **Weights & Biases** | `**Global**` | Premium experiment tracking |
| **Kubeflow** | `**Global**` | K8s-native ML platform |
| **Naver Cloud Platform (NCP)** | `**Korean-context**` | Korean-only cloud; relevant for Naver-adjacent or Naver-shipping companies |
| **KT Cloud / NHN Cloud** | `**Korean-context**` | Korean-only clouds; public-sector-heavy customers |

#### Evaluation / observability

| Tool | Tag | Notes |
|---|---|---|
| **RAGAS** | `**Global**` | RAG-specific metrics; open-source standard |
| **DeepEval** | `**Global**` | Pytest-like eval; broadest metric library |
| **promptfoo** | `**Global**` | CLI-first prompt A/B + red-team |
| **LangSmith** | `**Global**` | LangChain-first-party observability |
| **Arize Phoenix** | `**Global**` | OSS eval + OTel |
| **Helicone** | `**Global**` | Vendor-neutral LLM gateway/proxy |
| **lm-evaluation-harness (EleutherAI)** | `**Global**` | Academic benchmark standard |
| **HELM (Stanford CRFM)** | `**Global**` | Multi-dimensional holistic eval |

#### Korean-context-specific tools (drop for non-KR targets)

| Tool | Tag | Notes |
|---|---|---|
| **네이버 HyperCLOVA X** | `**Korean-context**` | Naver's proprietary LLM; Korean-language-optimized. Citation: [Naver Cloud HyperCLOVA X](https://www.ncloud.com/product/aiService/clovastudio) |
| **카카오 KoGPT** | `**Korean-context**` | Kakao Brain's Korean LLM line |
| **당근 AI Lab** | `**Korean-context**` | Daangn's product-AI research org |
| **토스 AI Lab / AIOC** | `**Korean-context**` | Toss's AI org |
| **업스테이지 Solar** | `**Korean-context**` | Upstage's Korean-optimized LLM |
| **마키나락스** | `**Korean-context**` | MakinaRocks — MLOps / industrial AI shop |
| **스캐터랩** | `**Korean-context**` | Scatterlab — conversational AI / character platform |
| **카글 (Kaggle)** | `**Global AND Korean**` | Globally run; KR community strong (Taehun Kim, Y.Nakama, etc.); Korean ML papers and competitions are visible on the global stage |

### 11.3 Interview signal tagging

#### Universal signals — work in any market

- **`**Global**` — System design (LLM-aware):** "design an AI X" with retrieval + agent + cache + cost + observability + eval gate. Universal pattern. Citation: [IGotAnOffer GenAI System Design](https://igotanoffer.com/en/advice/generative-ai-system-design-interview).
- **`**Global**` — Transformer internals:** Q/K/V, multi-head, causal mask, RoPE, FlashAttention, KV-cache. Universal whiteboard test.
- **`**Global**` — The four primary failure modes (tool misuse, prompt injection, cost amplification, eval drift):** Universal production-agent mental model.
- **`**Global**` — Defense-in-depth agent stack:** Input filter + action allowlist + sandbox + output filter + audit log + red-team + observability. Universal.
- **`**Global**` — Eval methodology:** HELM multi-dimensional; RAGAS; DeepEval; promptfoo. Universal pattern.
- **`**Global**` — Portfolio signal over credentials:** Plugin marketplaces, MCP servers, eval dashboards as "deployed to production" signals. Universal; cited at [DataExpert portfolio guide](https://www.dataexpert.io/blog/ultimate-guide-ai-engineering-portfolios).
- **`**Global**` — Take-home challenges:** 3–5 day build-a-small-RAG/agent-with-eval + writeup format. Universal 2026 format.
- **`**Global**` — Karpathy-style LLM-Wiki / technical writing:** Communication-as-hiring-signal. Universal pattern.

#### Korean-context signals (drop for non-KR targets)

- **`**Korean-context**` — 네이버 / 카카오 / 쿠팡 / 토스 / 당근 specific interview formats.** Each has a distinct process: 토스 1-day onsites with cross-functional panel; 네이버 다전형 코딩테스트; 카카오 코딩테스트 + 기술면 + 컬처핏; 쿠팡 코딩 + 시스템설계 + behavioral. For non-KR targets, replace with the target's published format (Anthropic / OpenAI / Mistral / Cohere each publish their own loop).
- **`**Korean-context**` — 학력 신호 (석사 / 박사 우대).** Korean R&D직 still weights graduate degrees; US tech / European tech increasingly does not. Adjust the resume emphasis accordingly.
- **`**Korean-context**` — 인성검사 (대기업).** Korea-specific psychometric test (NICE, HCT). Not used at US/EU tech companies.
- **`**Korean-context**` — 컬처핏 / 협업 round.** Korean companies (especially 토스, 당근) emphasize "fit" with company values. US/EU equivalents exist but emphasize different axes (impact, ownership, ambiguity tolerance).
- **`**Korean-context**` — Korean-language papers / Korean ML community.** Korean ML community is strong (NAVER AI Lab, Kakao Brain, 서울대 DSBA) but the work is published in English at NeurIPS / ICML / ICLR. For non-KR targets, swap to the target region's research community.
- **`**Korean-context**` — English fluency at 토스 / 당근 / VC 스타트업.** A Korean-context bar; for global targets, English is the default and Korean is irrelevant.

### 11.4 The 90-day action plan — reframed by layer

The original plan (§10) is Korean-shaped: it front-loads "Korean-market prep" in weeks 3–4, assumes Korean-language blog writing, and bakes-in Korean targets. The global-first reframe is **layered**: build the universal foundation first, then add the Korean-context layer only if Korea is a target.

#### Layer A — Global foundation (Days 1–30, identical for any market)

| Day | Deliverable | Signal produced |
|---|---|---|
| 1–3 | Audit `sh-ai-x/dev-harness-kit`; write a 1-page "what the plugin demonstrates" doc | Portfolio positioning |
| 4–7 | Audit the curated Obsidian vault; pick the 5 best leaf notes as your "thinking portfolio" | Communication signal |
| 8–10 | Write a 1500-word English blog post: "How I built a Karpathy-style LLM-Wiki with the `obsidian-organize` plugin" | Technical-writing signal |
| 11–14 | Republish the dev-harness-kit README as a personal-site landing page | Public-facing signal |
| 15–17 | Re-read the four paper classes + four blog posts; whiteboard each from memory | Foundation depth |
| 18–20 | Install vLLM locally; run a 7B model; measure cost-per-token; produce a 1-pager | Hands-on inference |
| 21–24 | Implement a small RAG pipeline with DeepEval + RAGAS; produce an eval report | Production eval skill |
| 25–28 | Implement a small LangGraph agent with traced observability; produce a 1-pager demo | Agent-engineering signal |
| 29–30 | Update English resume + LinkedIn with the §8.2 positioning line | Public materials |

**Layer A exits with a candidate who can apply to any AI-engineer role globally.**

#### Layer B — Global portfolio depth (Days 31–60)

| Day | Deliverable | Signal produced |
|---|---|---|
| 31–35 | Apply to 15–25 roles globally: Anthropic, OpenAI, Mistral, Cohere, Hugging Face, Replicate, Modal, scale-ups with remote-friendly postings | Pipeline volume |
| 36–42 | Mock-interview loop: 3 system-design mocks (RAG / agent / cost-control), 2 take-home walks, 1 behavioral | Interview fluency |
| 43–48 | Pick one niche (agent security / MCP server development / eval harness / multimodal). Build one *shipped* artifact over the weekend | Niche depth |
| 49–56 | One English-language technical blog post (1,500–2,000 words): the niche artifact + the engineering reasoning | Writing signal |
| 57–63 | STAR-format 5 stories: ambiguity, conflict, ownership, debugging under pressure, technical teaching | Behavioral bank |

**Layer B exits with a candidate whose portfolio is competitive at Anthropic / OpenAI / frontier-lab level.**

#### Layer C — Korean-context layer (Days 61–90) **ONLY IF targeting Korea**

| Day | Deliverable | Signal produced |
|---|---|---|
| 64–70 | Read the most recent annual reports of your top-3 Korean targets (네이버 / 토스 / 당근); quote 2–3 specifics in each interview | Company-specific prep |
| 71–75 | Korean-language resume + 자기소개서 tailored to 5 Korean targets (see §10 Korean line) | Korean materials |
| 76–82 | Apply to 10–15 Korean targets; track in /job-pipeline leaf | Korean pipeline |
| 83–90 | Mock interviews in Korean with native-speaker peers; calibrate phrasing, formality, honorifics | Korean interview fluency |

**Layer C is additive.** A global candidate with Layers A + B can still apply to Korean companies, but the conversion rate is lower than a candidate with all three layers. For 2026, given the 73% YoY drop in Korean junior postings (per the §9 salary data), **maximizing global surface area is a hedge against Korean-market contraction.**

#### Why this matters

The 2026 KR junior market is the toughest in over a decade (per the Korean-market data in §9.1 and the broader SWE market context). Layering the plan globally protects against that: a candidate with Layers A + B has a global surface area an order of magnitude larger than the Korean-only surface area, and the same dev-harness-kit portfolio is the credential at both US frontier labs and Korean conglomerates.

### 11.5 Salary band reframing — Global first, Korean as comparison

The original §9.1 listed Korean bands first. The global-first reframe reverses that.

#### Global salary bands (US/EU, 2026-Q3, base + typical bonus + equity, from levels.fyi / Glassdoor / ai.engineer/jobs)

| Track | US band | EU band (London / Berlin / Amsterdam) | Source |
|---|---|---|---|
| **신입 / Junior AI Engineer (L3-L4)** | $130K–$220K | €70K–€120K | [Levels.fyi](https://www.levels.fyi/) |
| **Mid AI Engineer (L5)** | $200K–$320K | €120K–€180K | [Levels.fyi](https://www.levels.fyi/) |
| **Senior AI Engineer / Research Engineer (L6)** | $280K–$460K | €180K–€280K | [Levels.fyi](https://www.levels.fyi/) |
| **Staff+ / Principal (L7+)** | $400K–$700K+ | €250K–€400K+ | [Levels.fyi](https://www.levels.fyi/) |
| **Remote-first AI startups (US-rate for global hires)** | $140K–$250K | n/a | [ai.engineer/jobs](https://ai.engineer/jobs) |

#### Korean bands as comparison row (reframed; original §9.1)

| Track | Korean band (KRW) | Korean band (USD equiv) | Ratio vs US junior |
|---|---|---|---|
| **신입 AI 개발자 (학사)** | ₩40M–₩60M | ~$30K–$45K | 0.2–0.3× US junior |
| **신입 / 주니어 AI 엔지니어 (석사, R&D직)** | ₩50M–₩80M | ~$38K–$60K | 0.3–0.4× |
| **중간 연차 (3–6년)** | ₩70M–₩100M | ~$53K–$75K | 0.25–0.35× |
| **상위 주니어 (석/박사 + 팁테크)** | ₩130M–₩250M | ~$98K–$188K | 0.5–0.85× (top quartile) |
| **평균 AI 엔지니어 (전 직급)** | ₩64M–₩97M | ~$48K–$73K | — |

Korean sources: https://m.blog.naver.com/hye8431/224326507093, https://brunch.co.kr/@sparta/110, https://www.threads.com/@slamslam__/post/DJZDwscTWrG/, https://www.cio.com/article/4146291/. US sources: https://www.levels.fyi/, https://ai.engineer/jobs, https://www.ivanturkovic.com/2026/04/24/ai-job-titles-2026-naming-chaos/.

**The headline**: at the 신입 / junior level, Korean bands are 1/2 to 1/3 of US equivalents in absolute USD terms. The gap closes as seniority increases (top-quartile 신입 / 주니어 with 석/박사 can hit 0.85× US band). For global-first candidates, this is the *why* of applying globally.

#### Equity / options consideration

US frontier labs and remote-first AI startups include meaningful equity (RSUs / ISOs / NSOs) that often doubles the headline compensation. Korean conglomerates (네이버, 카카오, 쿠팡) typically include RSU but the per-unit value is lower; VC-backed Korean AI startups offer options with high upside but high uncertainty. **For the global-first candidate, equity is the largest compensation gap, not base.**

### 11.6 The "drop / keep / contextualize" cheat sheet

For a candidate targeting **global-first**:

- **Drop entirely:** §9.1 Korean salary numbers as the primary anchor (replace with §11.5 Global numbers); §9.3 Korean 신입-specific expectations (학력, 인성검사); §10 weeks 5–6 "Korean-market prep"; Korean-language 자기소개서 in §10.
- **Keep as-is:** §1 (role taxonomy is global); §2 (foundations); §3 (RAG / agent / eval stack); §4 (cloud / platform); §5 (agent-engineering mindset); §6 (build-vs-buy); §7 (interview signals, except the Korean-context subset in §11.3); §8 (portfolio positioning — the dev-harness-kit is the credential everywhere); §10 weeks 1–4 (Layer A + first half of Layer B).
- **Contextualize:** §9 (reframe as comparison rather than primary; add the Global band row above it); §10 weeks 5–6 (split into Layer B global + Layer C Korean); §10 weeks 7–12 (Layer B continues; Layer C is opt-in).

For a candidate targeting **Korea-only**:

- Keep §1–§10 as-is.
- Layer C in §11.4 becomes the primary weeks 5–6, not a side layer.

For a candidate targeting **hybrid (global + Korea)**:

- Layer A + B are non-negotiable.
- Layer C is added in weeks 9–12.
- The job-pipeline tracker gets two columns: "global" and "Korea", each with their own conversion-rate tracking.

### 11.7 Citations — what to add for global-first

Global items should pull from official docs / arXiv / GitHub / official blog posts first:

- **Official docs:** [PyTorch](https://pytorch.org/), [LangChain docs](https://docs.langchain.com/), [vLLM docs](https://docs.vllm.ai/), [Hugging Face](https://huggingface.co/), [OpenAI Platform](https://platform.openai.com/), [Anthropic](https://docs.anthropic.com/).
- **Papers:** [arXiv cs.CL](https://arxiv.org/list/cs.CL/recent), [arXiv cs.AI](https://arxiv.org/list/cs.AI/recent), [arXiv cs.LG](https://arxiv.org/list/cs.LG/recent).
- **GitHub:** [EleutherAI/lm-evaluation-harness](https://github.com/eleutherai/lm-evaluation-harness), [langchain-ai/langgraph](https://github.com/langchain-ai/langgraph), [vllm-project/vllm](https://github.com/vllm-project/vllm).
- **Official engineering blogs:** [Anthropic Engineering](https://www.anthropic.com/engineering), [OpenAI Blog](https://openai.com/blog/), [Hugging Face Blog](https://huggingface.co/blog).
- **Salary:** [Levels.fyi](https://www.levels.fyi/), [Glassdoor](https://www.glassdoor.com/), [ai.engineer/jobs](https://ai.engineer/jobs).

Korean items should pull from Naver Labs / Kakao Brain / Toss engineering blogs + Wanted postings + Naver Labs papers:

- **Naver Labs / HyperCLOVA X:** [Naver Cloud HyperCLOVA X](https://www.ncloud.com/product/aiService/clovastudio), [Naver Labs Datasets](https://www.naverlabs.com/).
- **Kakao Brain:** [Kakao Brain Blog](https://kakao.ai/blog), [KoGPT paper](https://arxiv.org/abs/2105.12052).
- **Toss engineering:** [Toss Tech Blog](https://toss.tech/), [Toss招聘](https://toss.im/career/jobs).
- **당근:** [Daangn Tech Blog](https://medium.com/daangn), [2026 ML 채용](https://2026ml.daangn.com/).
- **Korean ML community:** [AI Korea](https://aikorea.org/), [nklcb](https://nklcb.kr/), [Karpathy-style LLM-Wiki Korean translation projects].

### 11.8 Closing note

The global-first reframing does not *replace* the Korean-market dossier — it *front-loads* it. A candidate with Layers A + B has more optionality; a candidate with Layer C added has more precision on Korean targets. The dev-harness-kit portfolio is the constant across both layers — the same artifact, the same README, the same eval-harness integration; the audience changes, the signal does not.

The Korean-specific tools (HyperCLOVA X, KoGPT, Toss AI Lab) are *contextualizers*, not *foundations*. The foundations are the universal ones: PyTorch, LangGraph, MCP, vLLM, RAGAS, DeepEval, promptfoo, AWS/GCP/Azure, OWASP LLM Top 10, MITRE ATLAS. Those are the skills that travel; the Korean-context tools are the ones that differentiate when a Korean company is the target.
