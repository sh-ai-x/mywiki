---
tags: ["owasp-llm08", "ai-security", "guardrails", "red-team", "interview-prep"]
priority: critical
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/18-strix"]
created: 2026-09-07
source: "_research/core-ai-security-defenses.md"
---

# Action Allowlisting / Least-Privilege for Agents

> The OWASP "LLM08 Excessive Agency" risk is the single largest production hazard for agentic systems. Mitigation is not a prompt-level concern; it is a code-level concern. The LLM is *untrusted* by definition; every action the agent takes must be authorized by code that does not depend on the LLM'

The OWASP "LLM08 Excessive Agency" risk is the single largest production hazard for agentic systems. Mitigation is not a prompt-level concern; it is a code-level concern. The LLM is *untrusted* by definition; every action the agent takes must be authorized by code that does not depend on the LLM's cooperation.

#### 4.1 The taxonomy of agency

OWASP LLM08 distinguishes three flavors of excessive agency:

- **Functionality** — the agent can invoke more actions than necessary (e.g., a calendar assistant that can also send email).
- **Permissions** — each invoked action has broader permissions than necessary (e.g., a read-only `query_db` tool that actually has `DROP TABLE` privileges).
- **Autonomy** — the agent can take consequential actions without human approval.

The defense is one for each: minimize the toolset, minimize the privileges per tool, and gate the consequential ones.

#### 4.2 Defense patterns

**Allowlist of actions.** The agent may invoke only a closed set of pre-declared tools, declared in code (not in the system prompt). The tool registry is the single source of truth. Dynamic tool creation is forbidden — the agent cannot add a new tool at runtime, even if the LLM "decides" to. Most agent frameworks (LangChain, LlamaIndex, CrewAI, AutoGen, Anthropic tool use, OpenAI function calling) have a tool-registration mechanism; use it to enforce the allowlist.

**Per-tool scope of authority.** Each tool call carries an explicit scope:
- `read_file(path)` may only access paths under `/workspace/`.
- `send_email(to, subject, body)` may only address recipients on a per-user allowlist; the `to` field is a controlled vocabulary.
- `query_db(sql)` is checked against a SQL parser; only `SELECT` statements are permitted; table names are checked against a per-role allowlist; row counts are capped.
- `http_fetch(url)` may only target an egress allowlist; non-allowed URLs are rewritten to a 403 page in the sandbox.
- `git_push(remote, branch)` may only push to a single `feature/*` namespace; never to `main`.

The LLM is told the scope exists; the enforcement is in code, so the LLM cannot violate it even by ignoring the system prompt.

**Reversibility tiers.** Classify every tool by reversibility and dollar-impact:
- **Tier 0 (always autonomous, fully reversible)**: read-only operations (`query_db`, `read_file`, `http_fetch`).
- **Tier 1 (autonomous, reversible within 24h)**: write to scratch space (`write_file` to `/tmp`), create draft email that waits for approval.
- **Tier 2 (autonomous, irreversible within minutes)**: send email, create issue, file PR.
- **Tier 3 (always confirm)**: delete records, transfer money, deploy to production, send to large recipient lists, post publicly.

For each tier, define the gate: Tier 0 runs without prompt; Tier 1 logs only; Tier 2 may require user confirmation; Tier 3 *always* requires user confirmation (UI button or out-of-band approval).

**Human-in-the-loop checkpoints.** A "confirmation" can be implemented as:
- A blocking prompt: the agent pauses; the user is shown the planned action and approves or rejects.
- An asynchronous approval: the agent queues the action and proceeds; a human can cancel within a time window. Useful for low-stakes autonomous loops.
- A sample-and-confirm pattern: every Nth action of a given type is shown to the user for review; the rest run silently.

UI matters: show the user the *exact* arguments, not a summary. "I'm about to send email to alice@… with subject 'Q3 results' and body '…'" not "I'm about to send a status update."

**Dry-run mode.** The first time a new action class is invoked, log the planned call without invoking the underlying API; require operator sign-off before wiring the real tool. This is the safest way to ship new agent capabilities — it forces a human to read the code path and confirm the scope is right.

**Rate and budget limits.** Per-tool call rate caps (e.g., 100 `send_email` per hour per user), token budgets per session (e.g., 1M tokens per hour), and dollar caps on paid actions (e.g., $50 of OpenAI API spend per session). Limits are checked before the tool is invoked, not after.

**Audit log.** Every tool call is logged with input, output, agent reasoning trace, the user request that triggered it, the timestamp, and the session ID. Logs are write-once and retained for at least 90 days. The audit log is the single most important artifact for post-incident review — the difference between "we have no idea what happened" and "here is the exact tool call that caused the breach" in production.

**Constitutional tool descriptions.** Each tool's description is written so the LLM knows when to call it. Review tool descriptions in the same review process as code — a vague tool description is a security bug.

#### 4.3 Agent design checklist

Before shipping an agentic system, answer:

1. What is the smallest possible set of tools? (Remove every tool you don't have a concrete use case for.)
2. For each tool, what is the *minimum* privilege required? (Read-only vs. read-write; per-row scopes; per-user scopes.)
3. For each tool, what is the reversibility tier? (Tier 0–3 as above.)
4. What is the dollar ceiling? What is the rate ceiling? What is the token budget per session?
5. What is the kill switch? (How do you disable the agent in production within seconds?)
6. What is the audit log? (Where does it go, who can read it, how long is it retained?)
7. What is the dry-run rollout plan? (When does the real tool get wired in?)
8. What is the user-facing confirmation UX? (Is the user shown the exact action?)

#### 4.4 Anti-patterns

- **"Trust the agent."** A common pattern in early agentic systems: the LLM is told "you may do anything the user asks" and tools are wide-open. This is LLM08 in its most dangerous form.
- **Cascading tool calls without checks.** The agent calls `read_file`, then `transform_data`, then `write_file`, then `git_commit`, then `git_push` — the human is asked to confirm at the end, if at all. Each step is reversible in isolation, but the cascade is not. Confirmation should be at the *commit* to the user's intent, not at the end of the chain.
- **Tool argument from free-form retrieved text.** `send_email(body=...)` where `body` is derived from a retrieved web page is the classic indirect-injection → exfiltration pipeline. Design the tool to require structured arguments, not free-form strings.
- **Tools that share credentials across users.** All users share the same API key for the downstream service, so one user's compromised agent can impersonate another. Per-user, per-action scoped credentials only.

## Related

- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — all defenses leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these defenses
