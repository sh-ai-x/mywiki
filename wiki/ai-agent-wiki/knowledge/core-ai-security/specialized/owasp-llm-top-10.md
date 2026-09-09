---
tags: ["ai-security", "nist-rmf", "iso-42001", "eu-ai-act"]
priority: medium
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/00-index"]
created: 2026-09-07
source: "_research/core-ai-security-frameworks.md"
---

# OWASP LLM Top 10 (Standards Mapping)

> **Document.** *OWASP Top 10 for LLM Applications*. Originally published 2023; v1.1 archived; current work is under the **OWASP GenAI Security Project** with a 2026 release. Free, openly licensed

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

## Related

- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — all frameworks leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these frameworks
