---
topic: security-job-hunting-korea-2026-§3-skills
tags: ["career", "job-hunting", "security", "korea", "section", "skills", "ai-red-team", "isms-p", "global-first", "junior", "interview-prep"]
related: ["ai-agent-wiki/career-coaching/security-job-hunting-korea-2026/_index", "ai-agent-wiki/career-coaching", "ai-agent-wiki/core-ai-security/_index"]
sources:
  - https://isms-p.or.kr/qlfc/base/selectQlfcBaseDetail.do
  - https://zdnet.co.kr/view/?no=20260119093656
  - https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-2.pdf
  - https://www.giac.org/certifications/generative-ai-security-qualification
  - https://www.hackthebox.com/blog/new-ai-security-certifications
  - https://recruit.kakaobank.com/jobs/255172
  - https://m.bzpp.co.kr/recruit/detail/BR260706A00063
  - https://www.kimchang.com/en/insights/detail.kc?sch_section=4&idx=31868
created: 2026-09-10
updated: 2026-09-10
status: promoted
parent: ai-agent-wiki/career-coaching/security-job-hunting-korea-2026
section: §3
global-first-filter: applied
---

# §3 Required Technical Skills by Role Family

## §3 Required Technical Skills by Role Family

### 3.1 보안 SI 컨설턴트 (ISMS-P / 진단 / 모의해킹)

The bread-and-butter Korean security role. Skill profile:

- **ISMS-P 인증 컨설팅** — KISA 인증 심사 기준 232개 통제 항목 숙지. 인증 심사 경험 자체가 어드밴티지.[^isms-p-qual]
- **취약점 진단** — 웹 (OWASP Top 10), 모바일 (MASVS), 인프라 (Nessus/OpenVAS), 클라우드 (CSPM). 2026 트렌드는 ISMS-P 인증이 체크리스트 → 실전 모의해킹·취약점 진단 의무화로 강화 추세.[^zdnet-isms-reform]
- **모의해킹 (penetration testing)** — Burp Suite, Metasploit, C2 frameworks, AD attack paths. OSCP가 사실상 표준.
- **컴플라이언스 보고서 작성** — 경영진 대상 ISMS-P gap 분석서, 위험평가 보고서. 한글 작성 능력 + 도식화 스킬.

### 3.2 침해사고 분석 / IR / DFIR

- 디지털 포렌식 (Autopsy, EnCase, Volatility)
- 네트워크 포렌식 (Wireshark, Zeek)
- 메모리 포렌식, 멀웨어 분석 (IDA, Ghidra, x64dbg)
- EDR 운영 (CrowdStrike, SentinelOne, S1)
- Threat hunting / Sigma rules / YARA
- CTF / 보안 경연대회 입상 이력

### 3.3 클라우드 보안

- AWS Security Specialty / GCP Professional Cloud Security Engineer (자격증)
- CSPM (Wiz, Prisma Cloud, Lacework)
- IaC 보안 (Terraform + tfsec, CloudFormation + cfn-nag)
- K8s 보안 (Kubernetes Hardening Guide, Falco, Kyverno)
- CI/CD 파이프라인 보안 (GitHub Actions OIDC, Sigstore, SBOM)

### 3.4 AI 보안 (LLM red-team) — 2026's highest-leverage family

This is where the dev-harness-kit directly differentiates. Required skills:

- **OWASP Top 10 for LLM Applications** (2025/2026 edition) — full coverage of LLM01–LLM10.
- **Prompt injection**: direct, indirect (Greshake 2023 paper), multi-modal.
- **Agent-specific threats**: tool misuse, plan injection, MCP tool poisoning (Invariant Labs Apr 2025), privilege escalation.
- **LLM red-team methodology**: GCG / AdvPrompter / Crescendo / Skeleton Key.
- **AI supply chain**: Hugging Face pickle RCE, model-on-model attacks.
- **AI risk management frameworks**: NIST AI 100-2, NIST AI RMF, ISO/IEC 42001 (AI management), EU AI Act, **Korea AI Basic Act** (2026-01-22 발효).[^nist-ai100-2]
- **Korean AI security certs (emerging)**: SANS/GIAC GAIQ (Generative AI Security Qualification), SANS Foundational AI Security Cert, HTB AI Security, INE AI Security.[^sans-gaiq][^htb-ai]

The Korean 2026 job-preference for this skill family is now explicit: 카카오뱅크 lists LLM-attack tooling in JD, NHN lists LLM-based autonomous-agent attack automation, 한화에어로스페이스 lists "AI 전 직무" 경력직 상시채용.[^kakaobank-redteam][^nhn-redteam]

### 3.5 GRC (Governance / Risk / Compliance)

- ISMS-P 인증 심사원 (PIPC, KISA 등록)
- ISO 27001 / 27002 Lead Auditor
- ISO 27701 (개인정보보호)
- PCI DSS (금융 결제)
- HIPAA / GDPR (글로벌 클라이언트)
- **AI Basic Act 영향평가 (AI Impact Assessment)**: 신규 트랙. 법무법인 김&장이 "하위법령 정합 bureau" 출범 (2025-05-14) — 컴플라이언스 시장이 빠르게 제도화.[^kimchang-ai-act]

---

## Source definitions (this section)

- [^isms-p-qual]: ISMS-P 자격검정 안내, "응시자 자격 기준." https://isms-p.or.kr/qlfc/base/selectQlfcBaseDetail.do (accessed 2026-09-10)
- [^zdnet-isms-reform]: ZDNet Korea, "수술대 오른 ISMS-P…S2W, 실전형 모의해킹 '주목'." https://zdnet.co.kr/view/?no=20260119093656 (accessed 2026-09-10)
- [^nist-ai100-2]: NIST AI 100-2, "Adversarial Machine Learning: A Taxonomy and Terminology of Attacks and Mitigations." https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-2.pdf (accessed 2026-09-10)
- [^sans-gaiq]: SANS/GIAC, "Generative AI Security Qualification." https://www.giac.org/certifications/generative-ai-security-qualification (accessed 2026-09-10)
- [^htb-ai]: Hack The Box, "New AI Security Certifications for 2026." https://www.hackthebox.com/blog/new-ai-security-certifications (accessed 2026-09-10)
- [^kakaobank-redteam]: 카카오뱅크 채용, "모의해킹 및 취약점분석 담당자 (Red Team)." https://recruit.kakaobank.com/jobs/255172 (accessed 2026-09-10)
- [^nhn-redteam]: NHN클라우드 채용, "RedTeam/Penetration Testing 엔지니어." https://m.bzpp.co.kr/recruit/detail/BR260706A00063 (accessed 2026-09-10)
- [^kimchang-ai-act]: Kim & Chang, "Enactment of AI Basic Act and Launch of Lower Statute Alignment Bureau." https://www.kimchang.com/en/insights/detail.kc?sch_section=4&idx=31868 (accessed 2026-09-10)
