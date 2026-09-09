---
tags: ["agent-engineering", "agentops-workbench", "evaluation", "benchmark", "ragas", "helm", "swe-bench", "mt-bench", "dspy", "llm-as-judge", "interview-prep", "priority-critical"]
priority: critical
related:
  - ai-agent-wiki/agent-engineering/agentops-workbench/observability-otel
  - ai-agent-wiki/agent-engineering/agentops-workbench/reliability-durable-effects
  - ai-agent-wiki/agent-engineering/agentops-workbench/langsmith-reuse-vs-build
created: 2026-09-09
source: "https://arxiv.org/abs/2211.09110"
---

# Evaluation Methodology

> **"How do you know the agent is working?"** is asked in every AI-engineering interview. The canonical answer names four things: a benchmark that fits the task family, a deterministic outcome check, a calibrated LLM-as-judge on a *human-reviewed* subset, and a frozen held-out set that guards against contamination.

## The pitch (60 seconds)

Evaluation is not "did it produce something". Evaluation is **taxonomy-first, multi-metric, scenario-aware, contamination-controlled**. Cite HELM for the methodology; RAGAS for RAG-specific metrics; SWE-bench for code; MT-Bench for chat; DSPy for prompt-as-code optimization. The judge (if any) runs on a human-reviewed subset only — it can never grant permission or promote labels.

## The five sub-questions

### 1. What benchmark fits this task family?

- **Retrieval (recall@k).** BEIR (Thakur et al., NeurIPS 2021) — the canonical zero-shot retrieval benchmark. The finding: lexical BM25 is hard to beat out-of-distribution; hybrid dense+sparse wins on average.
- **RAG end-to-end.** RAGAS (Es et al., EMNLP 2023) — defines faithfulness, answer relevance, context relevance, context recall. The proposal's "deterministic, no-human-in-the-loop outcome check" maps to RAGAS-style metric runs.
- **Chat / instruction following.** MT-Bench / Chatbot Arena (Zheng et al., NeurIPS 2023) — paired human preference data; the canonical source for LLM-as-judge and its known biases (position, verbosity, self-enhancement).
- **Code / agentic task completion.** SWE-bench (Jimenez et al., ICLR 2024) — "real GitHub issue → ground-truth PR" task family; 2,294 issue-commit pairs across 12 Python repositories, with SWE-bench Verified as the human-curated subset.

### 2. What does "better" mean?

**HELM** (Liang et al., 2022) is the methodologically rigorous model: taxonomy-first (define the dimensions you're measuring across — accuracy, robustness, fairness, bias, toxicity, efficiency, …), multi-metric (don't pick one number), scenario-aware (per-segment reporting by demographic, by domain, by difficulty). Use this framing when defending "report raw counts by family" and "select an improvement only when evidence supports it".

### 3. How do you avoid contamination?

The standard toolkit:
- **n-gram overlap** between training and eval.
- **Canary strings** — unique strings inserted into training; check whether they appear in eval completions.
- **Private held-out sets** — datasets you never publish, never train on, only evaluate against.
- **Freeze-before-tuning** — commit the eval set hash *before* any further training, so a "minor retrain" can't quietly incorporate the eval.

The proposal's 30-case held-out guard is the right discipline.

### 4. LLM-as-judge: when and how

The MT-Bench paper is the canonical source for both the *value* and the *failure modes* of LLM-as-judge. Three known biases:
- **Position bias** — preferring the first or last response in a pair.
- **Verbosity bias** — preferring longer responses regardless of quality.
- **Self-enhancement bias** — preferring responses from the same model family.

The empirical finding: **~80% agreement with human preferences** — high enough to be useful, low enough to be dangerous. The proposal's rule ("an optional isolated LLM judge scores groundedness on a human-reviewed subset and **cannot** grant permission or promote labels") is the right framing: the judge is a *signal*, not a *gate*.

### 5. What's the routing / ML baseline?

The proposal's ML baseline is literally `TfidfVectorizer` + `LogisticRegression` from scikit-learn — a two-class pipeline. This is deliberate: a TF-IDF + LR baseline is the strongest non-LLM baseline you can deploy in an afternoon, and beating it cleanly is the floor for claiming "the LLM is doing real work". The Cemri et al. (2025) finding — 50%+ of cases favor single-agent setups; multi-agent incurs ~15.2× compute and ~14.6× wall-clock — is the canonical defense for not jumping straight to a multi-agent topology comparison.

## What to defend in the interview

