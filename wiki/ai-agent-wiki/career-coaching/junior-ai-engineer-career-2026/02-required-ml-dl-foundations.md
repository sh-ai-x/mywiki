---
topic: junior-ai-engineer-career-2026/02
tags: ["career", "job-hunting", "junior", "ai-engineer", "foundations", "transformer", "interview-prep", "global-first"]
related: ["ai-agent-wiki/career-coaching/junior-ai-engineer-career-2026/01-ai-engineer-role-taxonomy-2026", "ai-agent-wiki/ai-engineering-tooling/_index"]
source: "_research/junior-ai-engineer-career-2026.md#2"
created: 2026-09-10
priority: critical
job-hunting: true
global-first-filter: applied
---

# 2. Required ML/DL foundations

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
