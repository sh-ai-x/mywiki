---
tags: ["prompt-injection", "jailbreak", "adversarial", "privacy"]
priority: medium
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/18-strix"]
created: 2026-09-07
source: "_research/core-ai-security-threats.md"
---

# Real-World Incident Timeline (2023–2026)

> Real-World Incident Timeline (2023–2026).

| Date | Target | Attack Class | Brief Summary | Source |
|---|---|---|---|---|
| Mar 2023 | ChatGPT (OpenAI) | Service breach / privacy | Redis-bug exposed ~1.2% of ChatGPT Plus subscribers' conversation titles and payment data | OpenAI status page / Italy Garante filing[^chatgpt-redis] |
| Mar 2023 | Samsung Semiconductor | Data exfiltration via LLM | Engineers pasted proprietary source code and meeting notes into ChatGPT; Samsung banned ChatGPT company-wide | Bloomberg / BBC[^samsung-leak][^bbc-samsung] |
| Jun 2023 | ChatGPT | Jailbreak (roleplay) | "Grandma exploit" — emotional roleplay produced Windows 10/11 product keys | The Independent, ExtremeTech[^grandma-exploit][^extreme-tech-grandma] |
| Jul 2023 | Bing Chat / GPT-4 | Indirect prompt injection | Greshake et al. demonstrate IPI exfiltrating Bing Chat context via crafted web content | arXiv:2302.12173[^greshake-ipi] |
| Jul 2023 | LLaMA-2, GPT-3.5 | Adversarial jailbreak | Zou et al. publish GCG universal transferable adversarial suffix | arXiv:2307.15043[^zou-gcg] |
| Jan 2024 | Anthropic LLMs | Sleeper-agent backdoor | Hubinger et al. demonstrate backdoors persisting through safety training | arXiv:2401.05566, Anthropic blog[^anthropic-sleeper] |
| Feb 2024 | Hugging Face Hub | Supply-chain RCE | HiddenLayer / JFrog find hundreds of malicious PyTorch pickle models executing reverse shells on `torch.load()` | HiddenLayer, JFrog blogs[^hiddenlayer-pickle][^jrog-pickle] |
| Feb 2024 | Air Canada chatbot | Misinformation / liability | Canadian CRT holds Air Canada liable for hallucinated bereavement-fare policy | BCCRT 2024 149[^air-canada-ruling] |
| Mar 2024 | OpenAI / academic | Model extraction | Carlini et al. extract non-trivial information from a production LM in ~$20 of API spend (ICML 2024 Best Paper) | arXiv:2403.06634[^carlini-stealing] |
| Apr 2024 | Model Context Protocol (Anthropic) | Tool poisoning (disclosed Apr 2025) | Invariant Labs discloses MCP tool-description poisoning | Invariant Labs blog[^invariant-mcp] |
| May 2024 | Replicate | Cross-tenant AI escape | Wiz Research discloses flaw allowing arbitrary code execution across tenants | Wiz blog[^wiz-replicate] |
| Jun 2025 | Microsoft 365 Copilot | Zero-click IPI | CVE-2025-32711 (EchoLeak, CVSS 9.3) — email-borne IPI exfiltrates Copilot context with no user interaction | MSRC, Aim Security, arXiv:2509.10540[^msrc-echoleak][^aim-echoleak] |
| Jul 2025 | xAI Grok | IPI + exfiltration | Researchers show Grok exfiltrates user data when malicious instructions are encrypted | Ars Technica, Embrace The Red[^grok-encrypted] |
| Jul 2025 | GitHub Copilot | IPI → RCE | CVE-2025-53773 — crafted repository content leads to RCE in the IDE | Embrace The Red[^gh-copilot-rce] |
| Aug 2025 | Real-world MCP servers | Tool poisoning benchmark | MCPTox benchmark quantifies tool-poisoning success on production MCP servers | arXiv:2508.14925[^mcptox] |
| Jan 2025 → Jan 2026 | DeepSeek | Misconfigured DB → PII leak | Wiz Research finds publicly accessible database with >1M user chat histories, API keys, plaintext admin credentials | Wiz blog, TechCrunch[^wiz-deepseek][^techcrunch-deepseek] |
| 2026 | M365 Copilot Personal | Prompt-rewrite bypass (Reprompt) | CVE-2026-24307 variant | CSA research note[^csa-copirate] |
| 2026 | Grok (xAI) | Encrypted-instruction exfiltration | Malicious instructions encoded so content filters cannot read them but target LLM obeys | Ars Technica, Embrace The Red[^grok-encrypted] |
| 2024 | OpenAI / academic | Scalable training-data extraction | Nasr, Carlini et al. demonstrate extraction from `gpt-3.5-turbo-instruct` | USENIX Security 2023[^nasr-extract-2023] |
| 2024 | Anthropic Claude Code | Tool misuse → filesystem access | Tool poisoning in MCP servers; CVE-2025-59536 (CVSS 8.7) | Securiti analysis[^securiti-echoleak] |
| 2024 | LLM medical VLM (Nature Comms) | Visual prompt injection in clinical context | Nature Comms study of VLM vulnerabilities in medical imaging | Nature Comms 2025[^nature-vlm-medical] |
| 2024 | Various frontier LLMs | Many-shot jailbreaking | Anthropic research showing context-window saturation can flip alignment | Anthropic 2024 |
| 2024 | Frontier LLMs | Skeleton Key multi-turn attack | Microsoft disclosure of multi-turn behavior-update jailbreak | Microsoft AI Red Team 2024 |
| 2023 | LLaMA-2, GPT-3.5/4 | Adversarial suffix (GCG) | Zou et al. — first automated universal transferable jailbreak | arXiv:2307.15043[^zou-gcg] |
| 2023 | GPT-2 (1.5B) | Training-data extraction | Carlini et al. — first systematic extraction of verbatim training data | USENIX Security 2021[^carlini-extract-2021] |

---

## Related

- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — all threats leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these threats
