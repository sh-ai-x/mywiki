---
tags: ["ai-security", "guardrails", "red-team", "sandboxing", "interview-prep"]
priority: high
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/18-strix"]
created: 2026-09-07
source: "_research/core-ai-security-defenses.md"
---

# Monitoring

> Monitoring is the "you'll know when it breaks" layer. It does not by itself prevent an attack, but it dramatically shortens the time from attack to detection (MTTD) and the time from detection to mitigation (MTTM). A mature monitoring program is the difference between a one-day incident and a one

Monitoring is the "you'll know when it breaks" layer. It does not by itself prevent an attack, but it dramatically shortens the time from attack to detection (MTTD) and the time from detection to mitigation (MTTM). A mature monitoring program is the difference between a one-day incident and a one-month incident.

#### 9.1 Structured logging of every LLM call

Capture, for every LLM call:
- Timestamp (UTC, ms precision).
- User ID, session ID, organization ID, IP address.
- Model name and version, system prompt ID/version, tool definitions version.
- Full prompt (user message and any retrieved context).
- Full completion (or first N tokens + finish reason).
- Tool calls (name, arguments, return value, latency, success/failure).
- Latency, input/output token counts, total cost.
- All classifier scores (input classifier, output classifier, groundedness, PII detection).
- Refusal / block / confirmation events with reason.
- A unique request ID correlated through the entire stack (app → classifier → LLM → output classifier → user).

Log immutably to write-once storage (S3 with object lock, append-only databases, or a SIEM). Logs are useless if they can be edited post-incident. Retain for at least 90 days; longer for high-stakes deployments. Encrypt at rest. Restrict access to the security and on-call teams.

#### 9.2 Anomaly detection on distributions

Track per-hour (or per-15-minute) distributions of:
- **Refusal rate.** A sudden drop suggests the classifier thresholds are misconfigured or the model has been downgraded. A sudden spike suggests a new attack campaign.
- **Input classifier scores.** Sudden shift in the distribution of harm scores suggests adversarial traffic.
- **Prompt length and token counts.** Sudden shift suggests long-context flood attacks (LLM04).
- **Tool call patterns.** A new tool class appearing, or a sudden spike in one tool, suggests a new attack or a model regression.
- **Geographic distribution.** A sudden shift in source-country distribution suggests credential stuffing or a regional attack campaign.
- **Latency and error rates.** Operational signals that also catch DoS attacks.

Run standard time-series anomaly detection (Page-Hinkley, EWMA control charts, or a learned model like a Prophet or LSTM forecaster). Alert on a 3-sigma deviation from the rolling baseline.

#### 9.3 Canary tokens and honey prompts

**System-prompt canary.** A unique secret nonce embedded in the system prompt, e.g., `INTERNAL_TOKEN_ORG_XYZ_DO_NOT_DISCLOSE_8a4f2c`. The nonce is per-deployment. Alert (page on-call) if the nonce ever appears in:
- User-visible output (the user is exfiltrating your system prompt).
- Any tool-call argument (the LLM is being steered to pass the nonce somewhere observable).
- A web fetch of an external service (the LLM is being used as a confused deputy).
- Any third-party dataset (a leakage path was discovered).

A canary firing is a high-confidence signal of prompt exfiltration. Treat as a security incident.

**Honey prompts / canary user accounts.** Synthetic user accounts and synthetic prompts seeded into the wild:
- Synthetic users with very identifiable names ("canary-user-1") that no real user would claim; alert if any LLM response is associated with these users.
- Synthetic documents in retrieval indexes with unique tokens; alert if the tokens appear in responses.
- Synthetic API keys issued to fake services; alert if the keys are ever used.

Honey prompts catch leakage paths that synthetic tests miss.

#### 9.4 Rate and pattern alarms

- **Brute-force jailbreak detection.** A single user/IP producing many refusals in a short window. Possibly an automated jailbreak campaign.
- **Data-exfiltration pattern detection.** Unusually long completions; many tool calls to external hosts in a single session; large tool-call argument payloads.
- **Resource exhaustion (LLM04).** Long-context floods (single prompt > 1M tokens); recursive tool loops (the agent calls the same tool repeatedly without making progress); expensive model calls in a tight loop.
- **Prompt-injection clusters.** Multiple users independently submitting the same (or near-same) prompt — likely a shared injection payload.
- **Geographic anomalies.** A user authenticating from a country they have never used before.

#### 9.5 Eval-set regression alarms

A small, fast-running set of ~100–500 prompts that cover the most common known failure modes. Run it continuously against production (e.g., every 15 minutes, or on a sampled fraction of traffic):
- A *known-bad* prompt that starts succeeding — the safety classifier has regressed or the model has been downgraded. Page on-call.
- A *known-good* prompt that starts failing — the model has regressed on capability, possibly a quality issue rather than a safety issue. Page the model team.

The eval set is a tripwire — its job is to fail fast when something has changed. It does not need to be exhaustive; it just needs to be sensitive to the changes you most care about.

#### 9.6 Source citation integrity (for RAG)

For RAG systems, monitor:
- The rate at which cited source snippets actually exist in the retrieval index. A spike in "cited but not found" suggests prompt-injection success or retrieval-index corruption.
- The distribution of source domains in cited snippets. A new domain appearing as a major source suggests a poisoning attack or a corrupted index.
- The age of cited sources. A spike in old or new sources can indicate a poisoning event.

#### 9.7 Drift detection

- **Model drift.** A new model version may have subtly different safety properties. Run the eval set on every model upgrade; compare distributions of refusal rates and classifier scores against the previous model.
- **Traffic drift.** User behavior changes over time; the model may start seeing more sensitive use cases. Monitor the distribution of use-case tags (from a topic classifier) and flag when a sensitive category spikes.
- **Concept drift.** For RAG, the meaning of terms in the corpus may change (e.g., a new product launch makes old documents obsolete). Monitor embedding-space distributions over time.

#### 9.8 Alerting and response

Define an on-call rotation, alert routing, and runbook for each class of alert. The runbook should specify:
- What the alert means.
- How to confirm it is a real incident (vs. a false positive).
- The first three actions to take.
- Who to escalate to.
- How to communicate to users and regulators if needed.

An alert without a runbook is a problem, not a feature. Most "alert fatigue" comes from alerts that page humans but don't tell humans what to do.

## Related

- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — all defenses leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these defenses
