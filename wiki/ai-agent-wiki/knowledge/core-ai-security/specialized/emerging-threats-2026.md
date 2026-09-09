---
tags: ["prompt-injection", "jailbreak", "adversarial"]
priority: low
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/18-strix"]
created: 2026-09-07
source: "_research/core-ai-security-threats.md"
---

# Emerging Threats (2026)

> The threat landscape is broadening along five axes as of 2026:.

The threat landscape is broadening along five axes as of 2026:

1. **Multi-modal jailbreaks** that span text + image + audio simultaneously. The "Beginner's Guide to Visual Prompt Injections" (Lakera) and Nature Communications paper on VLM attacks in medicine (2025, 122+ citations) signal mainstream awareness.[^lakera-visual][^nature-vlm-medical]
2. **Voice cloning + agent hijack**: real-time voice-cloning models paired with agentic assistants. An attacker calls a help-desk agent, mimics a known employee's voice, and the voice-enabled agent authorizes a transfer or reveals a credential. Real-time voice-cloning models crossed the human-recognizable threshold in 2024–2025; their coupling with agentic assistants is the natural next step.
3. **Autonomous-agent collusion**: multi-agent systems where two compromised agents coordinate to extract data that neither could alone. Initial academic demonstrations in 2025; no disclosed incident yet, but multi-agent frameworks (CrewAI, AutoGen, LangGraph multi-agent, OpenAI Swarm) are increasingly common in enterprise.
4. **Model-on-model attacks**: one LLM as the attacker, another as the target. "LLM-as-attacker" frameworks (AutoDAN, Advprompter) automate red-teaming; the same techniques can be deployed adversarially. The boundary between red-team tooling and offensive tooling is thin.
5. **Encrypted-channel exfiltration** (Grok, Jul 2025): instructions encoded such that content filters cannot read them but the target model decodes them. Defense requires semantic-level filtering rather than token-level.[^grok-encrypted]

### 12.1 Why the threat gradient is still tilting up

Three structural factors argue against near-term stabilization:

- **Capability ceiling not yet reached**. Foundation-model capability is still increasing; new capabilities (longer context, more tool use, persistent memory, browser control) each create new attack surfaces.
- **Defense asymmetry**. Defending against prompt injection is provably hard: any system where instructions and data share the same channel is vulnerable to channel-injection. The dual-LLM pattern (Willison) is the most promising architectural mitigation but is incomplete.
- **Economic pressure**. Vendor safety investment must compete with capability investment. Safety regression incidents are documented (e.g., xAI Grok system-prompt leaks, EchoLeak in M365 Copilot, GitHub Copilot RCE) — suggesting market pressure to ship faster than to ship safely.

### 12.2 Defensive research fronts to watch (2026)

- **Formal verification of agent tool composition**: type systems that make "read_email → forward_email to attacker" unrepresentable.
- **Constitutional AI and rule-checking judges**: a secondary model that checks the primary model's outputs against an explicit ruleset before they execute.
- **Cryptographic provenance for prompts and tool descriptions**: signed prompt templates and signed MCP tool descriptions that the agent can verify before use.
- **Sandboxed agent execution environments**: e.g., gVisor-style isolation per tool call, so even a hijacked agent cannot reach host resources.
- **Adversarial training for IPI specifically**: include IPI examples in RLHF / DPO data so the model learns to ignore instructions in retrieved content — partial progress only.[^jailbreak-survey]

### 12.3 Federated learning attacks

Federated learning (FL) trains a shared model across many clients without centralizing their data. The threat model differs from centralized training:

- **Byzantine clients** (Blanchard et al., 2017): a single malicious client can corrupt the global model if its updates are naively averaged. Robust aggregation (Krum, Bulyan, Median-of-means) mitigates this but reduces convergence speed.
- **Model poisoning via gradient manipulation** (Bhagoji et al., 2019): the attacker controls a small number of clients and crafts gradient updates to push the global model toward a backdoor — *without* needing to compromise the central server.
- **Inference attacks in FL**: membership inference (Nasr et al., 2019) and property inference are amplified because an attacker can observe the *gradient updates* from honest clients across rounds, not just final model outputs.
- **Data reconstruction from gradients** (Zhu et al., 2019; Geiping et al., 2020): in some settings, individual training examples can be reconstructed from gradient signals — a much stronger attack than inference on a deployed model.

These are particularly concerning for federated-fine-tuning of LLMs, which is the dominant deployment pattern for on-device personalization (Apple Intelligence, Google Gemini Nano, etc.).

### 12.4 Quantum-relevant threats (forward-looking)

Not yet a *practical* attack class but worth tracking:

- **Shor's algorithm on lattice cryptography**: if cryptographically-relevant quantum computers arrive, model weights encrypted at rest with lattice-based schemes (ML-KEM, CRYSTALS-Kyber) become vulnerable. Most ML supply-chain signing schemes already use post-quantum primitives, but legacy deployments are exposed.
- **Grover's algorithm on hash-based defenses**: hash pinning of model weights (sha256, BLAKE3) loses half its effective security under quantum search. Migration to SHA-3-512 or larger hash outputs is recommended.
- **Adversarial advantage under quantum ML models**: variational quantum classifiers (VQCs) appear to have different adversarial robustness properties than classical neural networks. Early results suggest some quantum models are *more* robust to classical adversarial attacks but vulnerable to quantum-specific attacks.
- **Harvest-now-decrypt-later** for proprietary model weights transmitted over the network: encrypted snapshots cached today could be decrypted in 10–20 years.

### 12.5 Energy / side-channel inference (emerging)

Energy/power side-channels on AI accelerator hardware (GPUs, TPUs, custom ASICs) can reveal:

- **Layer activation patterns** that fingerprint which model family is running.
- **Token-level inference** from power-trace correlation (especially on edge / mobile NPUs).
- **Weight extraction** through power-side-channel correlation over millions of inferences.

Practical relevance is limited to co-located attackers (e.g., malicious cloud tenant on the same physical host); still, defense-in-depth should include physical isolation for high-value model weights.

### 12.6 AI-generated malware and phishing at scale

GenAI itself is an offensive tool. Documented 2024–2026 concerns:

- **Polymorphic malware**: LLMs generate functionally-identical but lexically-different malware variants to evade signature detection.
- **Hyper-realistic phishing**: voice cloning + personalized email generation (target's social media → tailored spear-phish) crosses the human-recognizable threshold.
- **Deepfake impersonation for KYC bypass**: documented in financial fraud reports from 2024.
- **AI-assisted vulnerability discovery**: AI agents (ChaGPT, Claude Code, Cursor) are increasingly used by offensive security researchers; the same capabilities lower the bar for malicious actors.

The asymmetry here mirrors the jailbreak asymmetry: defenders must catch every variant; attackers need only one to succeed.

### 12.7 Counterfactual / causal-jailbreak research

A 2025 research direction: prompts that exploit *known failure modes* of model reasoning (anchoring, framing, recency bias) rather than directly requesting disallowed content. Example: ask the model to *simulate* a character who would produce the harmful content. The model's roleplay machinery bypasses safety filters not because the prompt is malicious but because it asks the model to *predict* malicious behavior — which is treated as a neutral task.

This blurs the line between "user is asking for harm" and "user is asking what harm looks like," a distinction frontier models handle inconsistently.

---

## Related

- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — all threats leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these threats
