---
tags: ["ai-security", "nist-rmf", "iso-42001", "eu-ai-act", "interview-prep"]
priority: high
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/00-index"]
created: 2026-09-07
source: "_research/core-ai-security-frameworks.md"
---

# NIST AI Risk Management Framework (AI RMF 1.0)

> **Document.** *Artificial Intelligence Risk Management Framework (AI RMF 1.0)*. NIST, January 26, 2023. 64 pages plus appendices. Voluntary. US-origin but widely adopted internationally as a baseline reference

**Document.** *Artificial Intelligence Risk Management Framework (AI RMF 1.0)*. NIST, January 26, 2023. 64 pages plus appendices. Voluntary. US-origin but widely adopted internationally as a baseline reference.

**Structure.** Four core functions rendered in a circular diagram showing their interrelated nature. GOVERN is the cross-cutting function that runs across MAP, MEASURE, and MANAGE. Each function is broken into categories and sub-categories.

#### 1.1 GOVERN (cross-cutting)

The CULTURE of AI risk management across the organization. GOVERN activities apply to every other function.

- **GOVERN 1 — Policies, processes, procedures and practices.** Documented AI policies, defined processes, accountability for AI risk decisions, board-level visibility.
- **GOVERN 2 — Roles and responsibilities.** Designated AI risk owners; clear lines of authority for AI systems across their lifecycle; separation of duties between development, deployment, and oversight.
- **GOVERN 3 — AI risk management considerations in workforce hiring and training.** AI literacy requirements; cross-functional training; on-call coverage for AI incidents.
- **GOVERN 4 — Documentation and transparency.** AI system inventory; data lineage; model cards; decision records; impact assessments.

GOVERN is the function that is most often skipped by engineering-led AI programs — and the one regulators look at first. A "we follow the AI RMF" claim without documented GOVERN artifacts is hard to defend in an audit.

#### 1.2 MAP — establish the context

Identify and frame AI risks in the context of the system being deployed.

- **MAP 1 — Context.** Define the AI system, its intended use, its stakeholders (users, affected parties, operators), and the broader societal context.
- **MAP 2 — Categorize the AI system.** Classify the system by type, deployment context, data sensitivity, and affected populations. Identify whether the system is high-risk (per applicable regulation) or low-risk.
- **MAP 3 — Understand the AI capabilities, limitations, and risks.** What the system can and cannot do; known failure modes; novel capabilities introduced by the model.
- **MAP 4 — Impacts.** Map intended and unintended impacts on individuals, groups, communities, and organizations. Consider downstream and second-order effects.
- **MAP 5 — Likelihood and magnitude of identified impacts.** Assess the probability and severity of each impact; prioritize for treatment.

The output of MAP is a *risk register* — a structured list of identified risks with assigned owners and priorities.

#### 1.3 MEASURE — analyze, assess, benchmark, monitor

Quantitative, qualitative, or mixed-method evaluation of AI risks.

- **MEASURE 1 — Appropriate methods and metrics.** Define what you measure and how: accuracy, fairness, robustness, security, privacy, explainability. For each metric, a measurement method and a target.
- **MEASURE 2 — Evaluate AI systems for trustworthy characteristics.** Run the eval suite; compare against baselines and thresholds. Track over time.
- **MEASURE 3 — Mechanisms for tracking identified AI risks over time.** Continuous monitoring; alert thresholds; dashboards; incident tracking.
- **MEASURE 4 — Feedback about efficacy of measurement.** Are the metrics themselves working? Are we measuring the right things?

The MEASURE function is where most engineering effort goes: building eval suites, running benchmarks, building dashboards. It is also where most AI programs *under-invest* in the social-science side: user research, demographic-disparate-impact analysis, qualitative interviews with affected populations.

#### 1.4 MANAGE — allocate resources to risks

- **MANAGE 1 — AI risks based on assessed impact.** Prioritize and treat. Allocate engineering, policy, and operational resources to the highest-impact risks.
- **MANAGE 2 — Mechanisms to maximize AI benefits and minimize negative impacts.** Active risk treatment: deploy a guardrail, change a workflow, add a human-in-the-loop, retire a feature.
- **MANAGE 3 — Documented plans for responding to and recovering from AI incidents.** IR runbooks, rollback procedures, communication plans.
- **MANAGE 4 — Processes for ongoing risk management.** Recurring risk review, exception handling, change control.

