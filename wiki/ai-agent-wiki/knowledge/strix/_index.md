---
tags: ["strix", "ai-security", "red-team", "autonomous-pentest", "owasp", "agentic-ai"]
related: ["ai-agent-wiki/18-strix", "ai-agent-wiki/19-context-aware-pentesting", "ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/essential/_index"]
created: 2026-09-08
---

# Core AI Security — Strix

> **Strix is the operational backbone of the core-ai-security knowledge base** — the autonomous AI pentester that exercises the threats catalogued across the wiki's essential / practical / specialized tiers and validates the defenses.

The [[ai-agent-wiki/18-strix|Strix (18)]] leaf note is the canonical product page. The notes in this sub-directory focus on how Strix maps onto the core-ai-security knowledge base: which threats it covers, how its output maps to NIST AI RMF and OWASP controls, and how to use it inside a red-team / CI workflow.

## Leaf Notes

- [[threat-coverage|Strix threat coverage]] — which OWASP LLM Top 10 + MITRE ATLAS techniques Strix can find and validate
- [[ci-integration|Running Strix in CI]] — wiring Strix into GitHub Actions / GitLab as a security gate
- [[as-a-defense-signal|Strix output as a defense signal]] — using Strix findings to prioritize guardrail and monitoring work

## Related

- [[ai-agent-wiki/18-strix|Strix (18)]] — the canonical product leaf
- [[ai-agent-wiki/19-context-aware-pentesting|Context-Aware Pentesting (19)]] — Strix's persistent threat-model layer
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]]
- [[ai-agent-wiki/core-ai-security/essential/_index|Essential tier]]
