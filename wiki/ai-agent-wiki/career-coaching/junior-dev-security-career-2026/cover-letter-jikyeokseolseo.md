---
tags: ["career", "job-hunting", "junior-swe", "junior-security", "cover-letter", "자기소개서", "korea-2026", "interview-prep"]
related:
  - ai-agent-wiki/career-coaching/junior-dev-security-career-2026/_index
  - ai-agent-wiki/career-coaching/junior-dev-security-career-2026/resume-portfolio-dev-harness-kit
  - ai-agent-wiki/career-coaching/junior-dev-security-career-2026/required-soft-skills-behavioral-interview
  - ai-agent-wiki/career-coaching
  - ai-agent-wiki/job-hunting-priority
created: 2026-09-10
---

# Cover letter + 자기소개서 strategy

> **TL;DR**: 자기소개서 hits the "신입 should know X" baseline in paragraph 1 (yes I meet the floor), then the "이 후보는 다름" differentiator in the second half (the dev-harness-kit portfolio is the differentiator). Use the 7-question structure; one anchor paragraph carries the portfolio, customized per role for company-specific signals.

(Pane C owns the deep 자기소개서 strategy. This section is the resume-side anchor.)

**The two-axis framing:**

- **"신입 should know X" baseline** — the floor that every 신입 is expected to clear. For SWE: a working knowledge of one stack (language + framework + DB + cloud), at least one shipped project, basic CS fundamentals (data structures, networking, OS). For security: 정보보안기사-level regulatory knowledge, OWASP Top 10 fluency, basic Linux/networking/crypto, exposure to one SIEM or one pentest tool.
- **"이 후보는 다름" differentiator** — the signal that survives the resume-screening round. For SWE: shipping artifacts (dev-harness-kit is the canonical version). For security: CTF write-ups + ISMS-P implementation experience + AI-security literacy.

The 자기소개서 should hit the baseline in the first paragraph (the "yes I meet the floor" signal) and the differentiator in the second half (the "I bring this that others don't" signal).

**Korean 자기소개서 structure (인적사항 + 7 questions typical):**

1. 성장과정 / 지원동기 — anchor the dev-harness-kit here; show the *why* of the architecture.
2. 본인의 장점 / 강점 — pick *one* strength that the portfolio demonstrates (e.g., "I measure before claiming improvement" — the HELM through-line).
3. 본인의 단점 / 보완점 — one genuine weakness + the active remediation.
4. 지원동기 / 입사 후 포부 — specific to the company; reference a recent product / engineering blog post / GitHub release.
5. 프로젝트 경험 — the dev-harness-kit (one detailed project > three shallow ones).
6. 협업 / 갈등 경험 — STAR format; technical specifics.
7. 기술적 도전을 해결한 경험 — the AI-coding collaboration angle; show how you use AI without letting it make decisions for you.

**Anchor paragraph (insert verbatim, customize per role):**

> "저는 [sh-ai-x/dev-harness-kit](https://github.com/sh-ai-x/dev-harness-kit)를 1년 6개월간 운영해 왔습니다. Claude Code와 Codex를 위한 듀얼 런타임 플러그인 마켓플레이스로, 15개 이상의 스킬이 TDD, AI-eval, 보안 리뷰, 코드 시각화를 다룹니다. 모든 스킬은 테스트를 거치고, 모든 변경은 구조화된 리뷰 게이트를 통과하며, 모든 릴리스는 결정론적 eval 세트를 실행합니다. 가장 관련 있는 시그널은 `dev-kit:security` 스킬입니다 — OWASP Top 10 + LLM01–LLM10 + 공급망 점검의 11-차원 fan-out 리뷰를 수행한 뒤 결과를 적대적으로 검증하는 스킬로, AI 에이전트를 더 많이 코드를 작성하는 것이 아니라 더 안전하게 코드를 작성하도록 만들기 위해 만들었습니다."

The 자기소개서 should be customized per role: the paragraph above is the *common* anchor; the role-specific paragraph should reference a specific product / recent engineering blog post from the target company.

## Related

- [[_index|Junior SWE + Security Pro sub-hub]]
- [[resume-portfolio-dev-harness-kit|Resume / portfolio positioning — dev-harness-kit]]
- [[required-soft-skills-behavioral-interview|Required soft skills + behavioral interview topics]]
- [[../career-coaching|career-coaching major hub]]
- [[../../job-hunting-priority|job-hunting-priority]]
