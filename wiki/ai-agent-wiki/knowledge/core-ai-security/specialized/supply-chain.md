---
tags: ["adversarial", "ai-security", "owasp", "llm-top-10"]
priority: medium
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/18-strix"]
created: 2026-09-07
source: "_research/core-ai-security-threats.md"
---

# Supply Chain

> In February–March 2024, security firms independently reported malicious PyTorch `.pt` / `.pth` checkpoints on Hugging Face Hub:.

### 8.1 Poisoned pre-trained models (Hugging Face 2024)

In February–March 2024, security firms independently reported malicious PyTorch `.pt` / `.pth` checkpoints on Hugging Face Hub:

- **HiddenLayer** (Feb 2024): identified models using pickle deserialization to spawn reverse shells on load.[^hiddenlayer-pickle]
- **JFrog Security Research** (Feb–Mar 2024): cataloged hundreds of malicious models with RCE payloads.[^jrog-pickle]
- Hugging Face responded with improved malware scanning (Picklescan) and progressive migration to `safetensors` (non-executable tensor format).

MITRE ATLAS technique **AML.T0020 Publish Poisoned Datasets** (and the model-equivalent) formalizes the attack category.[^mitre-atlas]

### 8.2 Malicious dependencies

- Training pipelines depend on data-processing libraries (pandas, scikit-learn, sentence-transformers). A compromised PyPI release can poison every downstream fine-tune.
- The 2022 `torchtriton` typosquat (a malicious PyPI package mimicking PyTorch's internal triton dependency) executed on `pip install` and harvested host info. Disclosed Dec 2022.[^pytorch-typosquat]

### 8.3 Compromised fine-tuning data

Public fine-tuning datasets (Alpaca, Dolly, OpenHermes, etc.) are aggregated from untrusted sources. Adversaries can seed adversarial examples into the wild, hoping downstream fine-tunes will scrape them. The OpenAI "GPT-3.5 turbo fine-tuning" launch (Aug 2023) and Llama-2 community fine-tunes (2023–2024) both rely on user-curated corpora with limited provenance.

### 8.4 Typosquatting / namespace confusion on model hubs

Just as `tensorflow-nightly` vs `tensroflow-nightly` exist on PyPI, Hugging Face repos can be typosquatted (e.g., `facebook/llama-2-7b` vs `facebook/llama-2-7B`). Organizations downloading "the same" model from a slightly-different repo may receive a poisoned checkpoint.

### 8.5 Replicate (May 2024) — cross-tenant AI execution

Wiz Research disclosed (May 2024) a critical vulnerability in Replicate's AI-as-a-service platform that allowed arbitrary model code execution across tenant boundaries — the AI equivalent of a cloud-hypervisor escape.[^wiz-replicate]

### 8.6 Defense pattern

- **safetensors** instead of pickle (Hugging Face default for new uploads since 2024).
- **Picklescan** and similar static analysis.
- **Cryptographic model signing** (Sigstore / cosign for ML weights).
- **Reproducible builds** with locked dependency hashes.
- **Provenance manifests** (e.g., C2PA-style for ML).

---

## Related

- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — all threats leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these threats
