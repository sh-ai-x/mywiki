---
topic: junior-ai-engineer-career-2026/11
tags: ["career", "job-hunting", "junior", "ai-engineer", "global-first", "filter", "contextualization", "interview-prep"]
related: ["ai-agent-wiki/career-coaching/junior-ai-engineer-career-2026/_index"]
source: "_research/junior-ai-engineer-career-2026.md#11"
created: 2026-09-10
priority: high
job-hunting: true
global-first-filter: applied
---

# 11. Global-first filter — what to keep, drop, contextualize

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
