---
tags: ["ai-security", "nist-rmf", "iso-42001", "eu-ai-act"]
priority: medium
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/00-index"]
created: 2026-09-07
source: "_research/core-ai-security-frameworks.md"
---

# CISA / NSA / FBI Joint Guidance

> **Documents.** Two jointly-issued publications, both released November 2024:.

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

## Related

- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — all frameworks leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these frameworks
