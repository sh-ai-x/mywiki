---
tags: ["ai-security", "owasp", "nist-rmf", "eu-ai-act", "mitre-atlas", "governance", "agentic-ai"]
related: ["ai-agent-wiki/00-index", "ai-agent-wiki/18-strix", "ai-agent-wiki/17-ai-agent-security", "ai-agent-wiki/strix/_index"]
created: 2026-09-08
---

# Core AI Security

> **The canonical AI-security knowledge base, organized by importance tier** — every AI engineer should know the **essential** tier; security specialists add the **practical** tier; deep-dive reference material lives in the **specialized** tier. The [[ai-agent-wiki/strix/_index|Strix sub-hub]] sits alongside (not inside) this tree as the operational backbone that exercises the whole thing.

## Importance Tiers

- [[essential/_index|Essential]] — 8 must-know leaf notes: OWASP LLM Top 10, prompt injection, jailbreaks, guardrails, action allowlisting, red-team methodology, NIST AI RMF, EU AI Act
- [[practical/_index|Practical]] — 11 implementation patterns: defense-in-depth, sandboxing, prompt hardening, retrieval filtering, training/inference defenses, monitoring, ISO 42001, CISA-NSA-FBI guidance, OWASP AI guide, implementation playbook
- [[specialized/_index|Specialized]] — 15 deep-dive reference notes: every attack class in depth, incident timeline, emerging threats, MITRE ATLAS, vendor SDKs, sector overlays

## Source Research

Each tier's research dossier lives in [[_research/]]:

- [[_research/core-ai-security-threats.md|Threats research dossier]] (feeds essential / specialized tiers)
- [[_research/core-ai-security-defenses.md|Defenses research dossier]] (feeds essential / practical tiers)
- [[_research/core-ai-security-frameworks.md|Frameworks research dossier]] (feeds essential / practical tiers)

## How to Use This Wiki

- **New to AI security?** Start with the [[essential/_index|Essential]] tier, top to bottom. Read order: OWASP LLM Top 10 → prompt injection → guardrails → action allowlisting → NIST AI RMF.
- **Implementing now?** Read [[practical/_index|Practical]] tier. The [[practical/implementation-playbook|90-day implementation playbook]] is the canonical order-of-operations.
- **Specialist / incident response?** Use the [[specialized/_index|Specialized]] tier as reference, starting from the [[specialized/incident-timeline-2023-2026|incident timeline]] for the case-class index.
- **Running Strix against this knowledge base?** The [[ai-agent-wiki/strix/_index|Strix sub-hub]] (sibling wiki, not under this tree) covers threat coverage, CI integration, and using Strix output as a defense signal.

## Related

- [[ai-agent-wiki/00-index|AI Agent Wiki Index]] — master catalog
- [[ai-agent-wiki/18-strix|Strix (18)]] — canonical Strix product page
- [[ai-agent-wiki/17-ai-agent-security|AI Agent 보안 (17)]] — IR playbooks and threat models for agent deployments
- [[ai-agent-wiki/19-context-aware-pentesting|Context-Aware Pentesting (19)]] — Strix's persistent threat-model layer
- [[ai-agent-wiki/strix/_index|Strix sub-hub]] — threat coverage, CI integration, defense-signal patterns (sibling wiki)
