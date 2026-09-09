# Security and AI Security: Separate Study Tracks

These are alternatives to the main AI Agent Engineer plan. Choose a target before building. AI assisting analysts and security of AI systems require different evidence.

## Shared foundations

| Topic | Required depth | Evidence |
|---|---|---|
| Networks | DNS/TCP/TLS/HTTP, proxies, subnetting, routing, firewalls | Explain a captured request and locate a connection failure |
| OS | Linux users/permissions/processes/services/logs; Windows events for SOC | Reconstruct a login/process timeline from lab events |
| Identity | Authentication, authorization, sessions, OAuth/OIDC concepts, RBAC, service credentials | Reproduce and fix object-level authorization in a local API |
| Web security | Injection, XSS, SSRF, path traversal, CSRF, uploads | Document mechanism, evidence, remediation and regression |
| Secure engineering | Threat models, boundaries, secrets, dependencies, CI, retention | Review a small service and prioritize confirmed findings |
| Incident handling | Scope, severity, evidence, time, containment, recovery, reporting | Distinguish observations from hypotheses in a report |

Use [PortSwigger learning paths](https://portswigger.net/web-security/learning-paths) for authorized labs and [OWASP ASVS](https://owasp.org/www-project-application-security-verification-standard/) for explicit control requirements. Select a version and applicable subset; do not claim full compliance.

## Track A: SOC / Security Operations

Target alert triage, investigation and escalation. Choose this if operations and possible shift work appeal to you.

| Order | Study | Stack / artifact |
|---|---|---|
| 1 | Network/Linux/Windows event fundamentals | Wireshark and lab logs; annotated timeline |
| 2 | Normalization, correlation, detection queries | One SIEM: Wazuh or Elastic; Python parser and saved queries |
| 3 | Detection rules and benign lookalikes | Sigma concepts, rule fixtures, precision/recall on labeled lab data |
| 4 | Investigation/escalation | Five incident reports including false positives |
| 5 | Automation | FastAPI enrichment service with human decisions |

Build the SOC variant of [Security Evidence Lab](../proposals/security-evidence-lab-proposal.md). LLM summaries are optional, must cite event IDs and do not replace detection evidence.

## Track B: AppSec / Security Automation

This reuses software-building experience and is the more coherent security alternative for the supplied history. It is not automatically easier than AI engineering.

| Order | Study | Stack / artifact |
|---|---|---|
| 1 | HTTP, auth, sessions, object-level authorization | FastAPI fixture service; Burp Community/manual requests |
| 2 | Injection, SSRF, trust boundaries | Local reproductions and minimal failing tests |
| 3 | Remediation | pytest, explicit authorization, egress policy; before/after evidence |
| 4 | Supply chain/CI | One static analyzer, dependency scanner and secret scanner; triage actual results |
| 5 | Cloud/IAM fundamentals | Deployment diagram, least-privilege roles, secrets and audit events |

Build the AppSec variant of Security Evidence Lab. Confirming and repairing a bug matters more than installing scanners.

## Track C: Security of AI Agents

Prerequisites: a working tool-using agent and shared security foundations.

| Order | Study | Completion evidence |
|---|---|---|
| 1 | Direct/indirect injection, provenance, attacker scope | Threat model and harmless quoted-instruction counterexamples |
| 2 | MCP trust, descriptions, registry drift, argument validation | Versioned contracts and schema-change tests |
| 3 | Identity, confused deputy, tenant scope, approval | Direct bypass tests independent of model behavior |
| 4 | Retrieval/memory authorization, disclosure, trace privacy | Cross-user tests and pre-export seeded-secret checks |
| 5 | Budgets, retries, deadlines, sandbox/egress boundaries | Concurrency tests and documented isolation limitations |
| 6 | Attack benchmarks, useful task success, false blocking, judge manipulation | Baseline/defense comparison with raw counts and uncertainty |

Build [MCP TrustBench](../proposals/mcp-trustbench-proposal.md) as a specialization extension. Training-time attacks, adversarial vision, model-weight theft and frontier-model research are later branches with additional prerequisites.

The local [allowlisting](../wiki/ai-agent-wiki/core-ai-security/essential/action-allowlisting.md) and [defense-in-depth](../wiki/ai-agent-wiki/core-ai-security/practical/defense-in-depth-architecture.md) notes provide starting ideas. Recheck blanket claims and edition-specific IDs against primary sources. Read-only tools can disclose data.

## Preparation blocks

Estimate 2–3 weeks for shared foundations, 3–4 for one branch's lab and 1–2 for reporting/interviews, assuming part-time study and prior Python. Do not study all tracks simultaneously.

Use certifications as employer-specific filters. Check current exam rules, eligibility and target postings before paying for Security+, Korean security qualifications or practical exams. Certificates do not replace incident or remediation evidence.
