---
tags: ["agent-engineering", "agentops-workbench", "langsmith", "reuse-vs-build", "evaluation-infrastructure", "experiment-tracking", "interview-prep", "priority-medium"]
priority: medium
related:
  - ai-agent-wiki/agent-engineering/agentops-workbench/evaluation
  - ai-agent-wiki/agent-engineering/agentops-workbench/observability-otel
created: 2026-09-09
source: "https://docs.langchain.com/langsmith/evaluation"
---

# LangSmith — Reuse vs Build

> **The general engineering rule is "reuse, don't rebuild".** LangSmith is the concrete decision: do you adopt its dataset / evaluator / experiment-run abstractions, or build your own? The proposal's *optional* LangSmith export is the right framing — even if the final experiment UI is in-house, the evaluator abstraction is the reference shape.

## The pitch (60 seconds)

LangSmith provides three capabilities that matter for any serious agent evaluation: **datasets** (versioned collections of inputs + expected outputs), **evaluators** (Python functions or LLM-as-judge prompts that score outputs), and **experiment runs** (a recorded execution of an evaluator over a dataset, with diffing across runs). When the question is "do we adopt this", the answer is usually *yes for the abstractions, maybe not for the hosted UI* — the abstractions are the durable shape; the UI is replaceable.

## The three abstractions

**1. Datasets.** A versioned collection of (input, expected_output, metadata) triples. The dataset has a stable ID; updates create new versions; experiments pin to a specific version. This is the proposal's `freeze-before-tuning` rule made concrete: a dataset hash is the freezing mechanism.

**2. Evaluators.** Functions that take (input, output, expected_output) and return a score. Two flavors:
- **Code evaluators** — deterministic checks: regex match, JSON-schema validation, exact equality, BLEU/ROUGE, custom Python. The proposal's "deterministic, no-human-in-the-loop outcome check" is exactly this.
- **LLM-as-judge evaluators** — a prompt + (optionally) a reference output; the LLM returns a structured verdict. The proposal's "isolated LLM judge scores groundedness on a human-reviewed subset" is exactly this.

**3. Experiment runs.** A recorded execution: "ran evaluator X over dataset Y version Z at timestamp T, results are in". Diffing across runs (run A vs run B) is the comparison surface. The proposal's `prompt_version` field is the experiment axis.

## What to reuse vs build

**Reuse (high confidence):**
- The **dataset** abstraction. Your data lives somewhere already; LangSmith's wrapper gives you versioning + lineage + diffing for free.
- The **evaluator** abstraction. Even if you write your own scoring code, framing it as an "evaluator" makes it composable.
- The **experiment run** abstraction. The recording / diffing pattern is hard to build well; not worth rebuilding.

**Maybe build (depends on team):**
- The **hosted UI**. If your team has strong opinions about experiment dashboards, in-house may win. If not, the hosted UI is the path of least resistance.
- The **trace storage**. If you're already on a Datadog / Honeycomb / Grafana Cloud backend, LangSmith's traces may duplicate what you have. See [[observability-otel|Observability]] for the cross-provider schema question.

**Don't build (almost always):**
- Your own dataset-versioning system. The hard parts (lineage, diffing, immutability, audit) are exactly the parts LangSmith has already amortized.

## What to defend in the interview

| Claim | Defense |
|---|---|
| "Why LangSmith specifically?" | It's the canonical LangChain/LangGraph-native eval platform; it has the abstractions that match the proposal's evaluation design; the abstractions are usable independently of the hosted UI. |
| "Why not roll our own?" | Dataset versioning + evaluator framework + experiment diffing is a multi-engineer-year investment; LangSmith has already amortized it across thousands of users. |
| "What about vendor lock-in?" | The abstractions (datasets, evaluators, runs) are *patterns*, not vendor-specific. If you adopt them, you can swap the implementation later; if you don't, you'll reinvent them. |
| "What would you host vs buy?" | The hosted UI is the most replaceable. The dataset format and the evaluator API are the most durable. Design your integration to depend on the API, not the UI. |
| "How do you keep the LLM-as-judge honest?" | Restrict it to a human-reviewed subset; never let it gate production; track agreement with humans over time (the ~80% finding from MT-Bench). See [[evaluation|Evaluation Methodology]]. |

## Anti-patterns to name

- **"We'll build our own eval framework."** The dataset / evaluator / experiment abstractions are well-understood; building your own is months of work for no differentiation.
- **Adopting the UI but not the abstractions.** You end up with a hosted dashboard over a dataset format you can't export. Adopt the abstractions; swap the UI as needed.
- **LLM-as-judge as a gate.** The judge is a signal, not a gate. Restrict to a human-reviewed subset; humans make the call.
- **No dataset versioning.** Without versioning, "did this get better" becomes "did we accidentally train on the eval".
- **Ignoring the trace data.** LangSmith (and OpenLLMetry) emit traces that are useful for debugging the evaluator itself. A regressing eval score is often a traceable bug.

## Where this connects

- **Evaluation** ([[evaluation]]) — LangSmith is the concrete implementation of the abstract methodology in the previous leaf.
- **Observability** ([[observability-otel]]) — LangSmith traces use the same GenAI semconv attributes; the trace data is portable to any OTLP backend.

## Sources

- [LangSmith evaluation docs](https://docs.langchain.com/langsmith/evaluation) — datasets, evaluators, experiment runs

## Related

- [[_index|agentops-workbench sub-hub]] — the 7-leaf preparation track
- [[../_index|Agent Engineering major hub]] — career-positioning view
- [[evaluation|Evaluation Methodology]] — the methodology leaf; LangSmith is the implementation
- [[observability-otel|Observability — OpenTelemetry for Agents]] — the trace schema both share
