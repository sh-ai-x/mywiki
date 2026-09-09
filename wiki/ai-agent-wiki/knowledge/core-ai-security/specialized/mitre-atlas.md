---
tags: ["mitre-atlas", "ai-security", "nist-rmf", "iso-42001", "interview-prep"]
priority: high
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/00-index"]
created: 2026-09-07
source: "_research/core-ai-security-frameworks.md"
---

# MITRE ATLAS

> **Document.** *Adversarial Threat Landscape for AI Systems* (ATLAS). Maintained by MITRE, with contributions from Microsoft, Google, OpenAI, Anthropic, and academic researchers. Free, publicly available, regularly updated

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

## Related

- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — all frameworks leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these frameworks
