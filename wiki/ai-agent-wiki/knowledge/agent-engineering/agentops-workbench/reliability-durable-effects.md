---
tags: ["agent-engineering", "agentops-workbench", "reliability", "exactly-once", "durable-effects", "gray-reuter", "transaction-processing", "interview-prep", "priority-high"]
priority: high
related:
  - ai-agent-wiki/agent-engineering/agentops-workbench/orchestration-langgraph
  - ai-agent-wiki/agent-engineering/agentops-workbench/evaluation
  - ai-agent-wiki/agent-engineering/agentops-workbench/observability-otel
created: 2026-09-09
source: "https://www.cs.brown.edu/courses/cs227/Readings/p761-gray.pdf"
---

# Reliability and Durable Effects

> **"Exactly-once is a property of the system, not the message."** That's the one sentence to internalize; the rest of this leaf is the citation chain. The classic source is Gray & Reuter's *Transaction Processing: Concepts and Techniques* — the same textbook that justifies the proposal's *"checkpointing alone cannot guarantee exactly-once external effects; query the mock ledger before retrying"* rule.

## The pitch (60 seconds)

A durable checkpoint is *necessary* for crash recovery, but it is *not sufficient* for exactly-once external effects. Between the checkpoint commit and the external tool call, the process can crash; on restart, the agent replays and re-invokes — duplicating the external effect (a second email sent, a second payment posted, a second row inserted). The fix is **idempotency keys + query-the-ledger-before-retry** — exactly the pattern Gray & Reuter describe for distributed transactions, applied to agent tool calls.

## Why checkpointing alone is insufficient

LangGraph (and every other durable-execution framework) gives you **at-least-once** execution on retry. The agent will re-run any node after a crash up to the last checkpoint, including nodes that called external tools with non-idempotent effects.

The failure shape:
1. Agent calls `send_email(to, body)`. Tool returns 200 OK. Email sent.
2. Agent about to call `mark_action_complete(id)`. Checkpoint written.
3. Process crashes between the email send and the next checkpoint.
4. On restart, agent replays from the last checkpoint, which is *before* the email send.
5. Agent calls `send_email(to, body)` again. **Email sent twice.**

The user's framing — "query the mock ledger before retrying" — is exactly the **presumed-abort** pattern from transaction processing: before committing, check the ledger; if the operation is already recorded, treat it as success and move on.

## The Gray & Reuter citation chain

**The textbook.** Gray, J. & Reuter, A., *Transaction Processing: Concepts and Techniques*, Morgan Kaufmann, 1993. The canonical source for the ACID properties, the two-phase commit protocol, the presumed-abort optimization, and the distinction between *message-level* guarantees and *system-level* guarantees.

**The relevant quotes (paraphrased):**
- "Exactly-once delivery is impossible without cooperation from the receiver."
- "The receiver must be idempotent or the sender must suppress duplicates."
- "The transaction is the unit of recovery, not the message."

Apply these to agent tool calls:
- The tool (or a wrapper around it) must be **idempotent** under a caller-supplied **idempotency key**.
- The agent must **query the ledger before retrying** — has this idempotency key been seen? If yes, return the prior result; if no, proceed.
- The **transaction** (in the agent's sense) is the chain from "started" to "effect persisted in the ledger", not just "message sent".

## What to defend in the interview

| Claim | Defense |
|---|---|
| "Why is checkpointing not enough?" | Checkpointing gives crash recovery; it doesn't give exactly-once external effects. The agent can crash between the tool call and the checkpoint, replaying the tool call. Cite Gray & Reuter on "exactly-once is a property of the system". |
| "How do you make tool calls idempotent?" | Idempotency key passed to the tool; the tool stores the key + result; on retry, the tool returns the stored result. The agent generates the key as part of the planning step, not at the call site. |
| "What's the query-the-ledger-before-retry pattern?" | Before invoking a tool with a known idempotency key, query the ledger: has this key been seen? If yes, return the prior result; if no, invoke and store. Presumed-abort optimization (Gray & Reuter). |
| "What about tools that aren't idempotent?" | Wrap them. The wrapper generates the idempotency key, calls the tool, persists the result. Or replace them with tools that are idempotent. Or scope them out of the agent (make them human-mediated). |
| "How do you test this?" | Inject crashes between tool call and checkpoint; assert the external effect happened exactly once. This is a property test, not a unit test — run it in CI. |

## Anti-patterns to name

- **"We have checkpoints, so we're safe."** Checkpoints give at-least-once; the *exactly-once* property requires idempotency keys + ledger queries.
- **Idempotency keys generated at the call site.** The key must be generated as part of the planning step (deterministic given the input), not at runtime — otherwise a retry may regenerate a different key and lose the dedup.
- **External effect without a ledger.** If the tool call writes to a system that isn't itself a ledger (e.g., a third-party API), the agent's wrapper is the ledger. Persist `(idempotency_key, result)` in your own store.
- **Trusting the HTTP 200.** A 200 means "the tool received the request", not "the effect is durable". The effect may have been written to a non-durable buffer.

## Where this connects

- **Orchestration** ([[orchestration-langgraph]]) — the checkpoint primitive is necessary; this leaf is about why it's not sufficient.
- **Evaluation** ([[evaluation]]) — "is it working?" assumes it works *reliably*; reliability is the prerequisite.
- **Observability** ([[observability-otel]]) — the audit log of "tool called with key X, returned Y, persisted to ledger" is what you trace through OTel.

## Sources

- [Gray & Reuter, *Transaction Processing: Concepts and Techniques*](https://www.cs.brown.edu/courses/cs227/Readings/p761-gray.pdf) — the textbook source for "exactly-once is a property of the system, not the message" and the query-the-ledger-before-retry pattern

## Related

- [[_index|agentops-workbench sub-hub]] — the 7-leaf preparation track
- [[../_index|Agent Engineering major hub]] — career-positioning view
- [[orchestration-langgraph|Orchestration — LangGraph, HITL, Checkpointing]] — the previous leaf; the checkpoint primitive that this leaf complements
- [[evaluation|Evaluation Methodology]] — reliability is a prerequisite to claiming "better"
- [[observability-otel|Observability — OpenTelemetry for Agents]] — the trace attribute schema for tool-call idempotency keys
