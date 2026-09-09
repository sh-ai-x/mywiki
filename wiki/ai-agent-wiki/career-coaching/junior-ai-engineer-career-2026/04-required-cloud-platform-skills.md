---
topic: junior-ai-engineer-career-2026/04
tags: ["career", "job-hunting", "junior", "ai-engineer", "cloud", "platform", "interview-prep", "global-first"]
related: ["ai-agent-wiki/career-coaching/junior-ai-engineer-career-2026/03-required-agent-llm-stack-knowledge"]
source: "_research/junior-ai-engineer-career-2026.md#4"
created: 2026-09-10
priority: high
job-hunting: true
global-first-filter: applied
---

# 4. Required cloud / platform skills

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
