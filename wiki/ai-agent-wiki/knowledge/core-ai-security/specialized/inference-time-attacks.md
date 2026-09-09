---
tags: ["privacy", "ai-security", "owasp", "llm-top-10"]
priority: low
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/18-strix"]
created: 2026-09-07
source: "_research/core-ai-security-threats.md"
---

# Inference-Time Attacks

> "Membership Inference Attacks Against Machine Learning Models" (Shokri, Stronati, Song, Shmatikov; arXiv:1610.05820, Oct 2016; IEEE S&P 2017):[^shokri-mia].

### 6.1 Membership inference (Shokri et al. 2017)

"Membership Inference Attacks Against Machine Learning Models" (Shokri, Stronati, Song, Shmatikov; arXiv:1610.05820, Oct 2016; IEEE S&P 2017):[^shokri-mia]

- Given black-box access to a model's prediction probabilities and a candidate data record, determine whether the record was in the training set.
- Methodology: train "shadow models" on data with known membership, then train an *attack model* that predicts membership from the target's outputs.
- Demonstrated on CIFAR, Purchase-100, MNIST, and (later) large LMs.
- Mitigation: limit confidence output, calibration, differential privacy during training.

### 6.2 Model inversion (Fredrikson et al. 2015)

"Model Inversion Attacks that Exploit Confidence Information and Basic Countermeasures" (Fredrikson, Jha, Ristenpart; ACM CCS 2015; arXiv:1602.04069):[^fredrikson-inversion]

- Reconstruct representative training inputs from confidence scores.
- Demonstrated facial-recognition model → recognizable faces of training subjects; lifestyle-decision tree → demographic profiles.
- Mitigation: round confidence scores, restrict query interface, output only top-k labels.

### 6.3 Training data extraction from LLMs (Carlini et al. 2021, 2023)

**Carlini et al. 2021**, "Extracting Training Data from Large Language Models" (USENIX Security 2021):[^carlini-extract-2021]
- Generated text from GPT-2 1.5B, compared to a reference corpus, found hundreds of verbatim memorized samples.
- Recovered PII (names, addresses, phone numbers), URLs, code snippets, and boilerplate.
- Introduced the **exposure** metric: how much an output reveals memorized content.

**Nasr, Carlini et al. 2023**, "Scalable Extraction of Training Data from (Production) Language Models" (USENIX Security 2023):[^nasr-extract-2023]
- Repeated the attack on `gpt-3.5-turbo-instruct` and other production models.
- Confirmed memorization scales with model size and data repetition.

### 6.4 Side-channel inference

Timing attacks on model APIs (Ye et al., 2024 "Beyond the Request: Exploiting Response Leakage") recover prompt contents from response latency. Cache-timing attacks on self-hosted models can recover input tokens. Defense: constant-time inference paths (largely aspirational for modern transformer serving).

### 6.5 Model-stealing (extraction) — Carlini et al. 2024

"Stealing Part of a Production Language Model" (Carlini, Paleka, Dvijotham, Steinke, Hayase, Tramèr et al., arXiv:2403.06634, ICML 2024 — Best Paper):[^carlini-stealing]

- Cryptanalytic extraction of a non-trivial fraction of a *production* LM's weights using ~$20 of API queries.
- Implication: any API-exposed model can be partially cloned; alignment-by-API-only is fragile.

---

## Related

- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — all threats leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these threats
