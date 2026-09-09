---
tags: ["prompt-injection", "adversarial", "ai-security", "owasp"]
priority: low
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/18-strix"]
created: 2026-09-07
source: "_research/core-ai-security-threats.md"
---

# Executive Summary

> The AI/ML security landscape in 2026 is qualitatively different from 2023. What began as a research curiosity (adversarial images, prompt injection demos) has matured into a multi-billion-dollar attack surface spanning LLM-powered SaaS, agentic workflows, and the open model-supply chain. Three st

The AI/ML security landscape in 2026 is qualitatively different from 2023. What began as a research curiosity (adversarial images, prompt injection demos) has matured into a multi-billion-dollar attack surface spanning LLM-powered SaaS, agentic workflows, and the open model-supply chain. Three structural shifts drive the escalation:

1. **LLMs became infrastructure**. Foundation models are now embedded in email clients (Microsoft 365 Copilot), IDEs (GitHub Copilot, Cursor), CRM systems, and help-desk platforms. Each integration is a new trust boundary that an attacker can cross via prompt injection rather than a CVE.
2. **Agents took action**. Function-calling and tool-use moved LLMs from "answer machines" to actors that send email, run code, and move money. Indirect prompt injection from tool outputs is now the dominant *real-world* attack class, not the academic one.
3. **Model hubs became package managers**. Hugging Face, PyPI, and Replicate are the npm-equivalents for AI, with similar typosquatting, malware, and dependency-confusion risks — but with the added twist that a malicious model checkpoint executes arbitrary code on deserialization (Python pickle).

The five most-damaging attack classes of the 2023–2026 window, ranked by observed real-world impact:

| Rank | Attack class | Why it matters |
|---|---|---|
| 1 | **Indirect prompt injection (IPI)** | The single largest source of disclosed enterprise AI incidents. Crosses every trust boundary: email→Copilot, doc→agent, web→chatbot. CVE-2025-32711 (EchoLeak) was a 9.3-CVSS zero-click IPI in M365 Copilot. |
| 2 | **Supply-chain compromise of pre-trained models / fine-tunes** | Pickle deserialization (RCE), trojaned weights, poisoned datasets. Hundreds of malicious Hugging Face uploads documented in 2024 alone. |
| 3 | **Agent tool-misuse / privilege escalation** | Auto-execution of destructive tools (delete_email, exec_shell) after IPI. MCP "tool poisoning" is a 2025-specific subclass. |
| 4 | **Training-data extraction / PII leakage** | Memorization in production LLMs is measurable; PII extraction rates of ~48% reported on GPT-3.5/4 in 2023 studies. |
| 5 | **Adversarial examples (image/audio)** | Still the canonical ML robustness threat; universal patches transfer across models and now target vision-language agents. |

Why escalation is accelerating rather than plateauing:

- **Defense lag**: There is no robust general defense against IPI. Output filtering is adversarial; structured tool arguments reduce but do not eliminate the attack.
- **Capability expansion**: Each new tool, browser plugin, MCP server, or memory feature is a new injection surface. Defenses must be re-evaluated per release.
- **Open-source proliferation**: Public model checkpoints, datasets, and MCP servers democratize attack research as much as defense research.
- **Regulatory pressure without enforcement**: EU AI Act, US Executive Orders, NIST AI 100-2 exist, but disclosures still lag incidents by months.

The remainder of this dossier covers the threat taxonomy in depth, anchored to OWASP LLM Top 10 (2025), NIST AI 100-2, and MITRE ATLAS, with citations on every claim and a chronological incident timeline spanning 2023–2026.

---

## Related

- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — all threats leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these threats
