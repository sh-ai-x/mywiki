---
topic: core-ai-security-frameworks
created: 2026-09-07T00:00:00Z
updated: 2026-09-09T17:32:27+00:00
sources:
  - https://www.nist.gov/itl/ai-risk-management-framework
  - https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf
  - https://www.iso.org/standard/81230.html
  - https://artificialintelligenceact.eu/the-act/
  - https://artificialintelligenceact.eu/article/5/
  - https://artificialintelligenceact.eu/article/50/
  - https://digital-strategy.ec.europa.eu/en/policies/ai-code-practice
  - https://digital-strategy.ec.europa.eu/en/library/ai-act-final-draft-code-practice-gpai-models-published
  - https://atlas.mitre.org/
  - https://atlas.mitre.org/mitigations/
  - https://owasp.org/www-project-ai-security-and-privacy-guide/
  - https://owasp.org/www-project-top-10-for-large-language-model-applications/
  - https://www.cisa.gov/resources-tools/groups/ai-data-security
  - https://learn.microsoft.com/en-us/azure/ai-services/content-safety/overview
  - https://platform.openai.com/docs/guides/moderation
  - https://www.anthropic.com/news/core-views-on-ai-safety
  - https://www.federalreserve.gov/supervisionreg/sr-letters/SR1107.htm
  - https://www.hhs.gov/hipaa/index.html
  - https://www.fedramp.gov/ai/
  - https://www.federalregister.gov/documents/2023/10/30/2023-24283/safe-secure-and-trustworthy-development-and-use-of-artificial-intelligence
  - https://en.wikipedia.org/wiki/Executive_Order_14110
  - https://www.federalreserve.gov/supervisionreg/sr-letters/SR1107a1.pdf
  - https://www.ecb.europa.eu/pub/pdf/other/ssm.letter.letter2024.10~ca6a99f3ed.en.pdf
  - https://www.fda.gov/medical-devices/software-medical-device-samd/artificial-intelligence-and-machine-learning-aiml-enabled-medical-devices
  - https://www.whitehouse.gov/presidential-actions/2025/01/23/removing-barriers-to-american-leadership-in-artificial-intelligence/
  - https://owasp.org/www-project-top-10-for-large-language-model-applications/llm01-prompt-injection
  - https://owasp.org/www-project-top-10-for-large-language-model-applications/llm08-excessive-agency
  - https://aws.amazon.com/bedrock/guardrails/
  - https://www.llama.com/docs/model-cards-and-prompt-formats/llama-guard-3/
  - https://www.itu.int/itu-t/recommendations/rec.aspx?rec=14930
  - https://www.iso.org/standard/81230.html
  - https://www.nist.gov/itl/ai-risk-management-framework/generative-ai-profile
  - https://www.cisa.gov/news-events/news/guidelines-secure-ai-system-development
  - https://www.ec.europa.eu/digital-strategy/our-policies/regulatory-framework-ai
  - https://artificialintelligenceact.eu/the-act/
status: promoted
---
promoted_to: wiki/ai-agent-wiki/knowledge/core-ai-security/frameworks/_index.md

## Sources

