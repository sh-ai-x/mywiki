---
tags: ["privacy", "ai-security", "owasp", "llm-top-10"]
priority: medium
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/18-strix"]
created: 2026-09-07
source: "_research/core-ai-security-threats.md"
---

# Privacy Attacks

> The Carlini et al. (2021) GPT-2 extraction attack recovered names, phone numbers, email addresses, and physical addresses — verbatim — from a public model.[^carlini-extract-2021] The 2023 follow-up on `gpt-3.5-turbo-instruct` showed the same phenomenon on a production model.[^nasr-extract-2023] A

### 10.1 PII leakage through memorization

The Carlini et al. (2021) GPT-2 extraction attack recovered names, phone numbers, email addresses, and physical addresses — verbatim — from a public model.[^carlini-extract-2021] The 2023 follow-up on `gpt-3.5-turbo-instruct` showed the same phenomenon on a production model.[^nasr-extract-2023] A 2024 study ("Understanding PII Leakage in Large Language Models," Old Dominion University) measured **48.19% PII extraction rate** on GPT-3.5/4 in targeted prompts.[^old-dominion-pii]

### 10.2 Re-identification

Even when individual attributes are partially redacted, combining leaked model outputs with public datasets enables re-identification. The "anonymization is not a model property" finding (Staab et al., EMNLP 2024): the *information content* of training data persists in model weights even after explicit scrubbing.

### 10.3 Training data extraction via memorization

LLMs memorize "secrets" (random-looking strings repeated across many training documents — UUIDs, license keys, API tokens in scraped GitHub). Once memorized, they reproduce with low perplexity. The exposure metric (Carlini 2021) quantifies this; the practical implication is that any string ever seen more than ~100 times in training is recoverable.

### 10.4 Inference-time memorization

Even *unintended* memorization happens: a model trained on customer support transcripts can later, with the right prompt, replay those transcripts to other customers. This is the technical mechanism behind the Samsung ChatGPT leak (March 2023) — the data was submitted once, retained for training, and now lives in the model.[^samsung-leak]

### 10.5 Defenses

- **Training data deduplication** (Carlini et al., 2023): removing repeated training documents reduces memorization by an order of magnitude.
- **Differential privacy** (DP-SGD, Abadi et al. 2016): provable bounds on per-record leakage, at the cost of model utility.
- **Output filtering**: regex/ML filters scrubbing known PII patterns from outputs.
- **On-device inference**: keep the model out of the API economy so training data is bounded to a known corpus.

---

## Related

- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — all threats leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these threats
