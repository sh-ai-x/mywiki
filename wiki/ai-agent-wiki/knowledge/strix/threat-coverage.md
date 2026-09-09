---
tags: ["strix", "owasp", "mitre-atlas", "threat-coverage", "red-team", "ai-security"]
related: ["ai-agent-wiki/18-strix", "ai-agent-wiki/core-ai-security/essential/owasp-llm-top-10", "ai-agent-wiki/core-ai-security/specialized/mitre-atlas", "ai-agent-wiki/strix/_index"]
created: 2026-09-08
source: "_research/core-ai-security-threats.md"
---

# Strix — Threat Coverage

> **Strix exercises the application and API layer of the OWASP Top 10 and a large subset of MITRE ATLAS** — but it is not a substitute for LLM-output safety testing, infrastructure / OT pentesting, or static analysis. Use it for what it does; route the rest to [[ai-agent-wiki/core-ai-security/essential/red-team-methodology|red-team methodology]] + [[ai-agent-wiki/core-ai-security/specialized/mitre-atlas|MITRE ATLAS]]-mapped tools.

## OWASP Top 10 (App / API layer) — covered by Strix

| OWASP ID | Risk | Strix coverage | Notes |
|---|---|---|---|
| A01 | Broken Access Control | Strong | IDOR, BOLA, privilege escalation, JWT attacks — the core of Strix's identity-thesis |
| A02 | Cryptographic Failures | Indirect | Detects misuse, not implementation |
| A03 | Injection (SQLi / NoSQLi / OS cmd / SSTI) | Strong | Out-of-the-box probes + custom payloads |
| A04 | Insecure Design | Strong | Business-logic tests via PoC exploitation |
| A05 | Security Misconfiguration | Strong | Headers, CORS, debug endpoints, default creds |
| A06 | Vulnerable Components | Indirect | Limited SCA — route to dependency scanners |
| A07 | Auth Failures | Strong | Session, token, MFA bypass |
| A08 | Software & Data Integrity | Strong | Race conditions, deserialization, SSTI |
| A09 | Logging Failures | Indirect | Detects via lack of evidence in response |
| A10 | SSRF | Strong | URL-fetch probes, OOB callbacks |

## OWASP LLM Top 10 — partial coverage

Strix operates at the **application layer**; it does not directly test LLM-output safety (e.g., jailbreak resistance, PII leakage, hallucination). For those, route to:

- [[ai-agent-wiki/core-ai-security/essential/prompt-injection|Prompt Injection]] — manual + automated probes (Garak, PyRIT, promptfoo)
- [[ai-agent-wiki/core-ai-security/essential/jailbreaks|Jailbreaks]] — judge-model evaluation
- [[ai-agent-wiki/core-ai-security/specialized/adversarial-examples|Adversarial Examples]] — research-level adversarial testing

Where Strix *does* help with LLM risks:

- **LLM01 (Prompt Injection)**: indirect — Strix's findings often reveal injection-enabling paths (e.g., user input that flows unescaped into an LLM tool call)
- **LLM05 (Improper Output Handling)**: strong — Strix exploits downstream effects of an LLM call returning tainted data
- **LLM08 (Excessive Agency)**: strong — Strix's core use case; chains tool misuses to demonstrate the agent overstepped its mandate

## MITRE ATLAS — partial coverage

Strix covers a meaningful subset of ATLAS techniques, mapped below:

- **AML.T0048 — Erode ML Model Integrity**: indirectly (via app-layer exploitation)
- **AML.T0051 — LLM Prompt Injection**: partial (indirect path discovery)
- **AML.T0053 — LLM Plugin/Extension Abuse**: strong (tool-call exploitation)
- **ML Model Access tactics** (AML.TA0008 sub-techniques): strong
- **Initial Access via public-facing application**: strong

For ATLAS techniques Strix cannot reach (e.g., AML.T0020 — Poison ML Model; AML.T0043 — Craft Adversarial Data), use specialized tooling or managed services.

## What Strix does NOT cover (route these elsewhere)

- **LLM-output safety** (jailbreaks, harmful content, hallucination) → promptfoo, Garak, PyRIT
- **Infrastructure / OT / network pentest** → CAI (Cybersecurity AI), manual pentester
- **Dependency / SCA scanning** → Snyk, Dependabot
- **Static analysis (SAST)** → Semgrep, CodeQL
- **Compliance audit reporting** (SOC 2, ISO 27001) → Strix's audit-tier report covers some; full coverage still needs a CREST firm

## How to use Strix as threat coverage evidence

For an AI product team, the recommended coverage stack is:

1. **Strix** for app/API dynamic + agent tool-chain coverage (continuous)
2. **promptfoo / Garak** for LLM-output safety evals (per release)
3. **Snyk** for SCA / dependency (per build)
4. **Human red team** for novel business-logic exploits (quarterly)

Together these four cover ~85% of the OWASP App + LLM Top 10. The remaining 15% is process / governance (NIST AI RMF / ISO 42001), which the [[ai-agent-wiki/core-ai-security/essential/nist-ai-rmf|NIST AI RMF]] and [[ai-agent-wiki/core-ai-security/practical/iso-iec-42001|ISO 42001]] notes cover.

## Related

- [[ai-agent-wiki/18-strix|Strix (18)]] — canonical product page
- [[ai-agent-wiki/strix/_index|Strix sub-hub]]
- [[ai-agent-wiki/core-ai-security/essential/owasp-llm-top-10|OWASP LLM Top 10]]
- [[ai-agent-wiki/core-ai-security/specialized/mitre-atlas|MITRE ATLAS]]