#### 1.5 Profiles

Companion profiles tailor the AI RMF to specific use cases, sectors, or technologies. They map the abstract categories to concrete actions. Published profiles include:

- **NIST AI 600-1 Generative AI Profile** (Jul 2024) — the most consequential; detailed in §1.6.
- **NIST AI 600-2 Secure Software Development for AI Systems** — companion profile on the SDLC side.
- **Sector profiles** — developed by sector-specific working groups (healthcare, finance, energy).

Profiles are how the AI RMF becomes operationally useful — they turn "MAP" into "before deploying a clinical decision support system, do X, Y, Z".

#### 1.6 NIST AI 600-1 — Generative AI Profile

**Document.** *Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile*. NIST AI 600-1. July 26, 2024. ~60 pages plus extensive appendices. Voluntary.

**Purpose.** Operationalize the AI RMF for generative AI and foundation models. The profile identifies 12 unique GenAI risks, proposes risk-management actions for each, and maps every action to a RMF category/sub-category.

**The 12 unique GenAI risks (GV = GOVERN, MP = MAP, MS = MEASURE, MG = MANAGE):**

1. **Confabulation** (GV, MS) — the model produces false or misleading information presented as fact (hallucinations, fabricated citations).
2. **Data privacy** (GV, MP, MS, MG) — leakage of training data or sensitive information through the model or its outputs.
3. **Harmful bias** (GV, MP, MS, MG) — disparate model performance or outputs across demographic groups.
4. **Information integrity** (MP, MS, MG) — generated content that contributes to disinformation, radicalization, or manipulation.
5. **Information security** (GV, MP, MS, MG) — model is used as a vector for cyberattacks (phishing generation, exploit synthesis, malware authoring) or is itself attacked (model theft, weight extraction).
6. **Obscured provenance** (GV, MP, MS) — generated content is presented as human-authored; the source is untraceable.
7. **Intellectual property** (GV, MP, MS, MG) — model emits copyrighted text, code, or images without attribution or license.
8. **Confusing or misleading human-AI interactions** (GV, MP, MG) — users over-rely on the model, anthropomorphize it, or are deceived about its capabilities.
9. **Data rights and impacts on data subjects** (GV, MP, MS) — training data was collected without proper consent; data subjects' rights are not respected.
10. **Environmental and sustainability impacts** (GV, MP) — energy and water consumption of training and inference.
11. **Inequitable distribution of AI benefits** (GV, MP) — benefits accrue to well-resourced groups; harms fall on under-resourced groups.
12. **Increased risk for specific populations** (GV, MP, MS, MG) — heightened harms to children, the elderly, persons with disabilities, marginalized communities.

For each risk, the profile specifies suggested actions for *developers* (model providers), *deployers* (organizations integrating the model), and *operators* (end-user-facing teams). The actions are cross-referenced to the AI RMF categories, making the profile a structured playbook rather than a principles document.

**Why it matters operationally.** Procurement contracts increasingly require vendors to map their safety claims to the AI 600-1 risk categories. The profile has become the de facto US baseline for GenAI safety, even outside federal regulation. It is the most-cited document when procurement asks "how do you handle confabulation?" or "what is your process for IP risk?".

#### 1.7 Companion resources

- **AI RMF Playbook** — a community-contributed, action-oriented companion document.
- **AI RMF Crosswalk** — maps the AI RMF categories to other frameworks (ISO 42001, SOC 2, NIST CSF).
- **Trustworthy and Responsible AI Resource Center** — NIST's central portal for tools, datasets, and case studies.

#### 1.8 Limitations and critiques

- **Voluntary.** No regulatory teeth; compliance is opt-in.
- **US-centric.** Written in the US regulatory idiom; non-US organizations must adapt to local requirements.
- **Abstract.** The RMF itself is principle-level; profiles are needed to make it operational. The 600-1 GenAI Profile is the only broadly-accepted profile to date.
- **Slow update cycle.** Profiles are revised on a 1–2 year cycle; the AI field moves faster.

## Related

- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — all frameworks leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these frameworks
