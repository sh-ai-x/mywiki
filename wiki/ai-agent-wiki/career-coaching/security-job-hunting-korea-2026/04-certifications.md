---
topic: security-job-hunting-korea-2026-§4-certifications
tags: ["career", "job-hunting", "security", "korea", "section", "certifications", "oscp", "isms-p", "global-first", "junior", "interview-prep"]
related: ["ai-agent-wiki/career-coaching/security-job-hunting-korea-2026/_index", "ai-agent-wiki/career-coaching"]
sources:
  - https://isms-p.or.kr/qlfc/base/selectQlfcBaseDetail.do
  - https://skyedaily.com/news/news_view.html?ID=234228&SKYEDAILY_MOBILE=1
  - https://owasp.org/www-project-ai-security-and-privacy-guide/
  - https://www.giac.org/certifications/generative-ai-security-qualification
  - https://www.hackthebox.com/blog/new-ai-security-certifications
created: 2026-09-10
updated: 2026-09-10
status: promoted
parent: ai-agent-wiki/career-coaching/security-job-hunting-korea-2026
section: §4
global-first-filter: applied
---

# §4 Certifications that Matter in Korea 2026

## §4 Certifications that Matter in Korea 2026

### 4.1 국가자격 (Korean national certs)

| 자격증 | 발급처 | 용도 | 2026 비고 |
|---|---|---|---|
| **정보처리기사** | 큐넷 (Q-net) | 개발 직무 기본 자격. 신입 지원 시 "있어야 하는" 자격. | 합격률 ~30–40% (회차별 변동). |
| **정보보안기사** | 큐넷 | 보안 직무 표준 자격. | 응시자격: 4년제 졸업 + 정보보호·개인정보보호 각 1년 경력.[^isms-p-qual] |
| **CPPG (개인정보보호사)** | 한국인터넷진흥원 | ISMS-P 인증 심사원 자격요건. | 보안 SI 컨설턴트의 사실상 필수. |
| **CISA / CISM** | ISACA | GRC / 관리 통제. | 한국어 시험 가능. |
| **CISSP** | (ISC)² | **2025-04 부로 한국 시험장 폐쇄**. 일본/싱가포르/홍콩 Pearson VUE 응시 필요. 응시료 ~$749. 비추천 (비용 + 여행).[^skyedaily-cissp] |

### 4.2 Offensive / Cloud

- **OSCP** (Offensive Security): 모의해킹/펜테스트 신입 → 경력 1–2년차에 가장 ROI가 높음. 한국 취득자 다수, 채용 시장에서 "있으면 플러스".
- **OSCE / OSEP / OSED**: OSCP 이후 단계. 3년+ 경력 때 도전.
- **AWS Security Specialty**: 클라우드 보안 직무 지원 시 어드밴티지. 한국어 시험 가능.
- **GCP Professional Cloud Security Engineer**: 동일.
- **CCSP (Certified Cloud Security Professional)**: 중립 클라우드 자격.

### 4.3 AI Security (2026 emerging)

아직 표준은 없지만 다음 5개가 빠르게 자리잡는 중:

1. **SANS/GIAC GAIQ** (Generative AI Security Qualification) — 가장 일찍 등장한 formal AI 보안 자격. SANS Institute curriculum 기반.[^sans-gaiq]
2. **SANS Foundational AI Security Certification** — 입문자용.
3. **INE AI Security Certification** — 공격자 관점.
4. **Hack The Box (HTB) AI Security Certifications** — 2026 신규. LLM exploitation, prompt injection, red team operations.[^htb-ai]
5. **CSA AI Security Certification** — vendor-neutral. 거버넌스 + 리스크 + 클라우드 AI.

**OWASP AI Security & Privacy Guide** (free)는 자격증은 아니지만, AI 보안 직무 면접의 사실상 표준 레퍼런스.[^owasp-ai-guide]

### 4.4 Cert-prioritization heuristic for 2026 Korean 신입

For a 신입 candidate without security industry experience, the highest-ROI cert stack is roughly:

1. **정보처리기사** (must-have for any IT role; not security-specific)
2. **정보보안기사** (the single most-asked Korean cert in security JDs)
3. **OSCP or HTB CPTS** (if pursuing offensive track)
4. **AWS Security Specialty or CCSP** (if pursuing cloud-security track)
5. **GAIQ or HTB AI Security** (if pursuing AI-security track — differentiator, since few candidates have this)

CISSP는 한국 신입 시장에서는 가성비 낮음 (5년 경력 요건 + 해외 응시). 3–5년 경력 이후에 도전.

---

## Source definitions (this section)

- [^isms-p-qual]: ISMS-P 자격검정 안내, "응시자 자격 기준." https://isms-p.or.kr/qlfc/base/selectQlfcBaseDetail.do (accessed 2026-09-10)
- [^skyedaily-cissp]: 스카이데일리, "[단독] '국제 보안 시험' CISSP, 한국 철수." https://skyedaily.com/news/news_view.html?ID=234228&SKYEDAILY_MOBILE=1 (accessed 2026-09-10)
- [^owasp-ai-guide]: OWASP AI Security & Privacy Guide. https://owasp.org/www-project-ai-security-and-privacy-guide/ (accessed 2026-09-10)
- [^sans-gaiq]: SANS/GIAC, "Generative AI Security Qualification." https://www.giac.org/certifications/generative-ai-security-qualification (accessed 2026-09-10)
- [^htb-ai]: Hack The Box, "New AI Security Certifications for 2026." https://www.hackthebox.com/blog/new-ai-security-certifications (accessed 2026-09-10)
