---
tags: ["adversarial", "ai-security", "owasp", "llm-top-10"]
priority: low
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/18-strix"]
created: 2026-09-07
source: "_research/core-ai-security-threats.md"
---

# Adversarial Examples

> "Intriguing properties of neural networks" (Szegedy, Zaremba, Sutskever, Bruna, Erhan, Goodfellow, Fergus; arXiv:1312.6199, Dec 2013):[^szegedy-2013].

### 7.1 Input perturbation (Szegedy 2013, Goodfellow 2014)

"Intriguing properties of neural networks" (Szegedy, Zaremba, Sutskever, Bruna, Erhan, Goodfellow, Fergus; arXiv:1312.6199, Dec 2013):[^szegedy-2013]

- First demonstration that imperceptible, optimization-crafted perturbations to images cause state-of-the-art classifiers to misclassify with high confidence.
- Introduced the L-BFGS-based attack (minimize ‖δ‖ subject to misclassification).

"Explaining and Harnessing Adversarial Examples" (Goodfellow, Shlens, Szegedy; arXiv:1412.6572, Dec 2014): introduced the **FGSM** (Fast Gradient Sign Method) — a single-step linear approximation of the perturbation.

### 7.2 Universal adversarial perturbations

Moosavi-Dezfooli et al., "Universal adversarial perturbations" (CVPR 2017): a *single* image-agnostic perturbation vector fools a network on most natural images. Demonstrated across VGG, ResNet, GoogLeNet on ImageNet. Critical for physical-world attacks: print one sticker, fool many inputs.[^universal-adv]

### 7.3 Adversarial patches (Brown et al. 2017)

"Adversarial Patch" (Brown, Man, Roy, Čech, Ba; arXiv:1712.09665, Dec 2017): a localized, printable patch (think a sticker) that causes targeted misclassification regardless of where it appears in the image. Foundation for real-world attacks on autonomous-vehicle perception.

### 7.4 Physical-world attacks

- Sticker attacks on stop signs (Eykholt et al., CVPR 2018): robust under lighting, angle, and distance variation.
- Eyeglass-frame attacks on face recognition (Sharif et al., CCS 2016).
- 3D-printed turtle misclassified as rifle (Athalye et al., ICML 2017).

### 7.5 LLMs are differently vulnerable

Text is discrete; the classical L-BFGS / FGSM attacks don't apply directly. The LLM analogues are:
- Token-level adversarial paraphrases that preserve meaning but flip classification (textfooler, BERT-attack).
- Discrete GCG-style suffix optimization (Zou et al. 2023, §4.4).
- Continuous-space attacks on embeddings (HotFlip, Ebrahimi et al., ACL 2018).

Multi-modal LLMs unify the two: a *pixel* perturbation can now cause a vision-language model to misclassify or follow attacker instructions, fusing the classical image-attack and modern IPI threat models.[^mdpi-visual-pi]

### 7.6 Why classical defenses are necessary even for LLM products

Many production LLM pipelines still embed vision components — OCR, document-understanding, video-frame analysis — that remain classically vulnerable. A document-classifier that triggers an LLM workflow on detected "invoice" images can be defeated by an adversarial patch that fools the classifier into misclassification (denial of service) or *into* misclassification as a different document type that routes to a different downstream tool (escalation).

Adversarial robustness therefore remains a first-class concern even when the headline product is an LLM. The MITRE ATLAS AML.T0013 (Craft Adversarial Data) and AML.T0015 (Evade ML Model) techniques formalize these attack patterns at the AI-system level.[^mitre-atlas]

### 7.7 Audio and speech adversarial examples

Adversarial audio (Carlini & Wagner, 2018; Schönherr et al., 2018; CommanderSong, 2019) hides commands in music, speech, or white noise so a voice-activated agent obeys the attacker while humans hear only the cover audio. The 2025 threat landscape adds:

- **Audio over-the-air** attacks on smart speakers (Yuan et al., 2024): perturbations that survive room acoustics, distance, and microphone distortion.
- **Voice-agent hijack**: combining voice cloning with adversarial-audio embedding so an attacker sounds like a legitimate user *and* triggers actions the legitimate user never authorized.

This is now a real-world concern for any LLM agent with a microphone.

### 7.8 Transferable perturbations

Adversarial perturbations *transfer* across models — a perturbation crafted to fool Model A often fools Model B trained on a different dataset or architecture. The implications:

- **Black-box attacks via transfer**: an attacker can craft perturbations using a local surrogate model and deploy them against an opaque API.
- **Cross-architecture transfer**: CNN → ViT transfer is weaker but non-zero; perturbations trained on ResNet frequently fool VGG and Inception.
- **Cross-modality transfer**: image perturbations have been shown to retain some adversariality when processed by VLMs (§7.5).

This is the foundational property that makes adversarial examples a *systemic* risk rather than a per-vendor research curiosity.

### 7.9 Defenses — adversarial training

**Adversarial training** (Goodfellow et al. 2014; Madry et al. 2017): augment training data with adversarial examples so the model learns robust features. Standard recipe — PGD-based min-max optimization. Limitations: 2–10× training cost; only robust to the attack used during training; degrades on clean accuracy.

**TRADES** (Zhang et al., ICML 2019): explicit trade-off between robustness and natural accuracy via a theoretically-grounded surrogate loss. Reduces the robustness–accuracy trade-off cost.

### 7.10 Defenses — defensive distillation

**Defensive distillation** (Papernot et al., 2016): train a student model to match the *probability distribution* (softmax at temperature T) of a teacher model rather than its hard labels. Smooths the decision surface, reducing gradient-based attacks. Limitations: ineffective against C&W attacks that optimize for logit margins rather than softmax.

### 7.11 Defenses — randomized smoothing

**Randomized smoothing** (Cohen et al., ICML 2019): wrap the classifier with Gaussian noise sampling; the smoothed classifier provably certifies an L2 robustness radius. Currently the strongest *certified* defense for image classifiers. Limitations: degrades clean accuracy; does not naturally extend to text or arbitrary classifiers.

### 7.12 Defenses — input preprocessing

Preprocess inputs to remove or reduce adversarial perturbation:
- **JPEG compression / feature squeezing** (Xu et al., 2017).
- **Image quilting / total variation minimization**.
- **Autoencoder-based denoising** (Meng & Chen, 2017).

Effective as one layer of defense-in-depth; bypassed by attacks specifically tuned to the preprocessing.

### 7.13 Defenses — detection (rejection)

Train a separate binary classifier to flag adversarial inputs. Methods:
- **Feature squeezing detector** (Xu et al., 2017).
- **Neural invariant / dropout-based detector**.
- **Local intrinsic dimensionality** (Ma et al., 2018).

All detection methods suffer from *adaptive* attackers who craft adversarial examples specifically to fool the detector. Defense is a moving target.

### 7.14 Defense state-of-the-art (2026)

For *image classification* under L2 attack budget ε=1, certified defenses achieve >90% certified accuracy on CIFAR-10 with smoothed ResNet-110. Under L∞ budget, state-of-the-art is ~60% certified accuracy. For *LLMs*, no robust certified defense exists; adversarial training against GCG-style suffixes reduces but does not eliminate attack success rates.

Practical recommendation: combine adversarial training (model-side), input preprocessing (pipeline-side), and detection (gateway-side) for layered defense. No single layer is sufficient.[^nist-ai100-2]

---

## Related

- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — all threats leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these threats