- https://www.nist.gov/itl/ai-risk-management-framework — NIST AI RMF 1.0 (Jan 2023); voluntary framework structured around four core functions — GOVERN, MAP, MEASURE, MANAGE — for designing, developing, and evaluating trustworthy AI.
- https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf — NIST AI 600-1 *Generative AI Profile* (Jul 2024); companion profile enumerating twelve GenAI-specific risks (confabulation, data privacy, dangerous information, harmful bias, IP infringement, etc.) and 200+ recommended actions mapped to the four RMF functions.
- https://www.iso.org/standard/81230.html — ISO/IEC 42001:2023 *Information technology — Artificial intelligence — Management system*; the world's first AI management system standard, structured per Annex SL (clauses 4–10) with AI-specific control objectives in Annex A; certifiable.
- https://artificialintelligenceact.eu/the-act/ and https://artificialintelligenceact.eu/article/5/ and https://artificialintelligenceact.eu/article/50/ — EU AI Act (Regulation (EU) 2024/1689); risk-tiered regulation with four tiers (unacceptable, high, limited, minimal) and obligations for general-purpose AI (GPAI) models under Articles 51–55.
- https://digital-strategy.ec.europa.eu/en/policies/ai-code-practice and https://digital-strategy.ec.europa.eu/en/library/ai-act-final-draft-code-practice-gpai-models-published — European Commission *General-Purpose AI (GPAI) Code of Practice*; voluntary compliance tool for GPAI providers covering Transparency, Copyright, and Safety & Security chapters.
- https://atlas.mitre.org/ — MITRE ATLAS: adversary-tactics-and-techniques knowledge base for AI/ML systems, modeled on ATT&CK with ML-specific tactics (e.g., ML Model Access, ML Attack Staging).
- https://atlas.mitre.org/mitigations/ — ATLAS defensive mitigations catalog: enumerated mitigations (Limit Model Access, Restrict Number of Models, Adversarial Input Detection, Model Hardening, Establish AI Supply Chain Controls, etc.) with attacker-technique cross-references.
- https://owasp.org/www-project-ai-security-and-privacy-guide/ — OWASP AI Security & Privacy Guide (200+ pages, v1.0); broad guidance for Builders/Breakers/Buyers, actively contributing to ISO/IEC and EU AI Act implementation guidance.
- https://owasp.org/www-project-top-10-for-large-language-model-applications/ — OWASP LLM Top 10 (v1.1 archived; current: 2025/2026 list under the OWASP GenAI Security Project); the de facto taxonomy of LLM application risks (LLM01–LLM10).
- https://owasp.org/www-project-top-10-for-large-language-model-applications/llm01-prompt-injection and https://owasp.org/www-project-top-10-for-large-language-model-applications/llm08-excessive-agency — canonical OWASP pages for LLM01 and LLM08 with examples and mitigations.
- https://www.cisa.gov/resources-tools/groups/ai-data-security — CISA AI Data Security guidance (with NSA, FBI, NCSC, and 21 international partners); "Guidelines for Secure AI System Development" and "Guidelines for Secure AI System Deployment" — jointly issued 2024.
- https://www.cisa.gov/news-events/news/guidelines-secure-ai-system-development — CISA landing page for the "Guidelines for Secure AI System Development" jointly with NSA, FBI, NCSC, and 21 international agencies (Nov 2024).
- https://learn.microsoft.com/en-us/azure/ai-services/content-safety/overview — Microsoft Azure AI Content Safety (vendor SDK/API suite) — Prompt Shields, Groundedness detection, Protected material, Task adherence; integrates with Azure OpenAI and Defender for AI services.
- https://platform.openai.com/docs/guides/moderation — OpenAI Moderation API (vendor SDK/API); omni-moderation-latest free classifier; foundational input/output filter in most production pipelines.
- https://www.anthropic.com/news/core-views-on-ai-safety — Anthropic Responsible Scaling Policy (vendor commitment); empirically-driven, portfolio-of-defenses framing.
- https://www.federalreserve.gov/supervisionreg/sr-letters/SR1107.htm — SR 11-7 *Guidance on Model Risk Management* (Apr 2011, US Federal Reserve); foundational banking-sector framework for model validation, governance, and ongoing monitoring — increasingly applied to AI/ML models.
- https://www.federalreserve.gov/supervisionreg/sr-letters/SR1107a1.pdf — SR 11-7 attachment A (supervisory expectations); detailed expectations for model risk management.
- https://www.hhs.gov/hipaa/index.html — HIPAA Privacy and Security Rules (45 CFR Parts 160, 162, 164); applies to any AI tool that creates, receives, maintains, or transmits PHI on behalf of a covered entity.
- https://www.fedramp.gov/ai/ — FedRAMP AI Prioritization Initiative (Aug 2025–Apr 2026); fast-track FedRAMP 20x authorization for enterprise conversational AI cloud services meeting SSO/SCIM/RBAC/data-isolation criteria; first three products (ChatGPT Enterprise, Gemini for Government, Perplexity Enterprise Pro) certified early 2026.
- https://www.federalregister.gov/documents/2023/10/30/2023-24283/safe-secure-and-trustworthy-development-and-use-of-artificial-intelligence and https://en.wikipedia.org/wiki/Executive_Order_14110 — Executive Order 14110 (Biden, Oct 30 2023); the largest US federal AI policy directive until it was rescinded hours after Trump's Jan 20 2025 inauguration.
- https://www.whitehouse.gov/presidential-actions/2025/01/23/removing-barriers-to-american-leadership-in-artificial-intelligence/ — Executive Order 14179 (Trump, Jan 23 2025) "Removing Barriers to American Leadership in Artificial Intelligence"; rescinds EO 14110 and reframes US AI policy around innovation and removing "onerous" regulation.
- https://www.ecb.europa.eu/pub/pdf/other/ssm.letter.letter2024.10~ca6a99f3ed.en.pdf — ECB letter to all significant institutions on AI (Oct 2024); supervisory expectations for governance, risk management, and model risk management for AI/ML.
- https://www.fda.gov/medical-devices/software-medical-device-samd/artificial-intelligence-and-machine-learning-aiml-enabled-medical-devices — FDA landing page for AI/ML-Enabled Medical Devices; includes list of authorized devices and the Predetermined Change Control Plan guidance.
- https://aws.amazon.com/bedrock/guardrails/ — AWS Bedrock Guardrails product page; cross-model safeguards for foundation models.
- https://www.llama.com/docs/model-cards-and-prompt-formats/llama-guard-3/ — Meta's Llama Guard 3 model card; input-output safety classifier.
- https://www.itu.int/itu-t/recommendations/rec.aspx?rec=14930 — ITU-T Y.3170-series and related ITU standards on AI/ML in networks; reference for telecommunications AI governance.
- https://www.nist.gov/itl/ai-risk-management-framework/generative-ai-profile — NIST AI RMF Generative AI Profile landing page.
- https://www.ec.europa.eu/digital-strategy/our-policies/regulatory-framework-ai — European Commission landing page for the EU AI regulatory framework; includes the AI Act, the AI Liability Directive, and the GPAI Code of Practice.

## Notes

### 1. NIST AI Risk Management Framework (AI RMF 1.0)

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

### 2. ISO/IEC 42001:2023 — AI Management System (AIMS)

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

### 3. EU AI Act — Regulation (EU) 2024/1689

**Document.** *Regulation (EU) 2024/1689 of the European Parliament and of the Council laying down harmonised rules on artificial intelligence (Artificial Intelligence Act)*. Adopted 13 March 2024; entered into force 1 August 2024. ~450 pages. The world's first comprehensive horizontal AI regulation.

**Approach.** Risk-tiered: the obligations depend on the risk class of the AI system. The Act also has a separate track for general-purpose AI (GPAI) models.

#### 3.1 Risk tiers

**Unacceptable risk (banned, Article 5).** Prohibited AI practices. The eight prohibitions in Article 5(1) cover:

1. **Subliminal / manipulative / deceptive techniques** that distort behavior causing significant harm.
2. **Exploitation of vulnerabilities** (age, disability, socio-economic circumstances) causing significant harm.
3. **Social scoring** by public authorities leading to detrimental or unfavorable treatment.
4. **Predictive policing** based solely on profiling or personality traits.
5. **Untargeted scraping** of facial images from the internet or CCTV to create or expand facial recognition databases.
6. **Emotion recognition** in the workplace and educational settings (with narrow exceptions for medical or safety reasons).
7. **Biometric categorization** inferring sensitive attributes (race, political opinions, trade union membership, religious beliefs, sex life or orientation) from biometric data.
8. **Real-time remote biometric identification** in publicly accessible spaces by law enforcement (with narrow exceptions for serious crime, missing persons, etc.; requires prior judicial or independent administrative authorization).

