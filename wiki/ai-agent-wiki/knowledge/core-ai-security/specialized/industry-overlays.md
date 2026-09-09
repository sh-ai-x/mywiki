---
tags: ["ai-security", "nist-rmf", "iso-42001", "eu-ai-act"]
priority: low
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/00-index"]
created: 2026-09-07
source: "_research/core-ai-security-frameworks.md"
---

# Industry-Specific Standards

> **HIPAA (45 CFR Parts 160, 162, 164).** The Health Insurance Portability and Accountability Act, specifically the Privacy Rule and Security Rule, applies to any AI tool that creates, receives, maintains, or transmits Protected Health Information (PHI) on behalf of a covered entity (healthcare pro

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

## Related

- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — all frameworks leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these frameworks
