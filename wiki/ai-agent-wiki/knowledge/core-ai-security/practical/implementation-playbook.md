---
tags: ["ai-security", "eu-ai-act", "governance"]
priority: medium
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/00-index"]
created: 2026-09-07
source: "_research/core-ai-security-frameworks.md"
---

# Implementation Playbook

> A practitioner-oriented guide to actually rolling out AI security and governance in an organization. Not derived from any single framework; synthesized from the above

A practitioner-oriented guide to actually rolling out AI security and governance in an organization. Not derived from any single framework; synthesized from the above.

#### 10.1 Maturity model

Most organizations move through five levels:

- **Level 0 — Ad hoc.** AI is used informally; no inventory; no policy; no controls. Common in organizations that "let developers try ChatGPT." Risk: high.
- **Level 1 — Aware.** A central function (often IT, security, or legal) is aware of AI use; an inventory exists in spreadsheets; some shadow-AI blocking on the network. Risk: moderate.
- **Level 2 — Governed.** Formal AI policy; documented risk register; approval process for new AI deployments; tiered controls by risk class. Risk: managed for known deployments; shadow AI remains.
- **Level 3 — Measured.** Continuous measurement of AI risk via evals, audits, and metrics; AI risks integrated into the enterprise risk framework; incidents tracked and learned from. Risk: actively managed.
- **Level 4 — Optimized.** AI risks are proactively anticipated; controls are tested adversarially; governance is a competitive advantage. Risk: minimized; AI is deployed confidently with bounded risk.

Most regulated enterprises (financial services, healthcare, federal contractors) are required to be at Level 2–3. Level 4 is the state of the art at leading AI labs and a handful of large enterprises.

#### 10.2 Getting started (90-day plan)

A practical first-quarter plan for an organization starting from Level 0 or 1:

**Days 1–30 — Discover and inventory.**

- Build an AI inventory: every AI system in use, including shadow AI. Methods: cloud expense review, network traffic analysis, developer survey, code-scanning for `import openai` / `from anthropic` / vendor SDK strings, SSO audit logs.
- For each system, capture: name, owner, use case, data inputs and outputs, model and provider, deployment surface, regulatory exposure (GDPR, HIPAA, EU AI Act, etc.).
- Identify the 3–5 highest-risk systems (e.g., customer-facing, handling PHI/PII, in a regulated function, in HR/credit/law-enforcement adjacent use cases).
- Stakeholder alignment: brief the CISO, GC, CEO, and board on the AI risk landscape.

**Days 31–60 — Establish baseline governance.**

- Draft an AI policy: scope, principles, approved use cases, prohibited use cases, approval process, vendor requirements, incident reporting.
- Establish an AI risk register and tier systems by risk (recommend three tiers: low, medium, high; align with EU AI Act tiers where applicable).
- Define a lightweight review process for new AI deployments: a one-page form covering use case, data, model, risk tier, controls, and sign-offs.
- Map the high-risk systems to the applicable frameworks (NIST AI RMF, EU AI Act, ISO 42001, sector-specific). Identify the largest gaps.

**Days 61–90 — Implement controls and quick wins.**

- For the high-risk systems, implement the defense-in-depth architecture from the defenses file:
  - Input classifier (e.g., OpenAI Moderation API or self-hosted Llama Guard 3).
  - Output schema validation.
  - Logging and audit.
  - Tool allowlist (for agentic systems).
  - Sandboxing (for code-execution agents).
- Conduct an initial red-team exercise on the high-risk systems (manual + Garak + promptfoo).
- Establish monitoring: at minimum, log every LLM call with full prompt, completion, model version, and user ID. Set up basic anomaly detection.
- Run a tabletop exercise: simulate an AI incident (e.g., model exfiltration, prompt-injection success, biased output, IP-infringement claim) and walk through the response.
- Begin ISO 42001 / SOC 2 / AI RMF alignment work, in parallel.

#### 10.3 Common pitfalls

