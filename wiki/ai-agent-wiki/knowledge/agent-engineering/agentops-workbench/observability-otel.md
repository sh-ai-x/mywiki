---
tags: ["agent-engineering", "agentops-workbench", "observability", "opentelemetry", "otel", "gen-ai-semconv", "tracing", "interview-prep", "priority-high"]
priority: high
related:
  - ai-agent-wiki/agent-engineering/agentops-workbench/evaluation
  - ai-agent-wiki/agent-engineering/agentops-workbench/reliability-durable-effects
  - ai-agent-wiki/agent-engineering/agentops-workbench/orchestration-langgraph
  - ai-agent-wiki/core-ai-security/specialized/detection-monitoring
created: 2026-09-09
source: "https://opentelemetry.io/docs/specs/semconv/gen-ai/"
---

# Observability — OpenTelemetry for Agents

> **The shared attribute schema for production agent traces in 2026 is OpenTelemetry GenAI semantic conventions.** If the interviewer asks "how do you debug an agent at 3am?", the answer is: structured traces with `gen_ai.*` attributes, span conventions for chat / text-completion / embeddings, and a separate content-capture policy that hooks into trace redaction. The reference implementation is OpenLLMetry.

## The pitch (60 seconds)

Agents emit telemetry, but until OpenTelemetry GenAI semantic conventions stabilized, every framework invented its own. **GenAI semconv** is the shared attribute schema: `gen_ai.system` (the provider), `gen_ai.request.model`, `gen_ai.usage.input_tokens`, `gen_ai.usage.output_tokens`, plus span kinds for `gen_ai.chat`, `gen_ai.text_completion`, `gen_ai.embeddings`, and chat-message events. OpenLLMetry (Traceloop) is the reference implementation mapping ≥ 50 providers to these conventions. The conventions explicitly separate header-level telemetry from *content capture* — the policy hook for trace redaction.

## Why a shared schema matters

Without a shared schema:
- Vendor A emits `model.name`; vendor B emits `model_id`; vendor C emits `llm.model`.
- A dashboard query "show me all calls that used GPT-4o and cost > $1" is impossible to write without per-vendor translation.
- Anomaly detection across providers requires per-vendor feature engineering.

With GenAI semconv, the same query works across OpenAI, Anthropic, Google, Bedrock, Vertex, and self-hosted models — and the dashboard, alert, and audit-log code is the same.

## The core attributes (GenAI semconv)

- **`gen_ai.system`** — provider identifier (`openai`, `anthropic`, `azure.ai.openai`, `vertex.ai`, `bedrock`, etc.).
- **`gen_ai.request.model`** — the model name as the *user* requested it (e.g., `gpt-4o-mini`).
- **`gen_ai.response.model`** — the model name as actually used (may differ after fallback).
- **`gen_ai.request.temperature`**, `top_p`, `max_tokens`, `stop_sequences` — sampling parameters.
- **`gen_ai.usage.input_tokens`**, `output_tokens` — token counts.
- **`gen_ai.chat` / `gen_ai.text_completion` / `gen_ai.embeddings`** — span kind.
- **`gen_ai.choice`** — index of the choice in a multi-choice response.
- **Chat-message events** — `gen_ai.user.message`, `gen_ai.assistant.message`, `gen_ai.system.message`, `gen_ai.tool.message` — span events carrying the actual messages.

## The content-capture / redaction hook

The conventions explicitly separate *header-level telemetry* (always captured) from *content capture* (opt-in, separately controlled). This is the policy hook:

- **Header-level** is always on: model name, token counts, latency, finish reason, tool-call name. Required for cost attribution, anomaly detection, SLO tracking.
- **Content capture** is opt-in: prompt text, completion text, tool-call arguments. Required for debugging specific failures and for evaluation pipelines.

The policy decision: who can turn content capture on? What retention? What redaction (PII, secrets, system prompts)? The conventions don't decide this; they make the decision possible to enforce. Cite this when the interviewer asks "what about PII in traces?" — the schema is the lever for the policy.

## OpenLLMetry — the reference implementation

