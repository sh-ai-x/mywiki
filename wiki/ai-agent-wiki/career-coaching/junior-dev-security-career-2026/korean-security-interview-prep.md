---
tags: ["career", "job-hunting", "junior-security", "korea-2026", "ctf", "isms-p", "red-team", "blue-team", "interview-prep"]
related:
  - ai-agent-wiki/career-coaching/junior-dev-security-career-2026/_index
  - ai-agent-wiki/career-coaching/junior-dev-security-career-2026/required-technical-skills-junior-security
  - ai-agent-wiki/career-coaching/junior-dev-security-career-2026/korean-security-market-state
  - ai-agent-wiki/career-coaching/junior-dev-security-career-2026/certifications-worth-getting
  - ai-agent-wiki/career-coaching
  - ai-agent-wiki/job-hunting-priority
created: 2026-09-10
---

# Korean security interview prep

> **TL;DR**: Korean security interviews weight ISMS-P depth, KISA 가이드라인 familiarity, and CTF exposure more than US/EU equivalents. Topics shift by company tier — 금융/대기업 emphasizes regulatory + PCAP/log analysis; 보안 SI emphasizes pentesting + CTF-style practicals; 플랫폼 보안 is closer to SWE-with-security-depth. Codegate 2026 Junior Division is the intended entry point. Start blue-team → pivot to product-security or red-team in year 2–3.

The Korean security interview has a distinctive structure compared to the US/EU: more emphasis on regulatory knowledge, more emphasis on written tests, more emphasis on CTF-style practicals.

**Technical interview topics by company tier:**

- **대기업 / 금융 (KB / 신한 / 하나 / 삼성생명):** ISMS-P deep dive, 개인정보보호법 specifics, KISA 가이드라인 familiarity, network forensics (PCAP analysis), log analysis (regex + SIEM queries), crypto basics, social-engineering scenarios. The interview is usually a 4-hour process: written test (1 hr) + technical interview (1 hr) + behavioral (1 hr) + final round (1 hr).
- **보안 SI (SK Shieldus / AhnLab / S2W):** Pentesting fundamentals (web + network), vuln-scan interpretation, exploit development basics, KISA CVE 가이드, CTF-style practicals. Expect a hands-on practical: "this PCAP has a C2 callback, what is the IOC?" or "this code sample has a vulnerability, find and exploit it".
- **플랫폼 보안 (NAVER / Kakao / Coupang):** Web security deep dive, cloud-native security, supply-chain (SBOM, dependency confusion), DevSecOps workflow. The interview is the most product-engineering-focused — closer to a SWE interview with security depth.
- **스타트업 / 컨설팅:** Generalist + breadth. Expect "here's a startup's tech stack, audit it and present findings" as a take-home. Strong written deliverable expected.

**CTF exposure (the strongest single signal):**

- **Codegate CTF 2026** ([codegate.org](https://codegate.org/fairDash.do?hl=ENG)) — Korea's premier security conference and CTF. The **Junior Division** is specifically for those born 2008+, individual event, 24-hour duration, 20-team offline final at COEX. See [Codegate 2026 on CTFtime](https://ctftime.org/event/3292/). The junior division is the *intended* entry point for a 신입 security pro in 2026.
- **Other notable KR CTFs:** Whitehat Contest (매년), Samsung CTF, Hacktheon (KITRI 부설), Dreamhack Wargame (online, ongoing).
- **International CTFs as exposure (not required but signals breadth):** DEFCON CTF Qualifier (US), Google CTF, PlaidCTF, HITCON CTF (Taiwan), SECCON CTF (Japan).
- **The signal on a resume:** a write-up blog (or GitHub repo) showing your solutions to even one CTF challenge. The *artifact* is the signal, not the rank.
- **Preparation resources:** pwn.college (free, structured), HackTheBox (subscription), TryHackMe (free tier), CyberDefenders (blue-team focus).

**Red-team vs. blue-team career path:**

- **Red-team (offensive):** higher visibility, higher salary ceiling, harder entry. Signals: OSCP, OSWE, CTF write-ups, public PoCs for disclosed CVEs. Job titles: 침해사고 분석가, 모의해킹 컨설턴트, Red Team Operator, Pentester.
- **Blue-team (defensive):** steadier demand, broader entry, more openings at any single employer. Signals: SIEM/SOAR experience, IR runbooks, GRC/ISMS-P certifications, KISA 침해사고 분석 사례. Job titles: SOC Analyst, Security Engineer, 보안관제, GRC 컨설턴트, ISMS-P 인증심사원.
- **Hybrid / product-security:** the new 2026 sweet spot. Signals: DevSecOps workflow, threat modeling, code-review security skill, AI-security literacy. Job titles: Product Security Engineer, Application Security Engineer, AI Security Engineer.

A 2026 junior's optimal positioning: **start blue-team** (more entry-level openings, more ISMS-P/KISA regulatory exposure, faster cert path) → **pivot to product-security or red-team in year 2–3** as certifications and CTF exposure compound.

## Related

- [[_index|Junior SWE + Security Pro sub-hub]]
- [[required-technical-skills-junior-security|Required technical skills for junior security pro]]
- [[korean-security-market-state|Korean security market state]]
- [[certifications-worth-getting|Certifications worth getting]]
- [[../career-coaching|career-coaching major hub]]
- [[../../job-hunting-priority|job-hunting-priority]]
