---
tags: ["prompt-injection", "ai-security", "owasp", "llm-top-10", "interview-prep"]
priority: high
related: ["ai-agent-wiki/core-ai-security/_index", "ai-agent-wiki/core-ai-security/threats/_index", "ai-agent-wiki/core-ai-security/defenses/_index", "ai-agent-wiki/core-ai-security/frameworks/_index", "ai-agent-wiki/18-strix"]
created: 2026-09-07
source: "_research/core-ai-security-threats.md"
---

# Agent-Specific Threats

> LLM agents extend the model with tools (function calls), memory, and planning loops. Every new capability is a new attack surface

LLM agents extend the model with tools (function calls), memory, and planning loops. Every new capability is a new attack surface.

### 9.1 Tool misuse

When an agent has `exec`, `fetch`, `send_email`, `write_file`, etc., an IPI can instruct the model to use those tools against the operator's interest. The agent's actions are *valid* (the user granted the tool), but the *intent* has been hijacked.

### 9.2 Plan injection

An attacker injects a sub-plan into the agent's working memory. Because the planner treats memory as authoritative, the agent follows the injected plan. Conceptually the same as IPI but targeting the planning module rather than the response module.

### 9.3 Privilege escalation via tool composition

A model with read-only `read_email` and write-only `forward_email` can be coerced (via IPI) into "read email → forward email to attacker." Each individual tool call is in scope; the *composition* is the escalation.

### 9.4 Indirect prompt injection from tool outputs

The most common 2024–2026 pattern: a web-fetch or email-read tool returns content that contains attacker instructions. The agent reads the content, the instructions become part of the context, the agent acts. Microsoft 365 Copilot and GitHub Copilot both fall in this category (CVEs §3.4).

### 9.5 Multi-agent collusion (theoretical but emerging)

In multi-agent setups (AutoGen, CrewAI, LangGraph multi-agent, OpenAI Swarm), one compromised agent can issue instructions that other agents — which *trust* inter-agent messages — will execute. A "trust" boundary that did not exist in single-agent design now exists at the inter-agent message layer.

### 9.6 MCP-specific attacks (April 2025+)

The Model Context Protocol (MCP, Anthropic, Nov 2024) standardizes how agents consume external tool servers. In April 2025, **Invariant Labs** disclosed *tool poisoning* — attackers embed malicious instructions in the `description` field of an MCP tool that the LLM reads but the user doesn't see.[^invariant-mcp] Simon Willison's April 2025 analysis formalized related issues as "rug pulls" and "tool shadowing."[^willison-mcp]

OWASP published **MCP Top 10** with **MCP03:2025 Tool Poisoning** as a headline risk.[^owasp-mcp] Cloud Security Alliance (CSA) published a research note on IDE auto-execution abuse in July 2026.[^csa-mcp-ide] The **MCPTox** benchmark (arXiv:2508.14925, Aug 2025) systematically evaluates real-world MCP servers for the vulnerability.[^mcptox]

### 9.7 Named agent-related CVEs

| CVE | Date | Product | Class |
|---|---|---|---|
| CVE-2025-32711 EchoLeak | Jun 2025 | Microsoft 365 Copilot | IPI → context exfil (CVSS 9.3)[^msrc-echoleak] |
| CVE-2025-53773 | 2025 | GitHub Copilot | IPI → RCE[^gh-copilot-rce] |
| CVE-2025-59536 | 2025 | Claude Code | IPI (CVSS 8.7)[^securiti-echoleak] |
| CVE-2026-24299 Copirate 365 | 2026 | M365 Copilot | Command injection[^csa-copirate] |
| CVE-2026-24307 Reprompt | 2026 | Copilot Personal | Prompt rewrite bypass |
| CamoLeak | 2025 | GitHub Copilot | Leaks private source code via crafted repo content[^camoLeak] |
| RoguePilot | 2025 | GitHub Copilot | Indirect PI through repo → IDE execution[^roguePilot] |

### 9.8 Agent-threat taxonomy (operator perspective)

The defensive operator needs a layered taxonomy to assign mitigations:

1. **Pre-tool hardening**: constrain the tool set to the minimum; require typed schemas; reject free-form tool arguments.
2. **Tool-call authorization**: every tool invocation checked against a policy (action, target, blast radius); high-risk tools require human approval.
3. **Result sanitization**: treat every tool result as untrusted content (the same posture as user input); strip instruction-like phrases; tag with provenance.
4. **Memory hygiene**: persistent memory should be write-restricted and human-reviewed; arbitrary agent writes to memory are an IPI surface.
5. **Cross-agent trust**: in multi-agent setups, inter-agent messages must carry provenance and be treated as semi-trusted.
6. **Audit & replay**: every tool call must be logged with input, output, decision rationale, and human approval flag; full replay should be possible for incident analysis.

Microsoft's 2024 red-team findings emphasize that no single layer is sufficient — even a "perfect" prompt-injection classifier at layer 3 is bypassed by clever encoding or multi-step assembly.[^msft-redteam]

### 9.9 The MCP ecosystem in 2025–2026

MCP (Model Context Protocol, Anthropic, Nov 2024) reached production-grade adoption in 2025: Claude Desktop, Cursor, Cline, and several enterprise chat platforms all consume MCP tool servers. The attack surface scaled with adoption:

- **Supply chain of MCP servers**: third-party MCP servers hosted on npm and GitHub. No standard signature/scan; description fields are user-editable; no version pinning by default.
- **Tool description poisoning**: descriptions can change after installation ("rug pull") without user notice.
- **Cross-server tool shadowing**: one MCP server's tool description can reference and override another server's behavior.
- **IDE auto-execution**: when an IDE auto-runs an agent on file changes, a malicious repo file can be ingested and acted on before the user reviews it.

CSA published an explicit MCP risk note in 2026 documenting IDE auto-execution abuse patterns.[^csa-mcp-ide] OWASP's MCP Top 10 (2025) catalogs these as MCP01 (Token Theft), MCP02 (Tool/Function Misuse), MCP03 (Tool Poisoning), MCP04 (Data Exfiltration), MCP05 (Privilege Escalation), and beyond.[^owasp-mcp]

---

## Related

- [[ai-agent-wiki/core-ai-security/threats/_index|Threats sub-hub]] — all threats leaf notes
- [[ai-agent-wiki/core-ai-security/_index|Core AI Security hub]] — top-level hub
- [[ai-agent-wiki/core-ai-security/defenses/_index|Defenses sub-hub]] — sister sub-domain
- [[ai-agent-wiki/core-ai-security/frameworks/_index|Frameworks sub-hub]] — sister sub-domain
- [[ai-agent-wiki/18-strix|Strix (18)]] — exercises these threats
