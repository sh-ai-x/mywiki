---
tags: ["iso-42001", "ai-security", "nist-rmf", "eu-ai-act"]
priority: medium
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/00-index"]
created: 2026-09-07
source: "_research/core-ai-security-frameworks.md"
---

# ISO/IEC 42001:2023 — AI Management System (AIMS)

> **Document.** *ISO/IEC 42001:2023 Information technology — Artificial intelligence — Management system*. Published December 2023. ~50 pages. First edition

**Document.** *ISO/IEC 42001:2023 Information technology — Artificial intelligence — Management system*. Published December 2023. ~50 pages. First edition.

**Purpose.** Specify the requirements for establishing, implementing, maintaining, and continually improving an AI management system within the context of an organization. It is the world's first certifiable AI management system standard.

#### 2.1 Structure (Annex SL)

Like all recent ISO management system standards (ISO 9001, 27001, 27701), ISO 42001 is built on the Annex SL high-level structure:

- **Clause 4 — Context of the organization.** Identify internal and external issues; the needs and expectations of interested parties; the scope of the AIMS.
- **Clause 5 — Leadership.** Top management must demonstrate leadership and commitment, establish an AI policy, and assign roles and responsibilities.
- **Clause 6 — Planning.** Actions to address risks and opportunities; AI risk assessment; AI risk treatment; AI objectives and planning to achieve them; planning of changes.
- **Clause 7 — Support.** Resources, competence, awareness, communication, documented information.
- **Clause 8 — Operation.** Operational planning and control; AI risk assessment; AI risk treatment; AI system impact assessment.
- **Clause 9 — Performance evaluation.** Monitoring, measurement, analysis, and evaluation; internal audit; management review.
- **Clause 10 — Improvement.** Continual improvement; nonconformity and corrective action.

#### 2.2 Annex A — AI-specific control objectives

Annex A contains a normative set of control objectives and controls (similar to Annex A in ISO 27001). Major groups:

- **A.2 — AI policies** — documented AI policy aligned with the organization's strategic direction.
- **A.3 — Internal organization** — roles, responsibilities, and authorities for AI; AI ethics committee or review board.
- **A.4 — Resources for AI systems** — AI data, tooling, compute, infrastructure.
- **A.5 — Assessing impacts of AI systems** — AI system impact assessment process.
- **A.6 — AI system lifecycle** — requirements, design, development, verification and validation, deployment, operation, retirement.
- **A.7 — Data for AI systems** — data quality, data provenance, data preparation, data labeling, data management.
- **A.8 — Third-party and customer relationships** — supplier relationships, customer communication, dispute resolution.
- **A.9 — Responsible use of AI systems** — responsible AI principles, fairness, transparency, explainability, contestability.
- **A.10 — AI system operations and monitoring** — operational monitoring, change management, incident management.
- **A.11 — Information for interested parties** — transparency, communication.
- **A.12 — Use of AI-generated content** — handling, distribution, accountability.

Each control has a control objective, recommended implementation guidance, and other implementation guidance. Organizations must justify any control they exclude from scope.

#### 2.3 Certification

ISO 42001 is certifiable. Accredited certification bodies (ANAB, UKAS, BSI, TÜV, DNV) began issuing certificates in 2024. The certification audit is a 2-stage process: Stage 1 (documentation review) and Stage 2 (on-site audit verifying implementation). Surveillance audits are annual; re-certification is every 3 years. First ISO 42001 certificates appeared in 2024; the market grew rapidly through 2025–2026.

**Implementation time.** A typical mid-size enterprise takes 6–12 months from kickoff to certification. Many organizations pair ISO 42001 with ISO 27001 (information security) and ISO 27701 (privacy) and pursue all three together — the controls overlap, and the audit can be combined.

#### 2.4 Common implementation patterns

- **AI system inventory.** The single most important artifact. Every AI system in scope is registered with: name, owner, use case, data inputs, model, deployment surface, risk classification (per the organization's own taxonomy), and the controls that apply.
- **AI risk register.** Per AI system, identify the specific risks (privacy, bias, security, IP, etc.) and the treatment plan.
- **AI policy.** One document, approved by top management, that states the organization's principles and commitments.
- **AI ethics committee or review board.** A cross-functional body that reviews high-risk AI deployments before launch. Membership typically includes legal, compliance, security, ethics, and technical leads.
- **AI impact assessment.** Required for high-risk systems; covers intended use, affected populations, potential harms, mitigations, residual risk, and sign-off.
- **Third-party AI assessment.** For each third-party AI system, the organization assesses the provider's practices against the same standard and includes the assessment in the procurement decision.
- **AI incident management.** A documented process for AI-specific incidents (model failure, data breach, bias discovery, etc.), integrated with the existing security incident response process.
- **Data lineage.** For each AI system, a documented view of where the training data came from, what transformations were applied, what consent was obtained, and what TDM opt-outs were respected.

#### 2.5 Relationship to other standards

- **NIST AI RMF.** ISO 42001 is the management-system framework; AI RMF is the risk-management methodology. They are complementary. NIST has published a crosswalk mapping AI RMF categories to ISO 42001 clauses and Annex A controls.
- **ISO 27001 (information security).** Substantial overlap on the security controls; many organizations extend their existing ISMS to cover AI.
- **ISO 27701 (privacy).** Overlap on data-handling controls; AI-specific data lineage often lives here.
- **EU AI Act.** ISO 42001 certification creates a *presumption of conformity* with the AI Act's general requirements (per Article 53(3) for GPAI and the corresponding provisions for high-risk systems). Certification is not a substitute for the AI Act's specific obligations, but it materially reduces audit burden.
- **SOC 2.** ISO 42001 certification complements but does not replace SOC 2; SOC 2 covers broader IT controls.

#### 2.6 Limitations

- **No sectoral overlays yet.** The standard is horizontal; healthcare, finance, and government have additional requirements that ISO 42001 does not address.
- **Slow to update.** As with all ISO standards, revisions happen on a 5–7 year cycle; the AI field moves faster.
- **Audit cost.** A full ISO 42001 certification audit is $50K–$200K depending on organization size and scope.

## Related

- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — all frameworks leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these frameworks
