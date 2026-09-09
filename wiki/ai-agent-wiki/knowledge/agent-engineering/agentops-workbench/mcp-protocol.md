---
tags: ["agent-engineering", "agentops-workbench", "mcp", "model-context-protocol", "oauth-2.1", "pkce", "json-rpc", "interview-prep", "priority-critical"]
priority: critical
related:
  - ai-agent-wiki/agent-engineering/agentops-workbench/orchestration-langgraph
  - ai-agent-wiki/agent-engineering/agentops-workbench/api-contracts
  - ai-agent-wiki/core-ai-security/essential/owasp-llm-top-10-2026
created: 2026-09-09
source: "https://modelcontextprotocol.io/specification/2025-06-18/authorization"
---

# MCP — Protocol Contract and Authorization

> **MCP is the 2026 standard for agent ↔ tool integration.** If an interviewer asks "how does your agent talk to a tool?", the answer is "Model Context Protocol, JSON-RPC 2.0 transport, OAuth 2.1 with mandatory PKCE and resource indicators, with the protocol revision pinned to 2025-06-18." Anything less is a hand-wave.

## The pitch (60 seconds)

MCP is a host/client/server protocol with three primitives — **Tools**, **Resources**, **Prompts** — over JSON-RPC 2.0, with capability negotiation at session start. Authorization is OAuth 2.1 with **mandatory PKCE** and **resource indicators** (RFC 8707) to prevent confused-deputy token reuse. The protocol revision line (currently `2025-06-18`) is what makes "documented protocol requirements" defensible in a procurement review.

## The architecture

```
┌─────────┐         ┌─────────┐         ┌─────────────┐
│  Host   │  ┌────┐ │ Client  │  JSON-  │ MCP Server  │
│ (app)   │◄─┤MCP │◄►│ (per-srv│  RPC    │ (tools,     │
│         │  │ stdio│ │         │  2.0    │  resources, │
│         │  │   │ │         │         │  prompts)   │
└─────────┘  └────┘ └─────────┘         └─────────────┘
```

- **Host** — the user-facing application (Claude Desktop, your agent app, an IDE).
- **Client** — a per-server connection inside the host; speaks JSON-RPC 2.0.
- **Server** — exposes Tools (actions), Resources (data), Prompts (templated text).

Two transports matter:
- **stdio** for local controlled services (the agent launches the server as a subprocess; no network).
- **HTTP + SSE / streamable HTTP** for remote services; this is where the OAuth 2.1 story lives.

## Capability negotiation

At session start, the server declares its capabilities (which primitives it supports, what schemas it exposes), and the client declares its capabilities (which it can consume). This is what makes MCP a *protocol* rather than a tool convention — both sides know what the other supports without hard-coding.

The proposal's "documented protocol revision" requirement is precisely this: the protocol's negotiated capabilities are pinned to a specific revision, so behavior is reproducible across versions.

## Authorization — OAuth 2.1 (2025-06-18)

The MCP 2025-06-18 revision adopts **OAuth 2.1** as the authorization model. The three load-bearing requirements:

1. **Mandatory PKCE** (RFC 7636) — required for all clients, including the "public client" case the agent falls into when there is no client secret.
2. **Resource indicators** (RFC 8707) — the access token is bound to a specific MCP server's resource identifier. This is the **confused-deputy fix**: a token issued for server A cannot be replayed against server B, even if both are hosted at the same authorization server.
3. **Audience binding** — the access token's `aud` claim is bound to the specific MCP server; the server rejects tokens issued for other audiences.

Plus metadata, discovery, and (for confidential-resource servers) token introspection.

## What to defend in the interview

| Claim | Defense |
|---|---|
| "Why MCP and not just OpenAPI?" | OpenAPI describes HTTP APIs; MCP describes *agent-useful* capabilities (Tools/Resources/Prompts) with capability negotiation, schema validation, and standardized error types. Discovery, schema validation, timeout, malformed results, unsupported capabilities, server disconnect are well-defined MCP failure modes — not custom error types. |
| "Why OAuth 2.1 and not 2.0?" | OAuth 2.1 consolidates the post-2017 security recommendations (PKCE everywhere, no implicit grant, no resource owner password grant, etc.) into one spec. For an agent client, mandatory PKCE matters because the agent has no client secret. |
| "Why pin the revision to 2025-06-18?" | MCP is a moving target; 2024-11 drafts did not mandate PKCE or resource indicators. Pinning the revision is the only way to make "documented protocol requirements" defensible in a procurement review. |
| "Why stdio vs HTTP?" | stdio for local controlled services (no network surface, OS-level isolation); HTTP for remote shared services (where the OAuth 2.1 story earns its keep). Mixing them under one protocol keeps the agent code uniform. |

## Failure modes to name

- **Discovery failure** — server doesn't expose the capability the client asked for. Defined error, not a crash.
- **Schema validation failure** — tool call arguments don't match the server-declared schema. Rejected before execution.
- **Timeout** — call exceeds the per-method timeout. The client must surface a defined error, not hang.
- **Malformed result** — server returns JSON-RPC that doesn't parse. Defined error, not a panic.
- **Unsupported capability** — client asks for a method the server doesn't support. Defined error.
- **Server disconnect** — transport drops mid-session. Client must reconnect and re-negotiate.

These are well-defined MCP failure modes (per the JSON-RPC 2.0 framing), not custom error types — cite this when the interviewer asks "what about errors?".

## Sources

- [MCP architecture overview](https://modelcontextprotocol.io/docs/learn/architecture) — host/client/server, Tools/Resources/Prompts, JSON-RPC 2.0 transport, capability negotiation
- [MCP 2025-06-18 authorization draft](https://modelcontextprotocol.io/specification/2025-06-18/authorization) — OAuth 2.1, mandatory PKCE, resource indicators (RFC 8707), audience binding
- [The New Stack: MCP gets OAuth 2.1-based authorization](https://thenewstack.io/mcp-gets-oauth-2-1-based-authorization-what-you-need-to-know/) — change summary and migration notes
- [Auth0: MCP OAuth 2.1 changes](https://auth0.com/blog/mcp-oauth-2-1-changes/) — PKCE, resource-server metadata, token introspection
- [JSON-RPC 2.0 specification](https://json-rpc.readthedocs.io/) — underlying framing

## Related

- [[_index|agentops-workbench sub-hub]] — the 7-leaf preparation track
- [[../_index|Agent Engineering major hub]] — career-positioning view
- [[orchestration-langgraph|Orchestration — LangGraph, HITL, Checkpointing]] — the previous leaf; the orchestration runtime that *calls* MCP tools
- [[api-contracts|API Contracts]] — OpenAPI / Swagger; the contract layer for non-agent APIs that MCP servers may wrap
- [[../../core-ai-security/essential/owasp-llm-top-10-2026|OWASP LLM Top 10 2026]] — LLM03 Excessive Agency and LLM04 Supply Chain are the security angles on the same surface