OpenLLMetry (Traceloop, GitHub: `traceloop/openllmetry`) is the reference implementation that maps ≥ 50 providers (OpenAI, Anthropic, Cohere, Bedrock, Vertex, Mistral, HuggingFace, Replicate, etc.) to GenAI semconv. Drop-in instrumentation for Python, TypeScript, Java, Go. Outputs to any OTLP-compatible backend (Jaeger, Tempo, Honeycomb, Datadog, New Relic, Grafana Cloud).

Use OpenLLMetry as the *known-good exporter* when integrating a new agent framework. Saves you from re-implementing the provider mapping.

## What to defend in the interview

| Claim | Defense |
|---|---|
| "Why OpenTelemetry?" | Vendor-neutral; OTLP is the de facto wire format; the same spans flow to any backend. No vendor lock-in. |
| "Why GenAI semconv and not your own schema?" | Cross-provider queries work out of the box; dashboard / alert code is portable; new provider? Plug in the OpenLLMetry mapping, no schema change. |
| "Why separate header-level from content capture?" | The header-level telemetry is needed for cost / SLO / anomaly detection regardless of policy. Content capture is sensitive (PII, secrets, system prompts) and needs a separate policy lever. |
| "How do you handle redaction?" | Span processors that scan content-capture fields and redact before export. List of regex patterns for known PII / secret shapes; LLM-as-judge for ambiguous cases; explicit opt-in for full-content retention (debugging only). |
| "How do you debug a specific failure?" | Find the trace by `gen_ai.request.model`, `gen_ai.choice`, or user/session ID; walk the span tree from root to leaf; inspect the content-capture events. |

## Anti-patterns to name

- **One schema per provider.** The dashboard query is unmaintainable; cross-provider anomaly detection requires per-provider feature engineering.
- **Always-on content capture.** PII leaks into traces; compliance nightmare. Turn it on per-environment, per-team, per-debug-session — never as a default.
- **No retention policy.** Traces live forever; storage grows unbounded; old traces contain old PII. Set a retention window (90 days for header-level, 30 days for content capture is a common starting point).
- **Spans without `gen_ai.*` attributes.** Custom spans are fine for the agent-specific nodes; the LLM call spans must carry GenAI semconv attributes or the cross-provider view breaks.
- **Logging instead of tracing.** `print()` calls and JSON logs are not a substitute for spans with parent-child relationships and structured attributes. You can't reconstruct a failed agent run from logs alone.

## Where this connects

- **Evaluation** ([[evaluation]]) — the eval pipeline reads traces to extract completions; observability and evaluation share the same attribute schema.
- **Reliability** ([[reliability-durable-effects]]) — the trace attribute schema includes idempotency keys, ledger query results, retry counts.
- **Orchestration** ([[orchestration-langgraph]]) — LangGraph nodes emit OTel spans; the checkpoint primitive should appear as a span event.
- **Security** — see [[../../core-ai-security/specialized/detection-monitoring|Detection Monitoring]] for the security angle on the same trace data (anomaly detection on tool-call patterns, prompt-injection cluster detection).

## Sources

- [OpenTelemetry GenAI semantic conventions](https://opentelemetry.io/docs/specs/semconv/gen-ai/) — stable `gen_ai.*` namespace; `gen_ai.request.model`, `gen_ai.usage.input_tokens`, `gen_ai.system`; span conventions for chat / text-completion / embeddings; chat-message events
- [OpenLLMetry (Traceloop)](https://github.com/traceloop/openllemetry) — reference implementation mapping ≥ 50 providers to GenAI semconv

## Related

- [[_index|agentops-workbench sub-hub]] — the 7-leaf preparation track
- [[../_index|Agent Engineering major hub]] — career-positioning view
- [[evaluation|Evaluation Methodology]] — eval pipelines share the same attribute schema
- [[reliability-durable-effects|Reliability and Durable Effects]] — trace attributes for idempotency keys, retry counts
- [[orchestration-langgraph|Orchestration — LangGraph, HITL, Checkpointing]] — LangGraph emits OTel spans; the checkpoint primitive should appear as a span event
- [[../../core-ai-security/specialized/detection-monitoring|Detection Monitoring]] — security angle on the same trace data
