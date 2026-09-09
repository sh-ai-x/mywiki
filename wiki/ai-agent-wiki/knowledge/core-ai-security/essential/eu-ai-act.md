---
tags: ["eu-ai-act", "ai-security", "nist-rmf", "iso-42001"]
priority: medium
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/00-index"]
created: 2026-09-07
source: "_research/core-ai-security-frameworks.md"
---

# EU AI Act — Regulation (EU) 2024/1689

> **Document.** *Regulation (EU) 2024/1689 of the European Parliament and of the Council laying down harmonised rules on artificial intelligence (Artificial Intelligence Act)*. Adopted 13 March 2024; entered into force 1 August 2024. ~450 pages. The world's first comprehensive horizontal AI regulat

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

## Related

- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — all frameworks leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these frameworks
