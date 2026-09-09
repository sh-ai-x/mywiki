---
tags: ["owasp", "prompt-injection", "jailbreak", "adversarial"]
priority: low
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/18-strix"]
created: 2026-09-07
source: "_research/core-ai-security-threats.md"
---

# Recommended Reading

> Curated reading list ordered by topic. Each entry is the single best starting point for that area

Curated reading list ordered by topic. Each entry is the single best starting point for that area.

### Foundations & taxonomy

1. **NIST AI 100-2**: "Adversarial Machine Learning: A Taxonomy and Terminology of Attacks and Mitigations." The canonical taxonomy; the basis for the AI/ML attack vocabulary used in this dossier.[^nist-ai100-2]
2. **MITRE ATLAS**: Adversarial Threat Landscape for AI Systems. ATT&CK-style matrix for AI/ML; the practical "what is the adversary doing now" reference.[^mitre-atlas]
3. **OWASP Top 10 for LLM Applications 2025**: industry-aligned threat taxonomy for LLM applications.[^owasp-2025]

### Prompt injection

4. **Greshake et al. (2023)**, "Not what you've signed up for" — the foundational paper on indirect prompt injection.[^greshake-ipi]
5. **Simon Willison's prompt-injection blog tag** — practitioner-focused commentary that often surfaces new attack patterns within weeks of disclosure.[^willison-prompt-injection]
6. **Microsoft AI Red Team blog (2024)** — concrete examples of indirect prompt injection, Crescendo, and Skeleton Key attacks against production systems.[^msft-redteam]

### Jailbreaks

7. **"Jailbreak and Guard Aligned LLMs: A Comprehensive Survey" (Sep 2024)** — the most thorough survey of jailbreak families and defenses.[^jailbreak-survey]
8. **Zou et al. (2023)**, "Universal and Transferable Adversarial Attacks on Aligned LLMs" — GCG paper; the foundation for automated suffix attacks.[^zou-gcg]
9. **"Multilingual Jailbreak Challenge in LLMs" (Oct 2023)** — the cross-language bypass attack.[^multilingual-jailbreak]
10. **"Many-shot jailbreaking" (Anthropic, Oct 2024)** — context-window saturation technique.

### Training-time & inference-time attacks

11. **Gu, Dolan-Gavitt, Garg (2017)**: "BadNets" — foundational backdoor-attack paper.[^badnets]
12. **Liu et al. (NDSS 2018)**: "Trojaning Attack on Neural Networks" — weight-level backdoor insertion.[^trojaning-2018]
13. **Hubinger et al. (Jan 2024)**: "Sleeper Agents" — Anthropic's demonstration that safety training fails to remove training-time backdoors.[^anthropic-sleeper]
14. **Shokri et al. (IEEE S&P 2017)**: "Membership Inference Attacks Against Machine Learning Models."[^shokri-mia]
15. **Fredrikson et al. (ACM CCS 2015)**: "Model Inversion Attacks that Exploit Confidence Information and Basic Countermeasures."[^fredrikson-inversion]
16. **Carlini et al. (USENIX Security 2021)**: "Extracting Training Data from Large Language Models."[^carlini-extract-2021]
17. **Nasr, Carlini et al. (USENIX Security 2023)**: "Scalable Extraction of Training Data from (Production) Language Models."[^nasr-extract-2023]
18. **Carlini et al. (ICML 2024 Best Paper)**: "Stealing Part of a Production Language Model."[^carlini-stealing]

### Adversarial examples

19. **Szegedy et al. (2013)**: "Intriguing properties of neural networks" — the foundational adversarial-examples paper.[^szegedy-2013]
20. **Goodfellow et al. (2014)**: "Explaining and Harnessing Adversarial Examples" — FGSM.
21. **Moosavi-Dezfooli et al. (CVPR 2017)**: "Universal adversarial perturbations."[^universal-adv]
22. **Brown et al. (2017)**: "Adversarial Patch" — printable physical attacks.
23. **Madry et al. (ICML 2018)**: "Towards Deep Learning Models Resistant to Adversarial Attacks" — adversarial training framework.
24. **Cohen et al. (ICML 2019)**: "Certified Adversarial Robustness via Randomized Smoothing" — strongest certified defense.

### Supply chain & agent threats

25. **HiddenLayer (Feb 2024)**: "Hugging Face Facesupply Chain" — pickle-deserialization RCE in model hubs.[^hiddenlayer-pickle]
26. **JFrog Security Research (2024)**: "Data Poisoning in Hugging Face Models."[^jrog-pickle]
27. **Invariant Labs (Apr 2025)**: "MCP Security Notification: Tool Poisoning Attacks."[^invariant-mcp]
28. **Simon Willison (Apr 2025)**: "Model Context Protocol has prompt injection security problems."[^willison-mcp]
29. **OWASP MCP Top 10**: catalog of MCP-specific risks including MCP03 Tool Poisoning.[^owasp-mcp]
30. **MCPTox benchmark (Aug 2025)**: systematic evaluation of tool-poisoning against production MCP servers.[^mcptox]

