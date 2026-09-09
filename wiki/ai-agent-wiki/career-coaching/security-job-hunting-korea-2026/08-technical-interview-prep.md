---
topic: security-job-hunting-korea-2026-§8-tech-prep
tags: ["career", "job-hunting", "security", "korea", "section", "ctf", "red-team", "llm-red-team", "global-first", "junior", "interview-prep"]
related: ["ai-agent-wiki/career-coaching/security-job-hunting-korea-2026/_index", "ai-agent-wiki/career-coaching", "ai-agent-wiki/core-ai-security/_index"]
sources:
  - https://infosecmap.com/event/codegate-ctf-2026-finals/
created: 2026-09-10
updated: 2026-09-10
status: promoted
parent: ai-agent-wiki/career-coaching/security-job-hunting-korea-2026
section: §8
global-first-filter: applied
---

# §8 Technical Interview Prep (Korean Context)

## §8 Technical Interview Prep (Korean Context)

### 8.1 CTF 자격 (Capture-The-Flag competitions)

CTF는 한국 보안 채용에서 사실상 "오픈소스 포트폴리오" 역할. 상위 입상자는 신입이라도 6,000만원+ 오퍼 가능.

- **코드게이트 (Codegate) 2026**: 2026-03-28 예선, 2026-07-23~24 본선 (서울 코엑스). 총상금 7,100만 원. 2026년부터 "글로벌 펠로우십" 신설 — AI 화이트해커 육성.[^codegate-2026]
- **데프캠 (DefCamp)**: 루마니아 본사 + 한국팀 다수 본선 진출. DefCamp 성적은 글로벌 레퍼런스.
- **Pwn2Own / Pwn0rama**: 최상위 대회. 입상자는 1년+ 경력 인정.
- **CTF 플랫폼**: Hack The Box (월 구독), TryHackMe, DreamHack wargame, Webhacking.kr, Lord of SQL Injection.

**신입에게 기대하는 CTF 수준**: 본선 진출은 아니어도, Hack The Box Pro Hacker 랭크 + DreamHack 상위 30%면 충분히 strong signal.

### 8.2 보고서 작성 (after-action reviews, ISMS-P gap analysis)

대부분의 한국 보안 면접은 "30분 보고서 작성"을 포함한다. 작성 능력은 별도로 평가된다.

- **스타일**: 1) 요약 (경영진용 1 paragraph) 2) 현황 진단 3) Gap 분석 (표) 4) 권고사항 5) 실행 로드맵.
- **도식화**: 한컴오피스 한글 + 표 + 플로우차트. Word/PowerPoint 능숙 필수.
- **표준 템플릿**: KISA ISMS-P 인증 심사원 보고서 양식, NIST CSF, ISO 27001 Annex A 통제 매핑.

### 8.3 PT / 자기소개서 발표 (30분 PT)

대부분의 대기업·금융공기업 2차 면접은 **30분 자기소개서 발표**를 포함. 합격/불합격의 30–40%가 이 단계에서 갈린다.

- **구조**: 5분 자기소개 → 15분 핵심 프로젝트(dev-harness-kit가 여기 들어감) → 5분 Q&A → 5분 마무리.
- **핵심**: (1) 한 슬라이드 한 메시지 (2) 5–7 슬라이드 적정 (3) 도식 > 글자 (4) 데모 영상/스크린샷 포함.
- **시연**: dev-harness-kit의 `/dev-kit:security-metrics`를 라이브로 돌려서 scorecard 보여주는 슬라이드 1개 추가하면 차별화.

### 8.4 모의해킹 / IR 실기 (SI / Red Team 면접)

- **웹 모의해킹**: DVWA, Hack The Box, PortSwigger Web Academy (무료).
- **네트워크 모의해킹**: TryHackMe, Proving Grounds Practice.
- **포렌식**: CyberDefenders, Blue Team Labs Online.
- **실기 대비**: 노트북 + Burp + Metasploit + Wireshark 셋업 연습.

### 8.5 코딩 테스트 (대부분 대기업 1차)

- **언어**: Python (보안 자동화 = 사실상 표준) + Go/Rust (가산점).
- **문제 유형**: 문자열 처리, 네트워크 패킷 파싱, 로그 파싱, 시뮬레이션, BFS/DFS.
- **플랫폼**: 프로그래머스, 백준 (BOJ), LeetCode (글로벌 지원 시).
- **난이도**: 프로그래머스 level 2–3 (Gold 4–5) 정도면 충분.

### 8.6 LLM red-team 실기 (AI 보안 직무 — 2026 신규)

- **OWASP Top 10 for LLM Applications** 시나리오 기반 실기: "LLM-에이전트 시스템에서 간접 프롬프트 인젝션 방어해보기".
- **도구**: Lakera Guard, Promptfoo, Garak (open-source LLM vulnerability scanner).
- **시연**: dev-harness-kit의 `security` skill이 OWASP-style 리뷰를 자동화하는 것을 직접 시연하면 strong signal.

---

## Source definitions (this section)

- [^codegate-2026]: 코드게이트, "Codegate CTF 2026 Finals." https://infosecmap.com/event/codegate-ctf-2026-finals/ (accessed 2026-09-10)
