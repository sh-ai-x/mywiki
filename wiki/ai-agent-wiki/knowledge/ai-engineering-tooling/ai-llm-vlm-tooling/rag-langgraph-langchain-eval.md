---
tags: ["rag", "langchain", "langgraph", "ai-engineering", "evaluation", "llm-as-judge"]
related: ["ai-agent-wiki/knowledge/ai-engineering-tooling/ai-llm-vlm-tooling/rag-retrieval-augmented-generation-the-rag-in-the-topic", "ai-agent-wiki/knowledge/agent-engineering/agentops-workbench/orchestration-langgraph", "ai-agent-wiki/knowledge/agent-engineering/agentops-workbench/evaluation"]
created: 2026-09-11
source: "_research/rag-langgraph-langchain-eval.md"
---

# RAG·LangGraph·LangChain과 Eval

> **RAG는 검색과 생성을 결합하고, LangChain은 구성 요소를 조합하며, LangGraph는 상태ful 실행을 오케스트레이션한다.**

## 핵심 구분

- **RAG**: 외부 지식원을 검색해 컨텍스트로 주입하는 애플리케이션 패턴이다. 검색 실패와 생성 실패를 분리해 디버깅해야 한다.
- **LangChain**: 모델·프롬프트·retriever·tool·parser를 조합하는 애플리케이션/에이전트 프레임워크다.
- **LangGraph**: state graph, 조건부 분기, checkpoint, durable execution, streaming, human-in-the-loop를 제공하는 orchestration runtime이다. LangChain 없이도 사용할 수 있다.

## Eval 설계

| 계층 | 주요 질문 | 측정 예 |
|---|---|---|
| Retrieval | 필요한 근거를 찾았나? | Recall@k, Precision@k, MRR, Context Precision/Recall |
| Generation | 근거에 충실하고 질문에 답했나? | Faithfulness, Answer Relevancy, Answer Correctness |
| Agent/workflow | 올바른 도구·순서·종료를 선택했나? | task success, tool-call accuracy, step validity |
| Production | 실제 환경에서 안정적인가? | failure rate, latency, cost, drift, human feedback |

Faithfulness는 답변 claim 중 retrieved context가 지지하는 비율이며, correctness와는 다르다. 틀린 컨텍스트를 충실하게 요약할 수 있으므로 retrieval 지표와 함께 평가해야 한다.

## 권장 방법

실제 질문을 유형별로 분류하고 reference answer와 gold passage를 만든다. Retrieval-only와 end-to-end 평가를 분리하고, deterministic checks·human review·calibrated LLM-as-judge를 병행한다. judge는 position/verbosity/self-preference bias가 있으므로 단독 production gate로 쓰지 않는다. 고정된 held-out set과 trace 기반 online evaluation으로 회귀와 운영 drift를 확인한다.

## Related

- [[rag-retrieval-augmented-generation-the-rag-in-the-topic|RAG 기존 노트]] — RAG 변형과 검색 전략
- [[../../../../agent-engineering/agentops-workbench/orchestration-langgraph|LangGraph orchestration]] — 상태 그래프와 HITL
- [[../../../../agent-engineering/agentops-workbench/evaluation|Evaluation methodology]] — benchmark와 LLM-as-judge
