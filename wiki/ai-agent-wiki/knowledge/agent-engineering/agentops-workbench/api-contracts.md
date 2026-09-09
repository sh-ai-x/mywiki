---
tags: ["agent-engineering", "agentops-workbench", "api-contracts", "openapi", "swagger", "json-rpc", "interview-prep", "priority-medium"]
priority: medium
related:
  - ai-agent-wiki/agent-engineering/agentops-workbench/mcp-protocol
  - ai-agent-wiki/agent-engineering/agentops-workbench/orchestration-langgraph
created: 2026-09-09
source: "https://swagger.io/specification/"
---

# API Contracts

> **Table stakes for backend roles, rarely the focus of an agent interview** — but you need to be able to defend `POST /v1/runs`, `POST /v1/actions/{id}/approve`, and the surrounding contract in OpenAPI / Swagger or JSON-RPC terms. This leaf is the contract layer for the surfaces the other leaves touch.

## The pitch (60 seconds)

An agent service exposes three contract surfaces: a **run lifecycle** API (create run, get run, list runs), a **human-in-the-loop** API (list pending actions, approve/reject action), and a **tool-call** API (which may itself be MCP — see [[mcp-protocol|MCP]]). Each surface is a typed contract: explicit request/response schemas, explicit error types, explicit auth. OpenAPI / Swagger for HTTP; JSON-RPC 2.0 for MCP. The interview question is rarely "what is OpenAPI?" — it's "where does the contract live, who owns it, and how do you evolve it without breaking consumers?".

## The contract surfaces

### 1. Run lifecycle

- **`POST /v1/runs`** — create a run. Body: `{ "agent_id": "...", "input": {...}, "metadata": {...} }`. Returns: `{ "run_id": "...", "status": "queued" }`.
- **`GET /v1/runs/{id}`** — get run state. Returns: full state machine status, current node, elapsed time, error if any.
- **`GET /v1/runs?agent_id=...&status=...&limit=...`** — list runs. For ops dashboards.
- **`POST /v1/runs/{id}/cancel`** — cancel a running run.

### 2. Human-in-the-loop

- **`GET /v1/runs/{id}/actions`** — list pending actions requiring approval. Returns: list of action objects with id, type, target tool, canonical args, expiry, nonce.
- **`POST /v1/actions/{id}/approve`** — approve a pending action. Body: `{ "approver": "user_id", "justification": "..." }`. Returns: 200 if approved, 409 if action already consumed or expired.
- **`POST /v1/actions/{id}/reject`** — reject a pending action. Same shape.
- **`POST /v1/actions/{id}/expire`** — admin-only; manually expire an action.

The approval endpoint binds (user, run, tool, canonical args, expiry, nonce). The HTTP signature `POST /v1/actions/{id}/approve` carries the action ID; the body carries the approval payload; the server validates the binding against the ledger before persisting. See [[reliability-durable-effects|Reliability]] for why the binding matters.

### 3. Tool-call (MCP)

If the agent calls MCP servers, the tool-call surface is JSON-RPC 2.0 over stdio (local) or HTTP+SSE / streamable HTTP (remote). The MCP 2025-06-18 authorization layer wraps the JSON-RPC framing; see [[mcp-protocol|MCP]] for the full story.

### 4. Telemetry

- **`POST /v1/runs/{id}/traces`** — submit a trace batch (or use OTLP directly to your backend).
- **`GET /v1/runs/{id}/spans`** — read spans for a run. See [[observability-otel|Observability]] for the GenAI semconv schema.

## The contract itself

OpenAPI 3.x is the standard. The full spec lives in a YAML/JSON file in the repo; CI validates that the implementation matches the spec (e.g., via `schemathesis`, `dredd`, or `openapi-validator`). Breaking changes require a new API version (`/v2/...`); non-breaking additions (new optional fields, new endpoints) can be added without a version bump.

For MCP servers, the contract is the MCP spec revision line (`2025-06-18`). The capabilities and tool schemas are part of the contract.

## What to defend in the interview

| Claim | Defense |
|---|---|
| "Why a typed contract?" | Type errors are caught at the boundary, not deep in the agent. Schemas are documentation; schemas generate clients; schemas enable contract tests in CI. |
| "How do you evolve the contract?" | Non-breaking additions: new optional fields, new endpoints. Breaking changes: new API version, dual-support window, deprecation timeline, migration guide. |
| "Why bind (user, run, tool, args, expiry, nonce) on approval?" | The HTTP endpoint is replayable; the binding is what prevents replay abuse. See [[reliability-durable-effects|Reliability]]. |
| "OpenAPI vs JSON-RPC?" | OpenAPI for synchronous HTTP APIs (the run lifecycle, the approval surface); JSON-RPC for MCP tool calls (which need capability negotiation and streaming). |
| "Where does the schema live?" | In the repo as a YAML file; validated in CI; consumed by the client generator; the source of truth for the contract test suite. |

## Anti-patterns to name

- **No contract file.** The "contract" lives in someone's head; the implementation drifts; consumers break silently.
- **No contract tests.** The implementation diverges from the spec; the divergence ships; consumers see unexpected behavior.
- **Breaking changes without versioning.** Add a field to a request — clients that don't expect it may break. Bump the version; support both during migration.
- **HTTP status codes as a substitute for typed errors.** A 200 with `{ "error": "..." }` body is not a typed error; it's a poorly-typed success. Use 4xx/5xx with a structured error schema.
- **Approval endpoints that don't bind canonical args.** A POST that approves "anything the agent is about to do" is a vulnerability, not a feature. Bind (user, run, tool, args, expiry, nonce).

## Where this connects

- **MCP** ([[mcp-protocol]]) — the tool-call contract surface; JSON-RPC 2.0 over stdio or HTTP.
- **Orchestration** ([[orchestration-langgraph]]) — the run lifecycle wraps the LangGraph state machine; the approval endpoint wraps `Command(resume=...)`.

## Sources

- [OpenAPI / Swagger specification](https://swagger.io/specification/) — primary reference for HTTP contract definitions

## Related

- [[_index|agentops-workbench sub-hub]] — the 7-leaf preparation track
- [[../_index|Agent Engineering major hub]] — career-positioning view
- [[mcp-protocol|MCP — Protocol Contract and Authorization]] — the JSON-RPC 2.0 contract surface for tool calls
- [[orchestration-langgraph|Orchestration — LangGraph, HITL, Checkpointing]] — the state machine that the run lifecycle wraps
- [[reliability-durable-effects|Reliability and Durable Effects]] — the binding rules for approval endpoints
