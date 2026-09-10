---
topic: RAG, LangGraph, LangChain, and Evaluation
tags:
  - rag
  - langchain
  - langgraph
  - ai-engineering
  - evaluation
  - llm-as-judge
related:
  - ai-agent-wiki/knowledge/ai-engineering-tooling/ai-llm-vlm-tooling/rag-retrieval-augmented-generation-the-rag-in-the-topic
  - ai-agent-wiki/knowledge/agent-engineering/agentops-workbench/orchestration-langgraph
  - ai-agent-wiki/knowledge/agent-engineering/agentops-workbench/evaluation
  - ai-agent-wiki/knowledge/agent-engineering/agentops-workbench/observability-otel
created: 2026-09-11
updated: "2026-09-10T16:27:11+00:00"
sources:
  - "https://arxiv.org/abs/2005.11401"
  - "https://docs.langchain.com/oss/python/langchain/overview"
  - "https://langchain-ai.github.io/langgraph/"
  - "https://docs.langchain.com/langsmith/evaluation-concepts"
  - "https://docs.langchain.com/langsmith/evaluation-approaches"
  - "https://arxiv.org/abs/2309.15217"
  - "https://github.com/vibrantlabsai/ragas/blob/main/docs/concepts/metrics/available_metrics/faithfulness.md"
status: promoted
promoted_to: wiki/ai-agent-wiki/knowledge/ai-engineering-tooling/ai-llm-vlm-tooling/rag-langgraph-langchain-eval.md
---

# RAG·LangGraph·LangChain 개념과 Eval

> **RAG는 지식을 검색해 생성에 주입하고, LangChain과 LangGraph는 그 파이프라인과 에이전트 실행을 구성하는 계층이며, Eval은 검색·생성·실행을 분해해 측정하는 방법론이다.**

## 1. RAG (Retrieval-Augmented Generation)

RAG는 모델 파라미터에만 의존하지 않고 외부 지식원에서 관련 문서를 검색한 뒤, 검색 결과를 프롬프트 컨텍스트로 넣어 답변을 생성하는 구조다. 원 논문은 지식 집약적 NLP에서 parametric memory와 non-parametric memory를 결합하는 접근으로 제시했다.

일반적인 흐름은 `문서 수집 → chunking/metadata → embedding·indexing → query 변환 → top-k retrieval → reranking/filtering → context assembly → generation → citation/validation`이다.

중요한 설계 구분:

- **검색 실패**: 정답 문서가 검색되지 않음. chunk 크기, query rewrite, embedding, hybrid search, reranker, top-k를 개선해야 한다.
- **생성 실패**: 정답 컨텍스트가 있는데도 답변이 틀리거나 근거를 벗어남. prompt, context ordering, 모델, 구조화 출력, claim validation을 개선해야 한다.
- **Naive RAG**는 단일 top-k 검색에 의존하기 때문에 multi-hop·전역 요약·모호한 질문에 취약하다. 필요할 때만 hybrid retrieval, multi-query, reranking, GraphRAG, agentic retrieval을 추가한다.
- RAG는 환각을 “자동으로 제거”하지 않는다. 검색된 컨텍스트가 부정확하거나 생성기가 근거 밖 내용을 만들면 여전히 실패한다.

## 2. LangChain

LangChain은 모델, 프롬프트, retriever, tool, output parser, memory 같은 부품을 표준 인터페이스로 조합하는 애플리케이션·에이전트 프레임워크다. 따라서 RAG의 loader/retriever/chain과 tool-calling agent를 빠르게 구성하기 좋다.

실무에서의 역할은 “무엇을 호출할지”를 구성하는 애플리케이션 계층이다. 단순 RAG chain에는 충분하지만, 장시간 실행, 복구, 조건부 분기, 사람 승인, 세밀한 상태 추적이 핵심이면 LangGraph 계층을 함께 사용한다.

## 3. LangGraph (사용자 표현의 ‘langraph’)

LangGraph는 상태 그래프를 정의하고 실행하는 저수준 orchestration runtime이다. 노드는 작업, 엣지는 순서·조건부 라우팅, state는 노드 사이에서 전달되는 실행 데이터다. LangChain 없이도 사용할 수 있으며, LangChain은 선택 가능한 구성 요소·에이전트 계층이다.

LangGraph의 차별점은 **durable execution, checkpoint/persistence, streaming, human-in-the-loop, stateful long-running workflow**다. `interrupt()`로 실행을 중단해 승인을 받고, 저장된 state와 `Command(resume=...)`로 재개할 수 있다. 단, checkpoint 자체가 외부 부작용의 exactly-once 실행을 보장하지 않으므로 tool idempotency, approval binding, nonce/expiry 같은 별도 설계가 필요하다.

## 4. 세 개념의 관계

```text
외부 문서·DB
    ↓
RAG: retrieve → rerank → ground generation
    ↓
LangChain: 모델·retriever·tool·agent 부품 조합
    ↓
LangGraph: 상태·분기·재시도·checkpoint·HITL 실행 제어
    ↓
LangSmith/관측성: trace·dataset·evaluation·production monitoring
```

RAG는 문제 해결 패턴, LangChain은 구성 요소와 애플리케이션 프레임워크, LangGraph는 복잡하고 지속되는 실행을 위한 runtime이라고 설명하면 가장 명확하다.

## 5. Eval의 기본 원칙

Eval은 최종 답변 하나의 점수만 보는 일이 아니다. LangSmith의 평가 접근처럼 애플리케이션을 LLM 호출, retrieval, tool invocation, output formatting 등 핵심 단계로 나누고 각 단계의 품질 기준을 정한다.

최소 평가 세트는 다음과 같다.

