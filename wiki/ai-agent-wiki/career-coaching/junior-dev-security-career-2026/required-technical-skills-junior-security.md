---
tags: ["career", "job-hunting", "junior-security", "korea-2026", "technical-skills", "owasp", "kisa", "ai-security", "interview-prep"]
related:
  - ai-agent-wiki/career-coaching/junior-dev-security-career-2026/_index
  - ai-agent-wiki/career-coaching/junior-dev-security-career-2026/korean-security-market-state
  - ai-agent-wiki/career-coaching/junior-dev-security-career-2026/korean-security-interview-prep
  - ai-agent-wiki/career-coaching/junior-dev-security-career-2026/certifications-worth-getting
  - ai-agent-wiki/career-coaching
  - ai-agent-wiki/job-hunting-priority
created: 2026-09-10
---

# Required technical skills for junior security pro

> **TL;DR**: Networking + Linux internals + web/cloud security + OWASP Top 10 + at least one scripting language (Python default) + one log/SIEM platform + one cloud security specialty + a CTF / capture-the-flag artifact. AI-security literacy (OWASP LLM Top 10 + MITRE ATLAS) is the 2026 differentiator.

The 2026 junior security signal stack: networking + Linux + web/cloud security + OWASP Top 10 + at least one scripting language + one log/SIEM platform + one cloud security specialty + a CTF / capture-the-flag artifact.

**Foundations (must know, not just "have heard of"):**

- **Networking** — TCP/IP stack, DNS, HTTP/2 + HTTP/3, TLS 1.3, BGP basics. The "what happens when I type google.com" answer must include the actual protocol layers.
- **Linux internals** — process model, file permissions, capabilities, namespaces, cgroups, systemd, journald, iptables/nftables basics. Security interviews at SK Shieldus / AhnLab expect a junior to be comfortable in a Linux shell.
- **Cryptography basics** — symmetric (AES-GCM), asymmetric (RSA, ECDSA, Ed25519), key exchange (Diffie-Hellman, X25519), TLS handshake, hashing (SHA-2/3), password hashing (Argon2id, bcrypt). Know the *why* of each primitive, not just the names.
- **Web security** — OWASP Top 10 (classic web), OWASP LLM Top 10 (for AI-adjacent roles), CWE top 25. See [OWASP LLM Top 10](https://owasp.org/www-project-top-10-for-large-language-model-applications/) for the AI side.
- **Cloud security** — IAM least-privilege, network segmentation, KMS, secrets management (Vault / AWS Secrets Manager), encryption at rest/in transit. AWS Security Specialty or Azure Security Engineer are the most-recognized certs here.

**Detection + response:**

- **SIEM** — Splunk, Elastic Security, QRadar, or one of the cloud-native ones (Sentinel, Chronicle, AWS Security Lake). Junior roles are typically tier-1 SOC analyst; expect to be tested on log parsing and correlation rules.
- **EDR** — CrowdStrike, SentinelOne, Defender for Endpoint, AhnLab EDR.
- **SOAR** — basic playbook authoring (Splunk SOAR, Cortex XSOAR). Junior-level competency is "I understand what a playbook is and can author a simple one".
- **Threat intelligence** — MITRE ATT&CK (the basis for most SOC work); MITRE ATLAS for AI threats; CVE / NVD; CISA KEV.

**Offensive / red-team (if pursuing red-team path):**

- **Web app pentesting** — Burp Suite, OWASP ZAP, manual SQLi / XSS / SSRF / SSTI / deserialization exploitation.
- **Network pentesting** — nmap, masscan, Metasploit, responder, bloodHound (AD).
- **Cloud pentesting** — Pacu (AWS), ScoutSuite, CloudGoat (training).
- **Mobile** — MobSF, Frida, objection (Android), Needle (iOS).
- **Binary / reversing** — Ghidra, IDA Free, radare2, pwntools, angr (only for reverse-engineering track).

**Scripting:**

- **Python** is the de facto security scripting language. Expect to write a log parser, a port scanner, a CVE PoC reproducer, or a regex-based YARA rule in the interview.
- **Bash** — fluency required for daily Linux ops.
- **PowerShell** — required for Windows-targeting roles.
- **Go** — a strong differentiator; many modern security tools (Caddy, Consul, Vault, Trivy, Tetragon) are written in Go, and reading them is a learning path.

**Korean-specific requirements:**

- **ISMS-P 인증 기준** — the Korean certification standard for information-security management. Know the 64 control items; know how they're audited; know the certification lifecycle. See [KISA ISMS-P](https://www.kisa.or.kr/eng/main.jsp).
- **개인정보보호법** — the primary statute. Know the definition of personal data, the consent regime, the breach notification rules, the cross-border transfer restrictions, the penalties (up to 5% of revenue). See [PIPC](https://www.pipc.go.kr/eng/main.do) and [법령 본문](https://www.law.go.kr/lsInfoP.do?lsiSeq=260917).
- **KISA 가이드라인** — KISA publishes dozens of technical guides (침해사고 분석, DDoS 대응, ransomware 대응, AI 보안). Junior-level familiarity expected at every Korean employer.
- **CTF exposure** — a CTF write-up portfolio is the strongest single differentiator. See [[korean-security-interview-prep|Korean security interview prep]].

**AI security (the 2026 differentiator):**

- **OWASP LLM Top 10** — LLM01 prompt injection, LLM03 excessive agency, LLM06 unbounded consumption. Every security interview in 2026 will probe this.
- **MITRE ATLAS** — adversarial threats to AI systems. Tactic/technique mapping is the same mental model as ATT&CK.
- **NIST AI 600-1** — the US GenAI risk profile; increasingly referenced in Korean procurement.
- **AI red-teaming** — manual + automated (Garak, PyRIT). The dev-harness-kit's `dev-kit:security` skill covers OWASP Top 10 + LLM01–LLM10 review.

## Related

- [[_index|Junior SWE + Security Pro sub-hub]]
- [[korean-security-market-state|Korean security market state]] — context
- [[korean-security-interview-prep|Korean security interview prep]] — how these skills are tested
- [[certifications-worth-getting|Certifications worth getting]] — the cert ROI ranking
- [[../career-coaching|career-coaching major hub]]
- [[../../job-hunting-priority|job-hunting-priority]]
