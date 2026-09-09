---
tags: ["owasp", "llm-top-10", "2026", "prompt-injection", "excessive-agency", "supply-chain", "ai-security", "interview-prep"]
priority: critical
related: ["ai-agent-wiki/core-ai-security/essential/owasp-llm-top-10", "ai-agent-wiki/core-ai-security/essential/prompt-injection", "ai-agent-wiki/core-ai-security/essential/action-allowlisting", "ai-agent-wiki/core-ai-security/specialized/mitre-atlas", "ai-agent-wiki/00-index"]
created: 2026-09-08
source: "https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/"
---

# OWASP LLM Top 10 — 2026 Edition

> **The 2026 OWASP LLM Top 10 was released 2026-08-03 and rewrote the rankings** — same 10 categories, but **Excessive Agency jumped 3 places (#6 → #3)** reflecting real-world agent damage, and **Unbounded Consumption was reframed around "denial of wallet"** (cost asymmetry, not just DoS). Methodology: 75% community vote, 25% real-world incident data, **6,639 incidents reviewed** — the first time the ranking was weighted by actual breach data.

## The 2026 List (current as of 2026-09-08)

| Rank | ID | Risk | Severity thesis |
|---|---|---|---|
| 1 | LLM01:2026 | **Prompt Injection** | Input alters model behavior. Sources: typed user input, poisoned documents, tool responses, images, long-term memory. **Invisible Unicode** can smuggle instructions past human review. |
| 2 | LLM02:2026 | **Sensitive Information Disclosure** | Model exposes data it shouldn't — through answer text, **tool-call arguments, reasoning traces, retrieved chunks, logs, embeddings**, and timing / token-length side channels. |
| 3 | LLM06 → LLM03:2026 | **Excessive Agency** | LLM + tools = an actor. Root causes: excessive functionality, excessive permissions, excessive autonomy. **Biggest promotion** — reflects production agent damage. |
| 4 | LLM03 → LLM04:2026 | **Supply Chain** | Third-party models, datasets, LoRA adapters, conversion pipelines, serving frameworks are attack surface. **Pickle-serialized files execute arbitrary code on load**. "Slopsquatting" = attackers register names that AI-suggested dependencies hallucinate. |
| 5 | LLM04 → LLM05:2026 | **Data and Model Poisoning** | Adversary corrupts data or model artifacts so harmful behavior is **baked in**, not injected at runtime. Backdoors stay dormant until a trigger phrase appears. |
| 6 | LLM10 → LLM06:2026 | **Unbounded Consumption** | Reframed as **cost asymmetry**: attacker spends ~0 to trigger computation that costs the provider far more. **"Denial of Wallet" is now a legitimate finding.** |
| 7 | LLM09 → LLM07:2026 | **Misinformation** | Model produces credible-enough output that is acted on. Pushed up by **incident data** as model output started driving tool calls and feeding other agents without human review. |
| 8 | LLM07 → LLM08:2026 | **Hidden Context Exposure** | Renamed from "System Prompt Leakage" — covers everything assembled into context users aren't meant to see: **system instructions, retrieved policy text, tool schemas, workflow rules**. |
| 9 | LLM08 → LLM09:2026 | **Vector and Embedding Weaknesses** | Wherever similarity search sits between data and prompt, the embedding layer joins the trust boundary. **Cross-tenant leakage is the priority test case.** |
| 10 | LLM05 → LLM10:2026 | **Improper Output Handling** | Model output reaching downstream without validation. Generated Markdown → HTML enables XSS; generated SQL concatenated enables injection; generated shell args enable command execution. **Risk unchanged but well understood** — biggest drop in ranking. |

## What changed from 2025

**Methodology**: First weighted blend — 75% community vote, 25% real-world incident data (6,639 incidents). 2025 was community-vote only.

**No new categories, no removed categories** — the same 10 risk families returned, with these changes:

| Change | From 2025 → To 2026 | Why |
|---|---|---|
| Renamed | LLM07 *System Prompt Leakage* → LLM08 *Hidden Context Exposure* | Scope widened from "system prompts" to "everything in context users don't see" — covers retrieved policy text, tool schemas, workflow rules |
| Promoted 3 spots | LLM06 *Excessive Agency* → #3 | Production agent damage in 2024-2026 (EchoLeak, GitHub Copilot RCE, MCP tool poisoning) — biggest rank jump |
| Promoted 4 spots | LLM10 *Unbounded Consumption* → #6 | Reframed around cost asymmetry ("denial of wallet") as LLM usage grew; massive LLM-cost incidents in 2025 |
| Promoted 2 spots | LLM09 *Misinformation* → #7 | Driven by incident data — model output now drives tool calls and feeds other agents without human review |
| Demoted 1 spot | LLM03 *Supply Chain* → #4 | Slight relative shift; risk unchanged |
| Demoted 1 spot | LLM04 *Data and Model Poisoning* → #5 | Slight relative shift; risk unchanged |
| Demoted 1 spot | LLM08 *Vector and Embedding Weaknesses* → #9 | Slight relative shift; risk unchanged |
| Demoted 5 spots | LLM05 *Improper Output Handling* → #10 | **Biggest drop** — risk unchanged but well understood and easily tested |
| Unchanged | LLM01 *Prompt Injection* (#1) | Still the top; methodology reinforced it |
| Unchanged | LLM02 *Sensitive Information Disclosure* (#2) | Still #2 — wide attack surface (tool-call args, reasoning traces, embeddings, timing) |

**New cross-references** in 2026 (not present in 2025):
- **NIST AI 600-1** (Generative AI Profile) — every LLM01-LLM10 maps to a NIST action
- **MITRE ATLAS** — every LLM01-LLM10 maps to ATLAS techniques
- **CWE** — every LLM01-LLM10 maps to underlying CWEs (CWE-1427 for Improper Output Handling, etc.)
- **OWASP Top 10 for Agentic Applications** (released 2025-12-09) — Excessive Agency (LLM03:2026) maps directly to several agentic-AI risks

## How to use this list

1. **Threat-model your LLM app**: walk LLM01-LLM10 in order, score each risk 0-3 against your system
2. **Map to controls**: for each scored risk, find the matching defense in [[ai-agent-wiki/core-ai-security/practical/defense-in-depth-architecture|defense-in-depth]] (LLM01 → L3 retrieval filtering, LLM03 → L5 action allowlisting, LLM06 → L6 sandboxing, etc.)
3. **Verify with Strix**: see [[ai-agent-wiki/strix/threat-coverage|Strix threat coverage]] — Strix covers LLM01 / LLM03 / LLM05 directly, and the rest via the matched application-layer risks
4. **Compliance mapping**: for SOC 2 / ISO 42001 / EU AI Act alignment, the [[ai-agent-wiki/core-ai-security/essential/nist-ai-rmf|NIST AI RMF]] + [[ai-agent-wiki/core-ai-security/practical/iso-iec-42001|ISO 42001]] + [[ai-agent-wiki/core-ai-security/essential/eu-ai-act|EU AI Act]] notes all cross-reference LLM01-LLM10

## Sources

- [OWASP GenAI LLM Top 10 2026 (official page, published 2026-08-03)](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/) — authoritative source
- [OWASP Top 10 for Large Language Model Applications (project root)](https://owasp.org/www-project-top-10-for-large-language-model-applications/) — cross-reference hub
- [HackerDNA — OWASP LLM Top 10 (2026): What Changed and How to Test](https://hackerdna.com/blog/owasp-llm-top-10) — detailed change analysis
- [CSA Research Note: OWASP GenAI Top 10 2026 + Agent Control Standard](https://labs.cloudsecurityalliance.org/research/csa-research-note-owasp-genai-top10-2026-agent-control-stand/) — companion agentic-AI coverage
- [OWASP Top 10 for Agentic Applications 2026](https://cycode.com/blog/owasp-top-10-agentic-applications/) — the related agentic list (Dec 2025)
- [[ai-agent-wiki/core-ai-security/essential/owasp-llm-top-10|OWASP LLM Top 10 — 2025 Edition]] — the prior list (preserved as historical reference)

## Related

- [[ai-agent-wiki/core-ai-security/essential/owasp-llm-top-10|OWASP LLM Top 10 — 2025 Edition]] — the prior version (historical reference)
- [[ai-agent-wiki/core-ai-security/essential/prompt-injection|Prompt Injection]] — LLM01 deep dive
- [[ai-agent-wiki/core-ai-security/essential/action-allowlisting|Action Allowlisting / Least-Privilege for Agents]] — LLM03 (formerly LLM06) mitigation
- [[ai-agent-wiki/core-ai-security/specialized/mitre-atlas|MITRE ATLAS]] — tactic mapping
- [[ai-agent-wiki/core-ai-security/essential/nist-ai-rmf|NIST AI RMF]] — control mapping