These prohibitions apply from 2 February 2025.

**High risk (Annex III).** AI systems in the following areas are considered high-risk:

- Critical infrastructure (water, gas, heating, electricity, traffic).
- Education and vocational training (admission, evaluation, exam monitoring).
- Employment, worker management, access to self-employment.
- Access to and use of essential private and public services and benefits (credit scoring, insurance pricing, emergency dispatch, public benefits).
- Law enforcement (crime prediction, recidivism risk, profiling, lie detection, evaluation of evidence reliability).
- Migration, asylum, and border control.
- Administration of justice and democratic processes.
- Safety components of products covered by sectoral legislation (medical devices, toys, vehicles, etc.) listed in Annex I.
- Biometric identification and categorization (1-to-1 and 1-to-many).

Obligations for high-risk systems (Chapter III) include:
- **Risk-management system** throughout the lifecycle (Article 9).
- **Data governance** — training, validation, and testing datasets must be relevant, representative, and as free of errors as possible; appropriate statistical properties for the intended use (Article 10).
- **Technical documentation** demonstrating conformity (Annex IV) (Article 11).
- **Record-keeping** — automatic logging of events (Article 12).
- **Transparency and information to deployers** — instructions for use including the system's characteristics, capabilities, and limitations (Article 13).
- **Human oversight** — designed to allow effective human oversight during the period of use (Article 14).
- **Accuracy, robustness, cybersecurity** — appropriate levels declared in the instructions; resilience to errors, faults, and adversarial attacks (Article 15).
- **Quality management system** for the provider (Article 17).
- **Conformity assessment** before placing on the market (Article 43).
- **Registration** in the EU database (Article 49).
- **Post-market monitoring** by the provider (Article 72).
- **Serious incident reporting** to market surveillance authorities (Article 73).

High-risk obligations apply from 2 August 2026 (or 2 August 2027 for systems embedded in safety components of products regulated under sectoral law).

**Limited risk (Article 50 transparency obligations).** AI systems that interact with natural persons, generate synthetic content, perform emotion recognition or biometric categorization, or generate "deepfakes" must:

- Inform users that they are interacting with an AI system (chatbots).
- Label synthetic content as artificially generated or manipulated (deepfakes, AI-generated text/images/video).
- Comply with EU copyright law, including Article 4(3) of the DSM Directive (TDM opt-out).

These obligations apply from 2 August 2025.

**Minimal risk.** All other AI systems. No obligations; voluntary codes of conduct encouraged.

#### 3.2 General-purpose AI (GPAI) models (Articles 51–55)

A separate track for foundation models. Two sub-tiers:

**All GPAI models (Article 53).** Providers must:
- Maintain **technical documentation** of the model (Annex XI).
- Provide **information to downstream providers** to enable compliance.
- Comply with EU **copyright law**, including implementing the TDM opt-out.
- Publish a sufficiently detailed **summary of training data** (per a template provided by the AI Office).

**GPAI models with "systemic risk" (Article 55).** Triggered by either:
- Training compute > 10^25 FLOPs, OR
- Designation by the European Commission based on capabilities, impact, or other criteria.

Additional obligations:
- Conduct **state-of-the-art model evaluations**, including adversarial testing.
- Assess and mitigate **systemic risks** at the Union level.
- Track and report **serious incidents** to the AI Office.
- Ensure **adequate cybersecurity** for the model and its infrastructure.
- **Energy efficiency** reporting.

GPAI rules apply from 2 August 2025. GPAI models placed on the market before 2 August 2025 must comply by 2 August 2027.

#### 3.3 GPAI Code of Practice

A voluntary compliance tool published by the European Commission in mid-2025 to help GPAI providers demonstrate conformity with the AI Act. Three chapters:

- **Transparency chapter.** Commitments on documentation, training-data summary, and downstream disclosure.
- **Copyright chapter.** Commitments to comply with EU copyright law, respect TDM opt-outs, and avoid generating copyrighted text.
- **Safety & Security chapter.** Commitments on model evaluation, risk assessment, red-teaming, incident reporting, and cybersecurity. Applies to systemic-risk GPAI.

Signatories as of 2026 include Google, OpenAI, Anthropic, Microsoft, and Amazon. Meta notably declined to sign the Copyright chapter, citing concerns about over-disclosure of training data.

Signing the Code creates a **presumption of conformity** with the relevant AI Act obligations — material reduction in audit burden.

#### 3.4 Penalties

Article 99 sets maximum administrative fines:
- **€35M or 7% of global annual turnover** (whichever is higher) for the most serious violations (Article 5 prohibitions, certain GPAI obligations).
- **€15M or 3%** for violations of high-risk obligations and most other provider/deployer duties.
- **€7.5M or 1%** for supplying incorrect information to authorities.

SMEs and startups face the lower of the absolute amount or a percentage-based cap.

#### 3.5 Enforcement and governance

- **AI Office** (within the European Commission) — coordinates implementation, oversees GPAI, promotes the Code of Practice.
- **AI Board** (Member State representatives) — advises, coordinates, issues guidance.
- **National competent authorities** in each Member State — designated as market surveillance authorities; handle day-to-day enforcement.
- **Notified bodies** (third-party conformity assessment bodies) — assess high-risk systems for providers that don't do self-assessment.
- **EU AI database** — public registry of high-risk AI systems.

#### 3.6 Extraterritorial reach

