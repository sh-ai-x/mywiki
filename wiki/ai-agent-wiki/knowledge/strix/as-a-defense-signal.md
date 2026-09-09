---
tags: ["strix", "guardrails", "monitoring", "defense-signal", "ai-security"]
related: ["ai-agent-wiki/18-strix", "ai-agent-wiki/strix/_index", "ai-agent-wiki/core-ai-security/essential/guardrails", "ai-agent-wiki/core-ai-security/practical/monitoring", "ai-agent-wiki/core-ai-security/practical/defense-in-depth-architecture"]
created: 2026-09-08
---

# Strix — Output as a Defense Signal

> **A Strix finding is not just a bug report — it is a prior on which defenses need hardening** — the issue class Strix found tells you which guardrail layer to invest in next, and the PoC gives you the test case for that guardrail's eval suite.

## The signal-mapping pattern

When Strix reports a finding, the natural follow-up is **"which layer in my defense-in-depth stack should have caught this?"** Use the table below to map the finding to the right control:

| Strix finding class | Likely-defense-layer gap | Action |
|---|---|---|
| IDOR / BOLA (A01) | Authentication or authz middleware | Add an automated BOLA test in CI; route to authz-team |
| SSRF (A10) | Outbound URL allowlist (L5) | Add the URL class to the egress allowlist or block at the proxy |
| SQL/NoSQL injection (A03) | Input validation or parameterized queries | Add the payload to a regression test against the ORM's prepared-statement enforcement |
| Missing auth (A07) | Middleware | Standard auth-template enforcement; add to monitoring as a 401-rate alert |
| Race condition (A08) | DB-level locking or idempotency keys | Add concurrency test; alert on suspicious traffic |
| Tool-misuse (LLM08) | Action allowlist (L5) | Add the action class to the allowlist with explicit scope; require human-in-loop for first invocation |
| Indirect prompt injection vector | Retrieval filtering (L3) | Add the source class to the per-source trust label; route to [[ai-agent-wiki/core-ai-security/practical/retrieval-filtering|Retrieval Filtering]] |

## Building a Strix-driven guardrail feedback loop

The recommended operating pattern is:

1. **Nightly Strix run** in full mode against staging
2. **Triage + dedup** findings vs. prior runs (Strix flags re-occurrences automatically)
3. **For each new high-severity class**, open a defense-investigation ticket with:
   - The Strix PoC
   - The target layer that should have caught it (per the table above)
   - The owner (the team that owns the layer)
4. **Within 30 days**, the team ships a guardrail improvement + a regression test using the Strix PoC as the eval case
5. **Re-run Strix**; the issue should no longer reproduce

This loop has two properties that matter:

- **It compounds**: every iteration makes the next Strix run cleaner, which makes the next triage faster, which makes the next defense investment cheaper
- **It produces a measurable signal**: the count of new high-severity findings per month is the KPI for "is our defense-in-depth actually getting better?"

## Anti-patterns to avoid

- **Treating Strix findings as one-off bug tickets** without mapping them to a defense layer → fires the same finding class every week
- **Closing findings as "won't fix" without a defense-layer annotation** → loses the signal that the layer is missing
- **Running Strix in CI but ignoring the output** (only present to satisfy a compliance checkbox) → the most expensive way to not use Strix

## KPIs to track

- **Time-to-fix-by-class**: median time from a Strix finding of class X to a regression test in CI for that class
- **Re-occurrence rate**: fraction of high-severity findings that re-appear in the next Strix run after being marked "fixed"
- **Defense-layer coverage**: for each layer (L1-L7 in the [[ai-agent-wiki/core-ai-security/practical/defense-in-depth-architecture|Defense-in-Depth Architecture]]), what fraction of Strix finding classes has an associated guardrail eval

## Related

- [[ai-agent-wiki/18-strix|Strix (18)]] — canonical product page
- [[ai-agent-wiki/strix/_index|Strix sub-hub]]
- [[ai-agent-wiki/core-ai-security/essential/guardrails|Guardrails]]
- [[ai-agent-wiki/core-ai-security/practical/monitoring|Monitoring]]
- [[ai-agent-wiki/core-ai-security/practical/defense-in-depth-architecture|Defense-in-Depth Architecture]]
