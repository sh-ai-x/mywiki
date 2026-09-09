---
tags: ["ai-security", "iso-42001", "owasp-ai", "governance", "interview-prep"]
priority: high
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/00-index"]
created: 2026-09-07
source: "_research/core-ai-security-frameworks.md"
---

# OWASP AI Security & Privacy Guide

> **Document.** *OWASP AI Security & Privacy Guide*. Maintained by the OWASP AI Security & Privacy Guide project. Current version: 1.0. 200+ pages. Free, openly licensed

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

## Related

- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — all frameworks leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these frameworks
