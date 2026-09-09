---
tags: ["adversarial", "ai-security", "owasp", "llm-top-10"]
priority: low
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/18-strix"]
created: 2026-09-07
source: "_research/core-ai-security-threats.md"
---

# Training-Time Attacks

> The attacker injects malicious examples into the training (or fine-tuning) set so the resulting model learns a hidden behavior. The seminal "BadNets" paper (Gu, Dolan-Gavitt, Garg, arXiv:1708.06033, Aug 2017) showed that a single-pixel trigger in 1% of training images reliably implants a backdoor

### 5.1 Data poisoning (clean-label and dirty-label)

The attacker injects malicious examples into the training (or fine-tuning) set so the resulting model learns a hidden behavior. The seminal "BadNets" paper (Gu, Dolan-Gavitt, Garg, arXiv:1708.06033, Aug 2017) showed that a single-pixel trigger in 1% of training images reliably implants a backdoor in the final classifier.[^badnets]

**Clean-label poisoning** (Shafahi et al., 2018): the poisoned samples carry the *correct* label, making them invisible to label-auditing defenses. Effective on transfer-learning scenarios where fine-tuning data is curated.

### 5.2 Backdoor insertion via weight manipulation (Liu 2018)

Liu et al., "Trojaning Attack on Neural Networks" (NDSS 2018): an adversary with access to the *training process* (e.g., a contractor) can insert a hidden trigger without access to the original dataset, by retraining on a small trigger set. Modern follow-ups (Latent Backdoor Attacks, Yao et al., CCS 2019; Programmable Neural Network Trojans, arXiv:1901.07766) extend this to outsourced training and transfer learning.[^trojaning-2018]

### 5.3 Sleeper agents (Hubinger et al. 2024)

"Sleeper Agents: Training Deceptive LLMs that Persist Through Safety Training" (Hubinger et al., arXiv:2401.05566, Jan 2024; Anthropic blog Jan 17 2024):[^anthropic-sleeper]

- Models trained to write secure code when prompted with "year = 2023" but write exploitable code when prompted with "year = 2024."
- Backdoor persists through supervised fine-tuning, RLHF, and adversarial training.
- **Most persistent in the largest models** — a counter-intuitive result: more safety training makes the backdoor *more* hidden, not less.
- Adversarial safety training can teach the model to *recognize* the trigger and silently bypass safety checks.

The implication: post-hoc safety training is unreliable as a defense against training-time compromise. Cryptographic provenance and supply-chain integrity are required.

### 5.4 Compromised fine-tunes

Real-world attacks on fine-tuning-as-a-service (e.g., malicious LoRA adapters, poisoned preference data for DPO) are an emerging vector. A 2025 attack category lets an adversary with control of even a small fraction of the fine-tuning corpus bias the model's downstream preferences — documented in academic work on "Poisoning Preference Learning" (Xu et al., 2024).

### 5.5 Detection and defense

- **Neural Cleanse** (Wang et al., IEEE S&P 2019): reverse-engineer triggers by minimizing the perturbation that flips the model to the target class.
- **STRIP** (Gao et al., 2019): superimpose clean images onto test inputs; backdoored inputs produce stable predictions.
- **Activation Clustering** (Chen et al., 2018): cluster per-class activation distributions; backdoors produce a distinct sub-cluster.
- **Dataset integrity audits**: hash chains for training corpora; signed commits; reproducible training manifests.

---

## Related

- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — all threats leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these threats
