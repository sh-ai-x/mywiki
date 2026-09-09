---
tags: ["constitutional-ai", "ai-security", "guardrails", "red-team"]
priority: medium
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/18-strix"]
created: 2026-09-07
source: "_research/core-ai-security-defenses.md"
---

# Training-Time Defenses

> Training-time defenses shape the model itself. They are the most powerful defenses because they affect every downstream call, but they are also the most expensive (they require fine-tuning infrastructure) and the slowest to update (a fine-tune takes days to weeks to ship). They are mostly the res

Training-time defenses shape the model itself. They are the most powerful defenses because they affect every downstream call, but they are also the most expensive (they require fine-tuning infrastructure) and the slowest to update (a fine-tune takes days to weeks to ship). They are mostly the responsibility of the model provider, not the deployer, but understanding them is essential to choosing a model and understanding its residual risk.

#### 7.1 RLHF — Reinforcement Learning from Human Feedback

The default alignment technique for modern LLMs. The pipeline:

1. **Collect preference data.** Human annotators see pairs of model outputs and choose which is better (more helpful, more harmless, more honest).
2. **Train a reward model.** A separate model learns to predict the human preference given an (input, output) pair.
3. **Fine-tune the LLM.** Use PPO, GRPO, or a similar RL algorithm to update the LLM's weights to maximize the reward model's score.
4. **Iterate.** As the LLM improves, collect more preference data on its current outputs and repeat.

Strength: produces a model that is genuinely *aligned* — it prefers the right answer, not just the right format. Foundation of the helpful-but-harmless behavior in ChatGPT, Claude, Gemini, and Llama.

Limitation: the reward model is a target — a sufficiently capable attacker can find inputs that produce high reward but are actually bad (reward hacking). The model can also develop behaviors that look aligned to the reward model but aren't aligned to the underlying intent (sycophancy, surface compliance, etc.).

#### 7.2 Constitutional AI / RLAIF

Constitutional AI (Bai et al. 2022, arXiv:2212.08073) replaces the human-labeled harmlessness data with two phases:

1. **Supervised self-revision.** The model is given a written list of principles ("constitution") and asked to critique and revise its own responses to be consistent with them. Multiple rounds of revision. The result is a dataset of "improved" responses, with no human labels.
2. **RLAIF (RL from AI Feedback).** A separate AI model ranks pairs of responses by which is more consistent with the constitution. Those preferences are used to train a reward model, which is then used to RL-fine-tune the original model.

The result is a model that engages with harmful queries rather than refusing them wholesale — it explains why the request is harmful and offers safer alternatives, instead of "I cannot help with that". This is the technique that powers Claude's "helpful, harmless, honest" behavior.

Strength: dramatically cheaper than human labeling; model can be re-constitutioned without re-labeling. Limitation: the constitution is itself a human artifact; a constitution that lists the wrong principles produces a model that is misaligned at scale.

#### 7.3 Adversarial training

Fine-tune the model on a dataset of adversarial examples — prompt injections, jailbreaks, perturbed inputs, optimized suffixes. The model learns to recognize and refuse them at inference.

Strength: empirically reduces attack success rate on the included attacks by 50–80% in published studies.

Limitation: arms-race-prone. New attacks (which weren't in the training set) still work. Adversarial training on GCG suffixes does not stop AutoDAN; adversarial training on AutoDAN does not stop PAIR. Continual re-training is required. Also expensive: a single adversarial-training run can cost $100K–$1M in compute.

#### 7.4 Dataset sanitization

The pre-training and fine-tuning data is the most important input to model behavior. Modern sanitization pipelines include:

- **PII filtering.** Regex + ML-based detection of emails, phone numbers, SSNs, addresses, names. Replace with synthetic equivalents or drop.
- **CSAM filtering.** Hash-based (PhotoDNA, NCMEC hash list) and classifier-based filtering against known child sexual abuse material. Mandatory by law in most jurisdictions.
- **Toxicity filtering.** Document-level classifier (e.g., Perspective API, internal model) drops high-toxicity documents.
- **Perplexity-based outlier detection.** Compute per-document perplexity under the base model; documents with anomalously low or high perplexity are flagged for review. Adversarial text often has unusual perplexity distributions.
- **Deduplication.** Near-duplicate documents are deduplicated to prevent memorization amplification.
- **Source-reputation scoring.** Documents from low-reputation sources (e.g., newly-registered domains, known misinformation sites) are down-weighted or excluded.
- **Copyright-respect processing.** Filter or properly license copyrighted material; track provenance to support fair-use defenses and DMCA compliance.
- **TDM opt-out respect.** For EU deployments, respect Text-and-Data-Mining opt-outs per Article 4(3) of the DSM Directive.
- **Poisoning detection.** For fine-tuning data (which is much smaller), anomaly detection on the embedding distribution catches poisoning attacks where a small number of adversarial examples are inserted into a public dataset (e.g., split-view poisoning against public fine-tune corpora).

Google's "Responsible AI data pipeline" is the canonical reference implementation; Hugging Face's `datatrove` and similar libraries implement subsets of the same pipeline.

#### 7.5 Differentially private training

Differential privacy (DP) provides a mathematical guarantee that no individual training example contributed more than a bounded amount to the model's outputs. DP-SGD (Abadi et al. 2016) clips per-example gradients and adds calibrated Gaussian noise; the resulting model provably cannot memorize individual training examples.

Strength: a strong defense against training-data extraction attacks. The "extract training data from GPT-2" research and follow-up work on larger models rely on memorization; DP training reduces the success rate by orders of magnitude.

Limitation: DP training typically reduces model utility by 1–5% on standard benchmarks at moderate ε (ε ≈ 8) and more at strict ε (ε ≈ 1). Compute overhead is significant. Not yet standard for frontier LLM training, but increasingly standard for fine-tuning on sensitive data (medical, financial).

#### 7.6 Safety instruction tuning

Beyond RLHF/RLAIF, a separate supervised fine-tuning (SFT) pass on a curated dataset of safety instructions:
- "If the user asks for X, respond with Y refusal style and offer Z alternative."
- "If you are uncertain about a fact, say so rather than guessing."
- "If a tool call could be destructive, ask the user to confirm."

This is a cheaper, more controllable version of full RLHF and is increasingly used to enforce org-specific policies without re-running the full alignment pipeline.

#### 7.7 Mechanistic interpretability (Anthropic's research focus)

A research direction rather than a deployed defense, but worth tracking. The goal: understand the internal circuits of the model well enough to identify and modify the specific neurons that drive harmful behavior. Currently a research-scale technique; the long-term hope is that a mechanistic understanding will allow more targeted, more reliable safety fixes than RLHF.

## Related

- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — all defenses leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these defenses
