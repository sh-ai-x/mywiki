---
tags: ["wiki", "master-hub", "map", "root", "job-hunting"]
---

# Wiki Map

> 모든 지식 도메인의 최상위 허브 — Obsidian 그래프의 중심 노드.
> 2026-09-10 재배치: job-categories facet가 신규 진입점, 토픽별 KB는 knowledge/ 하위로 이동. 모든 leaf에 `priority:` + `interview-prep` 태그 부착.

## 🚀 Start here — job categories

- [[wiki/ai-agent-wiki/job-categories/_index|Job Categories (facet hub)]] — 5개 직무별 (security / AI engineer / AI applied / AI-native / dev-tools) reading-list facet
- [[wiki/ai-agent-wiki/career-coaching|Career Coaching (junior, global-first)]] — 3개 dossier (SWE+security / AI engineer / Korean security) 통합, global-first filter 적용
- [[wiki/ai-agent-wiki/job-hunting-priority|🚀 Job-Hunting Priority Hub]] — priority-sorted reading list across knowledge/ 서브트리

## 🤖 AI Dev Tools (numbered notes, root)

- [[wiki/ai-agent-wiki/18-strix|Strix (18)]] — AI 에이전트 보안 테스트
- [[wiki/ai-agent-wiki/19-context-aware-pentesting|Context-Aware Pentesting (19)]] — Strix의 persistent threat-model 레이어

## 📚 Knowledge Base (topic-first)

토픽별로 정리된 4개 subtree. Job Categories facet가 이들을 reference함.

- [[wiki/ai-agent-wiki/knowledge/core-ai-security/_index|Core AI Security]] — 35개 leaf notes, 3개 tier (essential/practical/specialized). priority-tagged (5 critical / 11 high / 11 medium / 8 low)
- [[wiki/ai-agent-wiki/knowledge/agent-engineering/_index|Agent Engineering]] — 7개 leaf notes: LangGraph, MCP, evaluation, observability, reliability
- [[wiki/ai-agent-wiki/knowledge/ai-engineering-tooling/_index|AI Engineering Tooling]] — 7개 job-hunting-filtered leaf notes
- [[wiki/ai-agent-wiki/knowledge/strix/_index|Strix sub-hub]] — 3개 leaf notes: threat coverage, CI 통합, defense signal

## 🪵 System & Logs

- [[wiki/ai-agent-wiki/log|AI Agent Wiki — Change Log]] — 도메인별 ingest + 재구성 이력
- [[wiki/ai-agent-wiki/_archive/|Archive]] — outdated content (PKM, paper-deep-dives, EU AI Act 챕터 등)

---

## 그래프 읽는 법
- **큰 노드** = 많은 연결을 가진 허브 파일 (이 파일 + 각 도메인 hub)
- **클러스터** = 같은 도메인에 속하는 파일들이 허브 주변에 모임
- **Cross-domain 엣지** = 서로 다른 도메인 간 `[[wikilink]]` 연결
- **`priority:` 필드** = 모든 leaf의 frontmatter에 부착, Dataview `WHERE priority = "critical"` 등으로 필터링
- **`interview-prep` 태그** = critical/high 우선순위 항목에 자동 부착
- **Job-first navigation** = [[wiki/ai-agent-wiki/job-categories/_index|job-categories facet]] 가 knowledge/ 위의 curated view