| 계층 | 질문 | 대표 측정 |
|---|---|---|
| Retrieval | 필요한 근거를 찾아왔나? | Recall@k, Precision@k, MRR, nDCG, Context Precision/Recall |
| Generation | 검색 근거에 충실하고 질문에 답했나? | Faithfulness, Answer Relevancy, Answer Correctness, citation correctness |
| Agent/workflow | 올바른 도구·순서·종료를 선택했나? | task success, tool-call accuracy, step validity, latency, cost |
| Production | 실제 사용자 환경에서 안전하고 안정적인가? | failure rate, abstention, drift, latency/cost, human feedback |

## 6. RAG 평가 메트릭

- **Context Recall**: 정답을 만들기 위해 필요한 정보가 retrieved context에 포함됐는가. 정답 근거(annotation)가 필요하다.
- **Context Precision**: 검색 결과 상위에 관련 chunk가 얼마나 집중됐는가. 노이즈가 많으면 낮아진다.
- **Faithfulness**: 답변의 claim들이 제공된 context로 뒷받침되는 비율. Ragas의 정의는 `지원되는 claim 수 / 전체 claim 수`다. 정답과의 일치가 아니라 “컨텍스트에 근거했는가”를 본다.
- **Answer Relevancy**: 답변이 질문의 의도에 직접 답하는가. 장황하거나 질문을 빗나간 답을 잡는다.
- **Answer Correctness**: reference answer 또는 사람이 검증한 정답과 실제 의미가 맞는가. 최종 사용 가치에 가깝지만 reference 품질에 의존한다.

따라서 “faithfulness가 높다 = 정답이다”는 아니다. 틀린 문서를 근거로 매우 충실하게 틀린 답을 만들 수 있으므로 correctness와 retrieval 지표를 함께 본다.

## 7. Eval 실행 방법

1. 실제 사용 질문을 수집하고 easy/ambiguous/multi-hop/out-of-domain/안전 민감 질문으로 분류한다.
2. 질문별로 reference answer와 핵심 근거 문서(가능하면 gold passage)를 만든다.
3. baseline을 고정한다: naive top-k, hybrid, reranker, 모델·prompt 버전과 latency/cost를 함께 기록한다.
4. retrieval-only와 end-to-end를 분리 평가한다. 그래야 검색 문제와 생성 문제를 혼동하지 않는다.
5. deterministic check(문자열·JSON schema·SQL 결과·테스트 통과)와 human review를 병행한다.
6. LLM-as-judge는 rubric, pass/fail 기준, 짧은 이유를 출력하게 하고 인간이 검토한 샘플에서 calibration한다. judge 점수 하나로 production 승인을 자동 결정하지 않는다.
7. 고정된 held-out set에서 회귀 테스트하고, 운영에서는 trace 기반 online evaluation과 사용자 feedback으로 새로운 실패 유형을 추가한다.

## 8. 추천 평가 설계

```text
Retriever 변경 → Recall@k / Context Precision 확인
        ↓
Prompt·모델 변경 → Faithfulness / Relevancy / Correctness 확인
        ↓
Graph·agent 변경 → task success / tool-call / step trace 확인
        ↓
배포 후 → latency·cost·failure·drift·human feedback 모니터링
```

권장 보고서는 평균 점수 하나가 아니라 질문 유형별 분포, 실패 사례, latency/cost, abstention rate, confidence interval을 포함한다. LLM-as-judge는 position·verbosity·self-preference bias가 있으므로 가능하면 pair order randomization, human-reviewed calibration set, deterministic checks로 보완한다.

## Sources

- [Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks](https://arxiv.org/abs/2005.11401) — RAG의 원 논문
- [LangChain overview](https://docs.langchain.com/oss/python/langchain/overview) — LangChain 구성 요소와 agent framework
- [LangGraph overview](https://langchain-ai.github.io/langgraph/) — orchestration runtime, stateful execution, persistence
- [LangSmith evaluation concepts](https://docs.langchain.com/langsmith/evaluation-concepts) — 컴포넌트별·수명주기별 평가
- [Application-specific evaluation approaches](https://docs.langchain.com/langsmith/evaluation-approaches) — RAG와 agent 평가 접근
- [RAGAS: Automated Evaluation of Retrieval Augmented Generation](https://arxiv.org/abs/2309.15217) — RAG 전용 reference-free 평가 프레임워크
- [Ragas Faithfulness metric](https://github.com/vibrantlabsai/ragas/blob/main/docs/concepts/metrics/available_metrics/faithfulness.md) — claim 기반 faithfulness 정의

## Notes

- 면접용 한 문장: “RAG는 외부 지식을 검색해 grounding하는 패턴이고, LangChain은 모델·retriever·tool을 조합하는 프레임워크, LangGraph는 상태·분기·checkpoint·HITL을 실행하는 runtime입니다. Eval은 retrieval, grounded generation, task completion을 분리해 deterministic check·human review·LLM judge를 함께 씁니다.”
- 승격 시 RAG, LangGraph/LangChain 비교, Eval 방법론의 2~3개 leaf로 분리할 수 있다.

## Related

- [[ai-llm-vlm-tooling/rag-retrieval-augmented-generation-the-rag-in-the-topic|RAG 기존 노트]] — RAG 변형과 프레임워크 landscape
- [[agent-engineering/agentops-workbench/orchestration-langgraph|LangGraph orchestration]] — 상태 그래프와 HITL
- [[agent-engineering/agentops-workbench/evaluation|Evaluation methodology]] — benchmark, LLM-as-judge, 통계적 평가
- [[agent-engineering/agentops-workbench/observability-otel|Observability]] — trace와 운영 모니터링