- **"AI is a model problem."** Treating AI safety as a problem for the model team alone. AI safety is cross-functional: security, legal, compliance, privacy, ethics, operations. Governance must reflect that.
- **"The vendor is responsible."** The vendor is responsible for the *foundation model*; the deployer is responsible for the *application*. The LLM01 prompt injection vulnerability in your app is not OpenAI's or Anthropic's responsibility — it's yours.
- **"We'll add safety later."** Retrofitting safety is much more expensive than building it in. The cost of adding safety at the design stage is 10–100x less than retrofitting after a production incident.
- **"We need to block all AI."** Shadow AI is more dangerous than managed AI. The goal is not to block AI use; it's to ensure AI use is visible, governed, and controlled.
- **"One model, one vendor."** Vendor concentration is a risk. The frontier moves; a single-vendor strategy leaves you exposed to model regressions, price changes, capability gaps, and safety incidents at the vendor.
- **"We follow the AI RMF."** Without documented artifacts (AI inventory, risk register, impact assessments, control evidence, training records), the claim is hollow. Auditors will ask for evidence.
- **"Eval is a one-time thing."** Eval suites are living artifacts. They need to be updated every quarter to track the latest attack classes; results need to be tracked over time; regressions need to fail CI.
- **"Monitoring = logging."** Logging is necessary but not sufficient. Without anomaly detection, alerting, and runbooks, logs are write-only storage.

#### 10.4 Roles and responsibilities

A typical org-chart at Level 2+:

- **Chief AI Officer (CAIO) or equivalent.** Single accountable executive for AI risk; reports to the CEO or board. Owns the AI policy, the AI risk register, and the AI governance committee.
- **AI Governance Committee.** Cross-functional body that reviews high-risk AI deployments before launch. Members: CAIO, CISO, GC/CCO, head of compliance, head of data, head of engineering, an external ethics advisor.
- **AI Risk Owners.** Each AI system has a named risk owner (typically the business owner) who is accountable for the system's risk register, controls, and incidents.
- **AI Security / Trust & Safety team.** Specialized team that handles AI-specific security: red-teaming, eval suite maintenance, incident response for AI incidents, vendor assessment.
- **AI Engineering.** The product and ML engineering teams that build, deploy, and operate AI systems. Responsible for implementing the controls specified by the AI Governance Committee.

#### 10.5 Operating cadence

- **Weekly.** AI risk owners review their systems' monitoring dashboards; report anomalies.
- **Monthly.** AI Security team reviews eval-set results, red-team findings, vendor advisories, and regulatory developments.
- **Quarterly.** AI Governance Committee reviews the AI risk register, approves new high-risk deployments, and reviews the AI policy. External red-team engagement every 6–12 months.
- **Annually.** Full AI risk management review; recertify ISO 42001; refresh the AI policy; review the AI inventory for completeness.

#### 10.6 Framework crosswalk

A practical question: which framework to prioritize? The answer depends on the organization:

- **US-based, federal contractor.** Start with FedRAMP (if cloud), CISA joint guidance, and NIST AI RMF. Layer in sector-specific (HIPAA, SR 11-7) as applicable.
- **EU-based or EU-market-facing.** Start with EU AI Act (mandatory). Layer in ISO 42001 (presumption of conformity), NIST AI RMF (crosswalk), and sector-specific.
- **Globally operating.** ISO 42001 as the management-system foundation; NIST AI RMF as the methodology; EU AI Act for the EU market; sector-specific per region.
- **Foundation-model provider.** EU AI Act GPAI obligations, ISO 42001, voluntary signing of the GPAI Code of Practice, plus all the safety commitments in the system cards.
- **Highly regulated (banking, healthcare).** Sector-specific first (SR 11-7 / HIPAA + FDA / ECB), then ISO 42001 and NIST AI RMF.

In all cases, OWASP AI Security & Privacy Guide and OWASP LLM Top 10 are the practitioner's reference — they are the most concrete and code-oriented of the available guidance and should be on every AI developer's desk.

#### 10.7 What "good" looks like

A Level 3+ organization can answer "yes" to all of the following:

1. Do we have an AI inventory that includes shadow AI?
2. Can we name the risk owner of every AI system?
3. For every high-risk system, do we have a documented risk register, impact assessment, and control set?
4. Are AI risks integrated into the enterprise risk framework and reviewed by the board?
5. Do we have eval suites that run on every model upgrade and every system-prompt change?
6. Do we have a documented incident response process for AI-specific incidents?
7. Have we conducted red-team exercises in the last 12 months?
8. Are we tracking regulatory developments (EU AI Act delegated acts, FDA guidance, sector-specific rules) and updating our controls?
9. Is every employee who uses AI trained on safe use and our internal policy?
10. Is our AI policy and risk posture documented in a way that survives personnel changes?

If the answer to any of these is "no" or "I don't know," that is the next priority.

## Related

- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — all frameworks leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these frameworks