Like GDPR, the AI Act applies to providers and deployers that place AI systems on the EU market or that affect persons in the EU — regardless of where the provider is established. A US-based SaaS company whose product is used by an EU customer is potentially in scope.

#### 3.7 Other EU AI policy instruments

- **AI Liability Directive (proposed, 2022, under revision as of 2026).** Would create a rebuttable presumption of causation and a disclosure obligation for AI-related harm claims.
- **Digital Services Act (DSA).** Overlaps with AI Act on recommender systems, content moderation, and deepfakes.
- **GDPR.** Applies in parallel; AI Act does not displace GDPR.
- **NIS2 Directive.** Cyber-security baseline that applies to operators of essential services; some AI deployments fall under it.
- **EU AI Pact** (voluntary). Industry pledge to start implementing AI Act obligations ahead of the deadlines.

### 4. MITRE ATLAS

**Document.** *Adversarial Threat Landscape for AI Systems* (ATLAS). Maintained by MITRE, with contributions from Microsoft, Google, OpenAI, Anthropic, and academic researchers. Free, publicly available, regularly updated.

**Purpose.** A knowledge base of adversary tactics, techniques, and case studies observed against real production AI/ML systems. Modeled on MITRE ATT&CK (which covers enterprise IT) but tailored to the AI/ML attack surface: training data, model artifacts, inference endpoints, and the supply chain.

#### 4.1 Tactics

ATLAS organizes techniques under 14 tactics, roughly tracking the kill chain:

1. **Reconnaissance (AML.TA0001)** — gathering information about the target AI system (model type, training data sources, deployment surface).
2. **Resource Development (AML.TA0002)** — acquiring infrastructure (compute, accounts, datasets) for the attack.
3. **Initial Access (AML.TA0003)** — gaining a foothold (exploiting a vulnerability in the inference endpoint, phishing an ML engineer).
4. **ML Model Access (AML.TA0004)** — gaining read or write access to the model (parameter extraction, theft, or tampering).
5. **Execution (AML.TA0005)** — running attacker code (often through a model that emits code, or a compromised ML pipeline).
6. **Persistence (AML.TA0006)** — maintaining access across restarts (backdoored weights, compromised training pipeline).
7. **Defense Evasion (AML.TA0007)** — evading detection (adversarial inputs, mimicry).
8. **Discovery (AML.TA0008)** — exploring the target environment.
9. **Collection (AML.TA0009)** — gathering data (training data extraction, prompt harvesting).
10. **ML Attack Staging (AML.TA0010)** — preparing adversarial inputs (crafting prompts, generating adversarial examples).
11. **Exfiltration (AML.TA0011)** — stealing model weights, training data, or sensitive outputs.
12. **Impact (AML.TA0014)** — degrading, disrupting, or destroying the AI system (model DoS, evading safety filters, generating harmful content at scale).

