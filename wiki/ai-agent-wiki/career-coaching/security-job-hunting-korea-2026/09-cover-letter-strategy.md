---
topic: security-job-hunting-korea-2026-§9-cover-letter
tags: ["career", "job-hunting", "security", "korea", "section", "cover-letter", "global-first", "junior", "interview-prep"]
related: ["ai-agent-wiki/career-coaching/security-job-hunting-korea-2026/_index", "ai-agent-wiki/career-coaching"]
sources: []
created: 2026-09-10
updated: 2026-09-10
status: promoted
parent: ai-agent-wiki/career-coaching/security-job-hunting-korea-2026
section: §9
global-first-filter: applied
---

# §9 Cover Letter / 자기소개서 Strategy

## §9 Cover Letter / 자기소개서 Strategy

### 9.1 Positioning hook (first 200자)

자기소개서 첫 문단은 "왜 이 사람인지" 1문장으로 답해야. dev-harness-kit을 활용한 후킹 예시:

> **예시 hook 1 (기술 빌더 강조)**:
> "AI Native 보안 자동화 툴킷(dev-harness-kit)을 MIT 라이선스로 오픈소스 배포하며, OWASP A01–A10 카테고리별 결정론적 보안 점수(0–100)를 산출하는 정적 분석 엔진을 직접 설계·구현했습니다. 보안 도구를 사용하는 사람이 아니라, 보안 도구를 만드는 사람으로서 귀사의 보안 역량 강화에 기여하고 싶습니다."

> **예시 hook 2 (문제 해결 강조)**:
> "2026년 LLM 통합 SaaS의 급격한 확산은 새로운 공격 표면 — 간접 프롬프트 인젝션, MCP 도구 오염, 멀티모달 인젝션 — 을 만들어냈습니다. 기존 AppSec 방법론은 이 표면을 다루지 못합니다. 저는 이 문제를 OWASP LLM Top 10을 기반으로 한 자동 검토 스킬을 직접 개발하여 해결책을 만들었습니다."

> **예시 hook 3 (커뮤니케이션 강조)**:
> "금융보안원이 요구하는 ISMS-P 232개 통제 항목과 NIST AI 100-2가 요구하는 AI 위험 분류를 한 페이지에 매핑하는 보안 거버넌스 문서를 dev-harness-kit으로 자동 생성하는 워크플로우를 구축한 경험이 있습니다. 보안 정책은 '문서가 아니라 실행 가능한 규칙'이어야 한다는 철학을 가지고 일합니다."

### 9.2 문항별 전략

대부분의 자기소개서 문항 (보안 직무 기준):

1. **"보안 직무를 선택한 이유와 본인의 강점"** (500자) → §5 STAR 스토리의 압축본.
2. **"최근 분석한 보안 이슈와 본인의 대응"** (700자) → EchoLeak (CVE-2025-32711) 분석 + dev-harness-kit `security` skill로 자동 검토한 결과 인용.
3. **"본인이 주도한 프로젝트"** (700자) → dev-harness-kit의 `/dev-kit:security`와 `security-metrics` 소개. 링크 + 결과 (OWASP A01–A10 scorecard 샘플).
4. **"지원동기"** (500자) → 회사-specific. SI 컨설턴트 지원 시 "고객사 ISMS-P 인증 갱신 사이클을 자동화하는 도구"로 연결.
5. **"입사 후 포부"** (500자) → "1년차: ISMS-P 컨설턴트로서 5건 이상의 인증 갱신 프로젝트 참여, dev-harness-kit을 활용한 자동 검토 워크플로우 정착."

### 9.3 샘플 1-page 자기소개서 PT 스크립트 (5분)

```
[슬라이드 1] 표지
- 이름, 지원 직무, dev-harness-kit GitHub URL (QR 코드)

[슬라이드 2] Why security + why I build tools
- "보안 도구를 사용하는 사람이 아니라 만드는 사람"
- dev-harness-kit 한 줄 설명

[슬라이드 3] OWASP A01–A10 자동 검토 시연
- /dev-kit:security-metrics 출력 샘플 (실제 점수)

[슬라이드 4] 아키텍처: hook-based enforcement
- "정책은 문서가 아니라 실행 가능한 규칙"
- worktree-guard, TDD gate 시각화

[슬라이드 5] 실측 결과 / 신뢰 신호
- 818 commits, MIT, Codex/Claude parity

[슬라이드 6] 입사 후 1년 계획
- 도구를 사내 워크플로우로 정착
- Q&A 슬라이드
```
