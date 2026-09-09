---
topic: security-job-hunting-korea-2026-§11-90day-plan
tags: ["career", "job-hunting", "security", "korea", "section", "action-plan", "global-first", "junior", "interview-prep"]
related: ["ai-agent-wiki/career-coaching/security-job-hunting-korea-2026/_index", "ai-agent-wiki/career-coaching"]
sources:
  - https://blog.naver.com/kisa118/224098977736
  - https://aibasicact.kr/
created: 2026-09-10
updated: 2026-09-10
status: promoted
parent: ai-agent-wiki/career-coaching/security-job-hunting-korea-2026
section: §11
global-first-filter: applied
---

# §11 Action Plan — First 90 Days

90일을 6주 단위 3 phase로 구성.

## §11 Action Plan — First 90 Days

90일을 6주 단위 3 phase로 구성.

### 11.1 Phase 1: 기반 정리 (Day 1–21)

- **Week 1–2**:
  - dev-harness-kit README 전면 재작성. §5.5에 따라 security story를 상단에 배치. OWASP A01–A10 매핑 표 추가.
  - dev-harness-kit 자체에 `/dev-kit:security` 실행 → scorecard 캡처 → README에 인용.
  - LinkedIn 프로필 영문 + 한글 양국어 작성. "Open to Work" 활성화. 1-page summary 첨부.
  - 원티드 / 로켓펀치 / 잡코리아 / 사람인 프로필 동시 작성 (boilerplate 자기소개서 1개 + 4개 플랫폼 형식 맞춤).
  - GitHub Pages 또는 별도 페이지에 dev-harness-kit portfolio 페이지 작성 (README + 데모 영상).
- **Week 3**:
  - 정보처리기사 / 정보보안기사 응시 자격 확인 + 시험 일정 잡기. (정보처리기사: 매년 3회, 4·7·11월.)
  - OSCP / HTB CPTS 도전 시작 (가장 빠른 경로는 HTB CPTS — 3개월 완성 가능).
  - 한국 OWASP LLM Top 10 스터디 그룹 찾기. 한국 AI 보안 커뮤니티(예: AI Security Korea, AI Red Team KR) Discord/Slack 참여.

### 11.2 Phase 2: 포지셔닝 강화 (Day 22–60)

- **Week 4–5**:
  - 2~3개 회사별 cover letter 1-page 버전 작성. §9 hook을 회사에 맞게 변형.
  - 모의 PT 3회 (실제 30분 슬라이드 + 5분 Q&A). 녹화 → 셀프 리뷰 → 반복.
  - dev-harness-kit에 `/dev-kit:redteam` skill 추가 (실제로 OWASP LLM Top 10 자동 점검). 신규 commit → README 업데이트.
  - DreamHack / Webhacking.kr / Hack The Box 주 10시간 투자. 매주 writeup 1개 블로그 발행.
  - 코드게이트 2026 / 다른 CTF 예선 응시.
- **Week 6**:
  - 30개 기업 JD 분석. 직무 키워드 / 자격요건 / 우대사항 빈도 분석. dev-harness-kit의 어떤 기능이 어느 JD에 매칭되는지 매트릭스 작성.
  - 30개 기업에 우선순위 매기기 (매칭도 + 회사 선호도 + 합격 가능성). 상위 10개에 집중 지원.
  - 1차 서류 30개 제출. (대기업 공채 5개 + 금융공기업 5개 + SI 10개 + 스타트업 10개)

### 11.3 Phase 3: 면접 + 마감 (Day 61–90)

- **Week 7–8**:
  - 1차 면접 (서류 통과 20–30개 가정). 매 면접 후 1-page 회고 작성. dev-harness-kit에 interview-journal/ 폴더 만들어 누적.
  - 모의 면접 5회 (외부 friend or AI mock). 보안 직무 technical 질문 50개 + STAR 답변 5개 사전 준비.
  - AI 보안 직무 1차 면접 대비: LLM Top 10 + 실기 시연 (dev-harness-kit의 `security` skill을 5분 안에 시연).
- **Week 9–10**:
  - 2차/3차 면접. PT 슬라이드 1개 회사별 변형. EchoLeak 분석 사례 1개 깊게 준비.
  - 연봉 협상 준비. §10 밴드 + Levels.fyi 크로스체크 + 마이너 협상 카드 3장.
  - 합격 통보 → 48시간 안에 답변. 카운터오퍼 받으면 1주일 안에 결정.
  - 오퍼 수락 후: 백그라운드 체크 대비 (전 직장 동료 2인 사전 동의, 학위 증명서, 신분증 사본).

### 11.4 Korean-market specifics checklist

- [ ] **KISA 가이드라인 reading list** (필수):
  - [KISA Insight 2025 Vol.03] 리더들이 전망하는 2026년 사이버보안 이슈[^kisa-insight-2026]
  - KISA AI 보안 가이드라인 (2026년 신규 발표 추적)
  - ISMS-P 인증 심사 기준 (KISA)
  - NIST AI 100-2 (한국어 번역본 KISA)
  - AI Basic Act 영문본 + 한국어본[^ai-basic-act]
- [ ] **CTF platform 가입**:
  - [ ] Hack The Box (Pro Hacker, $14/월)
  - [ ] TryHackMe (Premium, $14/월)
  - [ ] DreamHack
  - [ ] Webhacking.kr
  - [ ] Lord of SQL Injection
  - [ ] PortSwigger Web Security Academy (free)
- [ ] **Korean security community 가입**:
  - [ ] KISA 공식 블로그 RSS 구독
  - [ ] 데일리시큐 (m.dailysecu.com) — 보안 뉴스 1위 매체
  - [ ] 보안뉴스 (boannews.com) — 업계 동향
  - [ ] ZDNet Korea 보안 섹션
  - [ ] AI Security Korea (디스코드/Slack)
  - [ ] 한국 OWASP 챕터 메일링 리스트
- [ ] **Target-company shortlist template** (우선순위 매트릭스):

| 회사 | 카테고리 | 매칭도 (1–5) | 선호도 (1–5) | 합격가능성 (1–5) | 우선순위 | 비고 |
|---|---|---|---|---|---|---|
| 금융보안원 | 공공/금융 | 5 | 5 | 3 | 1 | 신입 30명 규모 |
| 카카오뱅크 | Fintech | 5 | 4 | 3 | 2 | AI/Red Team JD 있음 |
| S2W | 스타트업 | 4 | 5 | 4 | 3 | 위협 인텔리전스 |
| KISA | 공공 | 4 | 4 | 3 | 4 | 청년인턴 트랙 |
| 토스 | Fintech | 4 | 4 | 3 | 5 | 클라우드 보안 JD |
| ... | | | | | | |

### 11.5 "If offered nothing" — 90-day contingency

- 정보보안기사 / OSCP 취득을 fallback 으로.
- 90일 후에도 오퍼가 없으면: (1) 계약직 6개월 / 인턴십 1년이라도 시작해서 1-year tenure 쌓기, (2) 그 기간 동안 자격증 + 공개 포트폴리오 강화, (3) 6개월 후 재도전.
- 한국 시장에서 "0 offers after 1 year of search"는 거의 발생하지 않음. 보안 직무 수요가 압도적.

---

## Source definitions (this section)

- [^kisa-insight-2026]: KISA Insight 2025 Vol.03, "리더들이 전망하는 2026년 사이버보안 이슈." https://blog.naver.com/kisa118/224098977736 (accessed 2026-09-10)
- [^ai-basic-act]: AIBasicAct.kr, "Korea AI Basic Act Official Portal." https://aibasicact.kr/ (accessed 2026-09-10)