(Plus ML-specific tactics like **AML.TA0012 Erode ML Model Integrity** and **AML.TA0013 Publish Poisoned Datasets** that don't map cleanly to ATT&CK.)

#### 4.2 Techniques

Each tactic has a set of techniques (e.g., under ML Attack Staging: AML.TA0010.000 Craft Adversarial Data, AML.TA0010.001 Generate Adversarial Examples via Gradient, AML.TA0010.002 LLM Prompt Injection). Techniques are documented with description, examples, mitigations, and references to published research or real-world incidents.

Selected notable techniques (illustrative, not exhaustive):

- **AML.T0002 Prompt Injection (LLM01)** — manipulating the LLM via crafted input.
- **AML.T0024 Erode Dataset Integrity** — inserting poisoned samples into the training set.
- **AML.T0020 Poison Training Data** — same, but as a supply-chain attack on data sources.
- **AML.T0007 Discover ML Model Family** — fingerprinting the model to choose attack strategy.
- **AML.T0011 LLM Jailbreak** — bypassing safety guardrails.
- **AML.T0008 ML Supply Chain Compromise** — compromising a third-party model or library.
- **AML.T0044 Full ML Model Theft** — extracting the full model via repeated API calls.
- **AML.T0048 Erode ML Model Integrity** — backdooring the model to misbehave on trigger inputs.
- **AML.T0051 LLM Metadata Exfiltration** — extracting system prompts or model configuration.

#### 4.3 Mitigations catalog

A separate catalog at atlas.mitre.org/mitigations enumerates defensive controls cross-referenced to the techniques they address. Selected notable mitigations:

- **AML.M0001 Limit Model Access** — restrict who can call the model and from where.
- **AML.M0002 Restrict Number of ML Models** — minimize model sprawl.
- **AML.M0003 Sanitize Training Data** — remove malicious or sensitive samples.
- **AML.M0004 Validate ML Model** — verify model behavior before deployment.
- **AML.M0005 Establish AI Supply Chain Controls** — vet third-party models, datasets, libraries.
- **AML.M0006 Control Access to ML Artifacts** — protect model weights and training data.
- **AML.M0007 Use Ensemble Methods** — combine multiple models to reduce single-model attack success.
- **AML.M0008 Adversarial Input Detection** — input classifiers and anomaly detection.
- **AML.M0009 Output Validation** — schema, semantic, and policy checks on model output.
- **AML.M0010 Model Hardening** — adversarial training, fine-tuning on known attacks.
- **AML.M0011 Model Watermarking** — embed a signature in the model to detect theft.
- **AML.M0012 Encrypt Sensitive Information** — encryption of training data and weights at rest and in transit.
- **AML.M0013 Code Signing** — verify integrity of ML pipeline components.
- **AML.M0014 Application Threat Modeling** — explicitly threat-model AI-specific risks.
- **AML.M0015 Human Review** — human-in-the-loop for consequential actions.

#### 4.4 Case studies

ATLAS documents real-world incidents (anonymized or with permission) including: Microsoft Tay (2016), the Meta Galactica withdrawal (2022), the ChatGPT prompt-injection exfiltration attacks (2023–2024), the Google Bard data leak, and dozens more. Case studies are the most valuable component of ATLAS for defenders — they show what actually happened, not just what could.

#### 4.5 How to use ATLAS

- **Coverage analysis.** Map your existing controls to the mitigations catalog; identify gaps.
- **Threat-informed defense.** Select the most relevant techniques (based on your threat model) and ensure mitigations exist for each.
- **Red-team planning.** Use the techniques as a basis for the red-team probe library.
- **Vendor assessment.** Ask vendors how their product addresses specific ATLAS techniques.

### 5. OWASP AI Security & Privacy Guide

**Document.** *OWASP AI Security & Privacy Guide*. Maintained by the OWASP AI Security & Privacy Guide project. Current version: 1.0. 200+ pages. Free, openly licensed.

**Purpose.** Comprehensive guidance for organizations building, breaking, or buying AI systems. Designed as a practitioner's complement to NIST AI RMF and ISO 42001 — more concrete and code-oriented than either.

#### 5.1 Audience framework: Builders, Breakers, Buyers

OWASP's structural choice is to organize guidance for three audiences:

- **Builders** — developers and ML engineers. Need: secure coding patterns, defensive architectures, model-training hygiene, deployment hardening.
- **Breakers** — red-teamers, security researchers, auditors. Need: threat taxonomy, attack patterns, test case libraries, scoring rubrics.
- **Buyers** — procurement, GRC, legal, executives. Need: due-diligence questionnaires, contract clauses, risk-assessment frameworks, vendor-comparison matrices.

This audience framework is unique among AI governance documents and is part of why the guide is widely cited.

#### 5.2 Major topic sections

- **AI threats and risks** — taxonomy of AI-specific threats across confidentiality, integrity, availability, privacy, and safety dimensions.
- **AI security controls** — concrete controls mapped to threats; specifies the *what* and the *how* in code-enforceable terms.
- **Privacy and AI** — data minimization, purpose limitation, consent, anonymization, de-identification, federated learning, on-device inference, differential privacy, homomorphic encryption.
- **Model and data lifecycle** — secure data collection, model training, model storage, model serving, model retirement; supply-chain integrity.
- **Deployment and operations** — production hardening, monitoring, incident response, model rollback.
- **Governance and compliance** — risk management, documentation, audit, certification alignment.
- **Sectoral guidance** — healthcare, finance, government, education, retail, critical infrastructure overlays.

#### 5.3 Relationship to other OWASP projects

- **OWASP Top 10 for LLM Applications** — the LLM-specific risk taxonomy (see §6).
- **OWASP CycloneDX** — software bill of materials (SBOM) standard, extended for ML (ML-BOM) to track model and data provenance.
- **OWASP SAMM** — software assurance maturity model, extended for AI.
- **OWASP ASVS** — application security verification standard, with AI-specific requirements.

#### 5.4 Active contributions to standards

OWASP AI Security & Privacy Guide contributors are actively engaged with:
- ISO/IEC working groups (contributing to ISO 42001 and related standards).
- EU AI Act implementation (advising on technical standards referenced by the Act).
- NIST AI RMF profiles (the Generative AI Profile and emerging sectoral profiles).
- The Bletchley Declaration and subsequent international AI safety commitments.

The guide is widely cited in EU and UK regulator consultations and in US federal AI procurement language.

### 6. OWASP Top 10 for LLM Applications (and the GenAI Security Project)

**Document.** *OWASP Top 10 for LLM Applications*. Originally published 2023; v1.1 archived; current work is under the **OWASP GenAI Security Project** with a 2026 release. Free, openly licensed.

**Purpose.** The de facto taxonomy of security risks in LLM applications. Used by security teams, procurement, and vendors to align on a common vocabulary.

#### 6.1 The 10 risks (v1.1, with 2026 update notes)

- **LLM01 Prompt Injection** — crafted inputs (direct or indirect) manipulate the LLM into ignoring instructions, performing unintended actions, or leaking data. The single highest-impact risk; responsible for the majority of real-world LLM incidents. The 2026 update introduces a sharper distinction between *direct* (user) and *indirect* (via retrieved content) injection.
- **LLM02 Insecure Output Handling** — insufficient validation of LLM outputs before they reach downstream systems (HTML rendering, SQL, shell, code execution). The XSS-into-prompt channel's mirror image.
- **LLM03 Training Data Poisoning** — tampering with the training data (or fine-tuning data) to introduce backdoors, biases, or capability degradation. Most relevant to foundation-model providers; lesser concern for downstream deployers.
- **LLM04 Model Denial of Service** — resource-heavy operations (long-context floods, recursive tool calls) that overload the model or its infrastructure. The LLM analog of traditional DoS.
- **LLM05 Supply Chain Vulnerabilities** — compromised components in the LLM stack: pre-trained models, training datasets, embedding models, vector stores, retrieval services, third-party plugins. The model itself is now a supply-chain artifact.
- **LLM06 Sensitive Information Disclosure** — the model inadvertently reveals training data, PII, system prompts, or other users' data through its outputs.
- **LLM07 Insecure Plugin Design** — plugins/tools with weak access control, insufficient input validation, or excessive privileges; the OWASP analog of insecure direct object references for the agent era.
- **LLM08 Excessive Agency** — the LLM-based agent has more functionality, permissions, or autonomy than necessary. Often the highest-impact risk in production agentic systems.
- **LLM09 Overreliance** — users or downstream systems depend on LLM outputs without adequate verification; hallucinations cause real harm. Distinct from LLM06 in that the disclosure is incidental rather than malicious.
- **LLM10 Model Theft** — unauthorized access to a proprietary model via weight extraction, distillation, or API abuse.

#### 6.2 The 2025/2026 update

The OWASP GenAI Security Project (succeeding the original Top 10) maintains a continuously updated list and introduces several new risk categories relevant to agentic systems:

- **System prompt leakage** (a sharper sub-class of LLM06).
- **Vector store poisoning** (a sub-class of LLM03 / LLM05).
- **Agentic tool misuse** (a sharper framing of LLM07/LLM08).
- **Multi-modal injection** (image, audio, video-based attacks distinct from text).
- **MCP and inter-agent trust** (new risks emerging from agent-to-agent communication protocols).

The updated list reflects the field's evolution from "LLM as a chatbot" to "LLM as an agent with tools and memory."

#### 6.3 How to use the Top 10

- **Threat modeling.** Use the Top 10 as a checklist during threat modeling for any LLM application.
- **Vendor assessment.** Ask vendors which Top 10 risks they address; ask for evidence (test results, documentation).
- **Education.** Use the Top 10 as a teaching tool for engineering teams new to LLM security.
- **Audit.** Cite the Top 10 in audit reports and risk assessments to ground claims in a shared vocabulary.

### 7. CISA / NSA / FBI / NCSC joint guidance

**Documents.** Two jointly-issued publications, both released November 2024:

- *"Guidelines for Secure AI System Development"*
- *"Guidelines for Secure AI System Deployment"*

**Authors.** CISA (US), NSA (US), FBI (US), NCSC (UK), and 21 other international cyber agencies (the "Five Eyes" plus allies including Germany, France, Japan, Australia, Canada, South Korea, and others).

**Purpose.** Authoritative US/Five-Eyes playbook for AI deployment security; intended to be referenced in federal procurement and defense AI contracts.

#### 7.1 Guidelines for Secure AI System Development (the development guidance)

Four pillars:

- **Secure design.** Threat-model AI-specific risks; define security requirements; integrate security-by-design principles; document assumptions and limitations.
- **Secure development.** Secure the supply chain (vet model and dataset sources; use signed model artifacts; track provenance); apply secure coding practices; conduct code review; manage secrets; sanitize training data; version control all artifacts.
- **Secure deployment.** Harden the deployment environment; network-isolate the model-serving infrastructure; implement authentication and authorization; protect model weights and configuration; use TLS everywhere; restrict network egress; implement rate limiting and DoS protection.
- **Secure operation and maintenance.** Monitor for anomalous behavior; log all model interactions; implement incident response; track and patch vulnerabilities; manage model updates and rollbacks; plan for model retirement.

#### 7.2 Guidelines for Secure AI System Deployment (the deployment guidance)

Companion document focused on the operator's responsibilities:

- **AI system inventory and asset management.** Know what AI is deployed, where, by whom, and what it accesses.
- **AI system access controls.** Strong authentication (MFA, phishing-resistant); RBAC; least privilege.
- **Data protection.** Encryption in transit and at rest; data minimization; anonymization; TDM opt-out respect.
- **Network security.** Segmentation of AI systems from general IT; egress controls; intrusion detection.
- **Logging and monitoring.** Comprehensive logging; AI-aware monitoring (prompt logs, response logs, classifier outputs); anomaly detection.
- **Incident response.** AI-specific playbooks (model rollback, output quarantine, user notification).
- **Third-party risk management.** Vendor assessment; contractual security requirements; ongoing monitoring.
- **Training and awareness.** Operator training on AI-specific risks; user training on safe use.

#### 7.3 Operational adoption

- **US federal.** Cited in FedRAMP and FedRAMP AI requirements; referenced in GSA and DoD procurement language.
- **UK.** NCSC adoption for government and critical-infrastructure AI.
- **Allied nations.** Used as a baseline by cybersecurity agencies in the 23 signatory countries.
- **Industry.** Increasingly required in enterprise procurement even outside government, especially for cloud and SaaS providers serving federal customers.

#### 7.4 Relationship to other guidance

- Complements NIST AI RMF (which is principle-level); CISA guidance is operational.
- Complements OWASP AI Security & Privacy Guide (which is more developer-focused); CISA guidance is more operator-focused.
- Provides a US-side anchor for international coordination; the UK NCSC and EU ENISA have similar (but distinct) guidance.

### 8. Vendor SDKs and APIs

#### 8.1 OpenAI

**Moderation API.** `omni-moderation-latest` — free endpoint; multi-modal text + image classification; categories: hate, harassment, self-harm, sexual, violence. Used as the foundational input/output filter in most OpenAI-based applications.

**OpenAI Safety best practices.** Public guidance recommending layered guardrails (moderation + system prompt + output validation), structured outputs to constrain tool calls, jailbreak-resistance via evals, and human-in-the-loop for high-stakes actions.

**OpenAI model cards.** Each released model has a system card describing the safety evaluations, the categories tested, the failure modes found, and the mitigations applied. Increasingly required reading for procurement.

**Function calling / structured outputs.** JSON Schema-constrained output that the SDK refuses to emit if the model output doesn't match. The most reliable defense against LLM02 Insecure Output Handling.

#### 8.2 Anthropic

**Constitutional AI.** Training-time harmlessness via self-critique against a written constitution (see defenses file §7.2).

**Responsible Scaling Policy (RSP).** Anthropic's commitment to only train or deploy models above certain capability thresholds after independent evaluation and demonstrated safety. RSP has graduated levels (ASL-2, ASL-3, ASL-4); each level has specific safety requirements.

**System cards.** Each major Claude release has a published system card describing evaluations, refusals, red-team findings, and the claimed RSP level.

**Tool use.** Claude's tool-use framework accepts a JSON Schema description of each tool; the SDK enforces the schema.

**Prompt caching.** Allows reuse of large system prompts across many requests, reducing cost and latency.

#### 8.3 Google

**ShieldGemma.** Open safety classifier family (2B/9B/27B) built on Gemma 2; downstream filter for dangerous content, harassment, hate speech, sexually explicit.

**Gemini API safety features.** Built-in safety filters across harm categories with adjustable thresholds; configurable blocklists; structured output; function calling.

**Google AI Studio / Vertex AI.** Managed environments with built-in safety tuning, content filtering, and evaluation tooling.

**Model cards.** Each Gemini release has a published model card with safety evaluations.

#### 8.4 Microsoft Azure

**Azure AI Content Safety.** The canonical Microsoft guardrail suite (detailed in the defenses file). Includes Prompt Shields (jailbreak / injection detection), Groundedness detection, Protected material, Task adherence, and harm-category classifiers.

**Azure AI Foundry / Azure OpenAI Service.** Pre-built integration with Content Safety; per-model-deployment content-filter policies; Defender for AI services for runtime threat detection.

**Copilot Studio / M365 Copilot.** Enterprise-grade AI assistant products with built-in content safety, audit logging, and admin controls.

**Model catalog.** Azure AI Foundry hosts models from OpenAI, Anthropic, Meta, Mistral, AI21, Cohere, and others — all with Content Safety integration.

#### 8.5 AWS Bedrock Guardrails

**Bedrock Guardrails.** Cross-model guardrails applicable to all foundation models on Bedrock (Claude, Llama, Mistral, AI21, Cohere, Amazon Titan). Six safeguard policies: content filters, denied topics, PII detection, contextual grounding, word/image filters, automated reasoning. Applies to model inference, agents, knowledge bases, and flows. Two tiers (Standard, Premium/Beta) trade latency, language support, and quality.

**Bedrock Agents.** Managed agent framework with built-in guardrail integration, KB retrieval, and code interpretation.

**Bedrock Knowledge Bases.** Managed RAG with built-in guardrails; can apply the same Guardrail policy to both retrieval and inference.

#### 8.6 Comparison

| Vendor | Strength | Weakness |
|---|---|---|
| OpenAI | Best developer ergonomics; mature moderation API | Closed model, closed safety training details |
| Anthropic | Strongest published safety commitments (RSP); Constitutional AI | Smaller model catalog |
| Google | Open model options (ShieldGemma, Gemma); strong research | Safety features less unified across surfaces |
| Microsoft Azure | Most comprehensive managed offering; Defender integration | Heavy Azure ecosystem dependency |
| AWS Bedrock | Cross-model guardrails; tight agent/KB integration | Less mature than Azure |

The right vendor depends on existing cloud commitments, regulatory requirements, and the specific safety features needed. Multi-vendor deployments (e.g., Claude for the application, OpenAI for moderation) are increasingly common as a defense-in-depth measure.

### 9. Industry-specific standards

#### 9.1 Healthcare — HIPAA + FDA + ONC

**HIPAA (45 CFR Parts 160, 162, 164).** The Health Insurance Portability and Accountability Act, specifically the Privacy Rule and Security Rule, applies to any AI tool that creates, receives, maintains, or transmits Protected Health Information (PHI) on behalf of a covered entity (healthcare provider, health plan, clearinghouse). Any AI vendor providing services to a covered entity must execute a Business Associate Agreement (BAA) before receiving PHI.

Key obligations:
- **Minimum necessary.** Use, disclose, or request only the minimum PHI necessary for the purpose.
- **De-identification.** Training data containing PHI must be de-identified per the Safe Harbor (18 identifiers removed) or Expert Determination (statistical) methods.
- **Security Rule.** Administrative, physical, and technical safeguards; access controls; audit logs; encryption; integrity controls.
- **Breach notification.** Breaches affecting > 500 individuals require notification to HHS, affected individuals, and (in some cases) the media within 60 days.
- **Enforcement.** HHS Office for Civil Rights (OCR) has increasing AI-related enforcement. Recent notable cases involved AI-powered clinical decision support and chatbots disclosing PHI.

**FDA — AI/ML-Enabled Medical Devices.** The FDA regulates "Software as a Medical Device" (SaMD) including AI/ML components. As of 2025–2026, > 1,000 AI/ML-enabled devices have been authorized. Key guidance:
- **Predetermined Change Control Plan (PCCP) guidance** (final, 2024). Allows manufacturers to specify in advance how the model will be updated post-market, without requiring a new clearance for every change. Material for the "always-learning" AI paradigm.
- **Good Machine Learning Practice (GMLP)** (joint with Health Canada and UK MHRA, 2021). Ten guiding principles for ML-enabled medical devices.
- **AI/ML Action Plan** (2021). FDA's roadmap for AI/ML oversight; ongoing.
- **Lifecycle approach.** FDA's Total Product Life Cycle (TPLC) approach for AI/ML emphasizes pre-market review, post-market surveillance, and ongoing quality assurance.

**ONC — HTI-1 (Health Data, Technology, and Interoperability: Protecting Care Access) final rule (2024).** Establishes transparency requirements for "decision support intervention" algorithms used in certified health IT. Developers must provide "source attributes" (e.g., the intervention's intent, the developer's contact information, funding source) and "quality measures" (e.g., validation testing, fairness assessments). Applies to ONC-certified Health IT Modules and to the developers that supply them.

#### 9.2 Finance — SR 11-7 + ECB AI guidance + sector overlays

**SR 11-7 (US Federal Reserve, Apr 2011).** *Guidance on Model Risk Management*. Three pillars:
- **Model development, implementation, and use.** Sound theoretical basis; appropriate assumptions; robust implementation; proper use.
- **Model validation.** Independent of development; ongoing; conducted by qualified staff; covers outcomes analysis, benchmarking, and sensitivity analysis.
- **Governance, policies, and controls.** Board and senior management oversight; policies and procedures; internal audit; documentation.

SR 11-7 applies to any model that "inputs data and produces outputs in the form of predictions, decisions, or recommendations" — explicitly including AI/ML. The guidance is enforced by the Federal Reserve, OCC, and FDIC, and is the de facto US banking-sector standard for AI/ML risk management.

**SR 11-7 attachment A.** Detailed supervisory expectations including model inventory, model tiering (higher tier = more scrutiny), validation frequency, and documentation requirements.

**OCC SR 2011-12 and interagency guidance.** Companion guidance from the OCC covering national banks. Aligned with SR 11-7.

**CFPB Circular 2023-09.** Emphasized that creditors using AI/ML models must still comply with anti-discrimination laws (ECOA/Reg B, FCRA). Models that produce disparate impact on protected classes are illegal regardless of intent.

**EU — ECB letter on AI (Oct 2024).** The European Central Bank's Supervisory Board sent a letter to all significant institutions outlining supervisory expectations for AI/ML. "Comply or explain" — banks not meeting the expectations must document why. Covers:
- **Governance.** Board-level oversight of AI; clear roles and responsibilities; AI risk as a category in the risk framework.
- **Risk management.** Identification, measurement, monitoring, and mitigation of AI-specific risks. AI risk integrated into operational, credit, and model risk.
- **Model risk management.** AI/ML models treated under the existing model risk management framework (analogous to SR 11-7) but with AI-specific considerations: explainability, data quality, third-party dependencies, ongoing monitoring for drift and bias.

**EU — DORA (Digital Operational Resilience Act, in force Jan 2025).** Applies to financial entities; includes ICT (information and communication technology) risk management, incident reporting, third-party risk management, and resilience testing. AI/ML systems that are ICT systems fall under DORA.

#### 9.3 Government — FedRAMP + EO 14110/14179

**FedRAMP.** The Federal Risk and Authorization Management Program is the US government standard for cloud service authorizations. FedRAMP 20x (launched 2024) is the next-generation authorization process, emphasizing automation, continuous monitoring, and reciprocity.

**FedRAMP AI Prioritization Initiative (Aug 2025 – Apr 2026).** A targeted fast-track for enterprise conversational AI cloud services. Eligibility criteria:
- FedRAMP 20x authorization.
- SSO, SCIM, RBAC, and data isolation.
- Demand from at least five CFO Act agencies.
- Meets AI-specific security requirements (training-data isolation, model governance, audit logging).

First three products certified early 2026: ChatGPT Enterprise, Gemini for Government, Perplexity Enterprise Pro. No new entrants accepted after the window closed in April 2026.

**Executive Order 14110 (Biden, Oct 30 2023).** *Safe, Secure, and Trustworthy Development and Use of AI*. Key provisions:
- **Dual-use foundation model reporting.** Developers of models trained above specified compute thresholds (> 10^26 FLOPs) must report training processes, ownership of model weights, results of red-team safety testing, and measures taken to meet safety standards.
- **Agency chief AI officers.** Each large federal agency must designate a chief AI officer.
- **Safety testing by DHS and VA.** DHS and VA designated to pilot AI safety testing.
- **NIST evaluation guidance.** Directed NIST to develop evaluation guidance for AI systems (resulting in the AI RMF and AI 600-1 profile).
- **FTC consumer protection.** Directed the FTC to use its authority to protect consumers from AI-related harms.
- **Biosecurity, CBRN.** Required agencies to study and address AI's potential to enable chemical, biological, radiological, and nuclear threats.
- **Federal procurement.** Required federal procurement guidelines for AI.

EO 14110 was **rescinded hours after Trump's Jan 20 2025 inauguration**.

**Executive Order 14179 (Trump, Jan 23 2025).** *Removing Barriers to American Leadership in Artificial Intelligence*. Replaces 14110 with a pro-innovation stance:
- Directs the OMB to rescind AI procurement guidance that "unduly burdens" innovation.
- Mandates an "AI Action Plan" within 180 days (delivered Jul 2025).
- Directs OSTP and NSF to prioritize AI research and infrastructure.
- Removes many of the safety-testing requirements from 14110.
- Directs agencies to identify and eliminate regulations that "unnecessarily hinder" AI development.

The practical effect: US federal AI policy has shifted from "AI safety as primary concern" (14110) to "AI innovation as primary concern" (14179). State-level legislation (especially California SB 1047, vetoed Sep 2024, and Colorado SB 24-205) and procurement requirements (FedRAMP, DoD) continue to impose substantive AI safety obligations even as federal direction softens.

#### 9.4 Other sectoral standards

- **Telecommunications.** ITU-T Y.3170-series and successor recommendations on AI/ML in networks. Reference for AI governance in telecom operators.
- **Education.** FERPA (US) for student data; sector-specific state laws (e.g., New York's restrictions on student-data-using AI); Department of Education guidance on AI in education.
- **Defense.** DoD AI Ethical Principles (2019, revised 2020); JAIC/DIU guidance for AI procurement.
- **Energy.** NERC standards for grid reliability; FERC orders on AI/ML in grid operations.
- **Insurance.** NAIC Model Bulletin on AI/ML (US, adopted by ~20 states); Solvency II AI guidance (EU/UK).
- **Legal.** ABA Model Rules on AI competence; jurisdiction-specific rules on AI in legal practice.
- **HR / Employment.** NYC Local Law 144 (automated employment decision tools audit); Illinois AI Video Interview Act; EU AI Act high-risk classification for employment AI.

### 10. Implementation playbook

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

## Layout-fix note

Frontmatter `promoted_to:` updated 2026-09-10 to reflect the wiki move from `wiki/ai-agent-wiki/<topic>/` to `wiki/ai-agent-wiki/knowledge/<topic>/`. The original leaf notes (and hubs) themselves are still valid; only the staged file's `promoted_to:` pointer needed an update.
