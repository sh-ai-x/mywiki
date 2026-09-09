---
tags: ["agent-engineering", "agentops-workbench", "orchestration", "langgraph", "hitl", "checkpointing", "interview-prep", "priority-critical"]
priority: critical
related:
  - ai-agent-wiki/agent-engineering/agentops-workbench/_index
  - ai-agent-wiki/agent-engineering/agentops-workbench/reliability-durable-effects
  - ai-agent-wiki/agent-engineering/agentops-workbench/observability-otel
  - ai-agent-wiki/core-ai-security/essential/action-allowlisting
created: 2026-09-09
source: "https://docs.langchain.com/oss/python/langgraph/overview"
---

# Orchestration — LangGraph, HITL, Checkpointing

> **The interview default for "how does a stateful agent work" in 2026.** LangGraph is the orchestration substrate; `interrupt()` is the human-oversight primitive; durable checkpointers are what make the agent resumable across crashes. This leaf is what you rehearse when an interviewer says *"walk me through a stateful agent"*.

## The pitch (60 seconds)

Stateful agents are **state machines, not prompt chains**. The framework is LangGraph; the nodes are actions; the edges are conditional; the durable checkpoint is what survives a restart; the human-in-the-loop pause/resume is `interrupt()` + `Command(resume=...)`. Approval gates bind *user, run, tool, canonical arguments, expiry, and one-use nonce* — never trust the resume edge alone.

## The three load-bearing primitives

**1. State machine.** LangGraph exposes the agent as a typed state graph — nodes are actions, edges are conditional, state is the typed object passed between nodes. The AgentOps Workbench proposal's state machine (`queued → running → waiting_for_approval → succeeded/failed/cancelled`) maps 1:1 to this primitive.

**2. `interrupt()` + `Command(resume=...)`.** The HITL pause/resume API. The agent throws `interrupt()` at any point; the runtime serializes the current state and pauses; a human reviews and calls `Command(resume=<value>)` to continue. This is what `POST /v1/actions/{id}/approve` in the proposal wraps.

**3. Durable checkpointer.** The runtime persists state to a backing store (Postgres, Redis, file). On crash or resume, the agent reconstructs state from the checkpoint. The checkpointer is **necessary** but **not sufficient** for exactly-once external effects — see [[reliability-durable-effects|reliability]] for that caveat.

## What the docs actually say

- **LangGraph overview** documents the runtime, state, conditional routing, and checkpoint primitives. The proposal's `Tech Stack` and `Architecture` pin LangGraph as the orchestration substrate for exactly these reasons.
- **HITL docs** document the `interrupt()` semantics and the persistent-checkpointer requirement for production. The two-step pause→resume pattern is the reference.
- **LangChain blog post on `interrupt()`** is the official rationale for the human-oversight pause/resume API and the review-action workflow.

## What to defend in the interview

| Claim | Defense |
|---|---|
| "Why a state machine, not a single prompt?" | Conditional routing is explicit; the state is inspectable; crashes are recoverable; HITL hooks are first-class. A prompt chain can't do any of these reliably. |
| "Why LangGraph over raw Python?" | State typing, checkpointing, HITL primitive, conditional edges, observability hooks — all built-in. Building these yourself is a multi-month investment that LangGraph already amortized. |
| "What about checkpointing failures?" | Async checkpointers may not flush the HITL payload until the next node runs. The fix is to bind the approval to (user, run, tool, canonical args, expiry, nonce), not to the resume edge alone. This is a LangChain-forum-acknowledged caveat, not a paper-over. |
| "How do you test the state machine?" | Replay from a checkpoint with a different `Command(resume=...)` to verify the branch; assert state shape after each node; assert that no destructive tool call ran without an interrupt-resume pair. |

## Anti-patterns to name

- **Prompt chains as state.** A long prompt with "if/then" instructions is not a state machine — it has no inspection point, no crash recovery, and no first-class HITL.
- **In-memory checkpointers in production.** Lose state on restart; the agent silently loses user approvals.
- **Trusting the resume edge without binding canonical args.** The attacker who can guess the resume shape can rerun the same tool call with the same args; binding (args, expiry, nonce) prevents this.
- **One mega-tool.** An orchestration graph with one node calling one mega-tool is just a function call. Split into typed tools with explicit scopes.

## Sources

- [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview) — runtime, state, conditional routing, checkpoint primitives
- [Human-in-the-Loop docs](https://docs.langchain.com/oss/python/langchain/human-in-the-loop) — `interrupt()` semantics, persistent-checkpointer requirement for production
- [LangChain blog on `interrupt()`](https://www.langchain.com/blog/making-it-easier-to-build-human-in-the-loop-agents-with-interrupt) — official rationale for the human-oversight pause/resume API

## Related

- [[_index|agentops-workbench sub-hub]] — the 7-leaf preparation track
- [[../_index|Agent Engineering major hub]] — career-positioning view
- [[reliability-durable-effects|Reliability and Durable Effects]] — the next leaf; "exactly-once" is a system property, not a checkpointer property
- [[../_index#sub-trees|Agent Engineering]] — sibling sub-trees
- [[../../core-ai-security/essential/action-allowlisting|Action Allowlisting]] — LLM03 Excessive Agency mitigation; the security counterpart to scoped tool calls