| Claim | Defense |
|---|---|
| "Why a benchmark at all?" | A benchmark is the only way to compare a new model/system to a baseline in numbers, not vibes. Without one, "it's better" is unfalsifiable. |
| "Why HELM-style multi-metric?" | Single-number benchmarks reward gaming. Taxonomy-first reporting surfaces the failure modes that aggregate scores hide. |
| "Why a frozen held-out set?" | The eval set has to be hard to accidentally leak into training. Frozen means a hash you check before every run. |
| "Why restrict the LLM-as-judge to a subset?" | ~80% agreement with humans is not enough to gate production. Use it as a fast first-pass signal on a human-reviewed subset; humans still make the call. |
| "Why TF-IDF + LR as the ML baseline?" | Beats random; deployable in an afternoon; beats naive LLM-on-everything. Beating it is the floor. |
| "Why not full multi-agent topology comparison?" | Cemri et al. 2025: 50%+ of cases favor single-agent; multi-agent is ~15× the compute. Stage the comparison, don't run a full factorial. |

## Statistical rigor

For paired comparisons across trials, cite Dror, Baumer, Shlomov & Reichart (EMNLP 2019) — the canonical "Hitchhiker's Guide to Testing Statistical Significance in NLP". The relevant warning: "extra trials of one case" do *not* create independent samples; bootstrap resampling or paired tests across cases are the correct tools. The proposal's "case-family-aware uncertainty" caveat is the right framing.

## Prompt-as-code (DSPy)

DSPy (Khattab, Zaharia, Potts, Stanford HAI) is the canonical "prompts as code, compiled to a policy" reference. The proposal's `prompt_version` field is the right abstraction — every prompt change is an experiment axis, recorded and reproducible. Cite DSPy and arXiv:2507.03620 ("Is It Time To Treat Prompts As Code?") when explaining why.

## Sources

- [BEIR: A Heterogeneous Benchmark for Zero-shot Evaluation of Information Retrieval Models (Thakur et al., NeurIPS 2021)](https://arxiv.org/abs/2104.08663) — canonical zero-shot retrieval benchmark
- [RAGAS: Automated Evaluation of Retrieval Augmented Generation (Es et al., EMNLP 2023)](https://arxiv.org/abs/2309.15217) — RAG-specific metrics (faithfulness, answer relevance, context relevance, context recall)
- [Holistic Evaluation of Language Models (HELM, Liang et al., 2022)](https://arxiv.org/abs/2211.09110) and [HELM project page](https://crfm.stanford.edu/helm/) — taxonomy-first, multi-metric methodology
- [SWE-bench (Jimenez et al., ICLR 2024)](https://arxiv.org/abs/2310.06770) — real GitHub issue → ground-truth PR task family; [SWE-bench Verified](https://openai.com/index/introducing-swe-bench-verified/) is the human-curated subset
- [Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena (Zheng et al., NeurIPS 2023)](https://aclanthology.org/2023.emnlp-main.153/) — LLM-as-judge source; position/verbosity/self-enhancement biases; ~80% human agreement
- [DSPy: Compiling Declarative Language Model Calls into State-of-the-Art Pipelines (Stanford HAI)](https://hai.stanford.edu/research/dspy-compiling-declarative-language-model-calls-into-state-of-the-art-pipelines) — prompts-as-code, compiled to a policy
- [Is It Time To Treat Prompts As Code? (arXiv:2507.03620)](https://arxiv.org/html/2507.03620v1) — multi-use-case study on DSPy-style optimization
- [scikit-learn TfidfVectorizer](https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfVectorizer.html) and [LogisticRegression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html) — the two-class ML baseline
- [The Hitchhiker's Guide to Testing Statistical Significance in NLP (Dror et al., EMNLP 2019)](https://aclanthology.org/2023.emnlp-main.153/) — paired-comparison rigor
- [LangSmith evaluation docs](https://docs.langchain.com/langsmith/evaluation) — capability surface for dataset / evaluator / experiment-run abstractions

## Related

- [[_index|agentops-workbench sub-hub]] — the 7-leaf preparation track
- [[../_index|Agent Engineering major hub]] — career-positioning view
- [[observability-otel|Observability — OpenTelemetry for Agents]] — what you measure in *production* (not just in eval)
- [[reliability-durable-effects|Reliability and Durable Effects]] — the next critical question after "does it work?" is "does it work *reliably*?"
- [[langsmith-reuse-vs-build|LangSmith — Reuse vs Build]] — concrete reuse decision for the eval infrastructure