### Real-world incidents (chronological anchors)

31. **Samsung ChatGPT leak (Mar 2023)**: the canonical "employee pastes secrets into consumer LLM" case.[^samsung-leak]
32. **ChatGPT Redis incident (Mar 2023)**: the largest consumer-LLM data breach to date.[^chatgpt-redis]
33. **Air Canada chatbot ruling (Feb 2024)**: first major legal liability for LLM hallucination.[^air-canada-ruling]
34. **Replicate cross-tenant vulnerability (May 2024)**: cloud-hypervisor escape equivalent for AI-as-a-service.[^wiz-replicate]
35. **DeepSeek exposed database (Jan 2025)**: largest AI-side data leak of 2025.[^wiz-deepseek][^techcrunch-deepseek]
36. **CVE-2025-32711 EchoLeak (Jun 2025)**: zero-click IPI in M365 Copilot.[^msrc-echoleak][^aim-echoleak]
37. **CVE-2025-53773 (2025)**: IPI → RCE in GitHub Copilot.[^gh-copilot-rce]

### Practitioner-facing

38. **Cloud Security Alliance research notes** (2025–2026): regularly-updated practitioner guides on image-prompt injection, MCP auto-execution, command-injection variants.[^csa-image-prompt][^csa-mcp-ide][^csa-copirate]
39. **NIST AI 100-2** (re-listed for the practitioner audience): the single most authoritative reference for adversarial-ML vocabulary.[^nist-ai100-2]
40. **Embrace The Red blog** (Hasier Larrañaga): ongoing primary-source coverage of disclosed Copilot / Claude / Grok vulnerabilities.[^grok-prompt-leak][^gh-copilot-rce][^grok-encrypted]

### 13.3 Per-attack-class detection methods

Beyond high-level tooling, defenders rely on a small set of *signal classes* — measurable properties of inputs, model activations, or outputs that correlate with attack activity:

| Signal class | What it detects | Limitations |
|---|---|---|
| **Perplexity spikes** | GCG-style adversarial suffixes, encoding-based jailbreaks (base64/ROT produce high-perplexity token sequences) | Adversaries now optimize for low-perplexity attacks (PRM, AdvPrompter) |
| **Embedding drift** | Adversarial examples, poisoned fine-tunes (the model's internal representation shifts from baseline) | Requires maintaining a per-task embedding baseline; expensive |
| **Behavioral baselines** | Jailbreaks, IPI (the model's tool-call patterns deviate from training distribution) | Sensitive to legitimate distribution shift (new product, new user) |
| **Judge models** | All content-based attacks (a secondary LLM scores the primary's outputs for harm / policy violation) | Judge is itself jailbreakable; adversarial attacks against the judge are now documented |
| **Activation clustering** | Backdoors (per-class activations form distinct sub-clusters for trigger inputs) | Requires white-box access; offline analysis only |
| **Output entropy / refusal rate** | Over-refusal false positives; misalignment drift | High false-positive rate on legitimate edge cases |
| **Token-level provenance** | IPI from tool outputs (tag every tool-output token with its source URL/doc ID; downstream reasoning can use the tag) | Requires structured tool wrappers; not all tool ecosystems support |
| **Latency histograms** | Side-channel inference attacks, model-stealing extraction queries | Coarse signal; needs correlation with query patterns |
| **Cost-attribution spikes** | Unbounded-consumption / model-thealing | Needs billing-tagging infrastructure |
| **Prompt-template fingerprinting** | Known jailbreak families (DAN, Grandma, Crescendo) via fuzzy match against a curated corpus | Bypassed by paraphrased variants |

### 13.4 Continuous monitoring vs. point-in-time scanning

The 2024–2026 incident corpus makes one pattern clear: *point-in-time* red-teaming captures a snapshot, but capability expansions (longer context, new tools, new MCP servers) and capability regressions (safety drift during fine-tunes) shift the threat surface continuously. Continuous monitoring — automated nightly jailbreak suites, live IPI fuzzing against deployed endpoints, anomaly detection on tool-call streams — is necessary to keep pace.

Concrete recommendations:

- **Daily automated jailbreak suite** (HarmBench + a curated internal set) against every production model endpoint.
- **Live IPI canary documents** — synthetic email / doc / web pages with known injection payloads; if they don't trigger detection, the defender has a regression.
- **Behavioral anomaly detection on tool-call streams** — flag tool sequences that match known abuse patterns (e.g., "read file → search for credentials → forward to external URL").
- **Red-team rotation** — independent third-party red teams every 6 months; not just internal.
- **Safety regression tests in CI** — every model upgrade and every agent-config change runs a fixed battery of attack strings; failure blocks release.

---

## Related

- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — all threats leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these threats
