---
title: AI Agent Engineer Competency Map
updated: 2026-09-08
---

# AI Agent Engineer Competency Map

This plan maps the supplied job description to study topics and reviewable evidence. P0 is required for the first portfolio release; P1 follows the vertical slice; P2 is selective depth.

## Job duties → study → evidence

| Duty | Study topics | Portfolio evidence | Priority |
|---|---|---|---|
| Prompt optimization | Role/task separation, output contracts, few-shot selection, context ordering, prompt versioning, token budgets, controlled experiments | Three versioned prompts evaluated on the same validation cases; publish failures and cost | P0 |
| Topology and planning | State machines, routing, bounded planning, termination, retries, parallel dependencies, escalation | Compare fixed workflow, single tool agent and planner/executor under equal budgets | P0 |
| Agent/workflow evaluation | Schema checks, tool/argument correctness, retrieval relevance, citations, task outcomes, recovery, judge calibration | Node tests plus end-to-end outcome oracles and raw trial results | P0 |
| Specialized benchmark generation | Domain taxonomy, synthetic generation, independent answer checks, deduplication, provenance, grouped splits, leakage | Generator → review queue → frozen versioned dataset | P0 |
| MCP integration/development | Host/client/server roles, tools/resources/prompts, discovery, negotiation, schemas, transports, timeouts, authorization | One custom server, one pinned existing server, compatibility and failure tests | P0 |

## Additional fundamentals

| Area | Learn in this order | Completion exercise |
|---|---|---|
| Python | Types, exceptions, context managers, async I/O, cancellation, tests, packaging | Cancel concurrent work without leaving an active job or swallowing cancellation |
| Servers | HTTP, FastAPI/Pydantic, authentication vs authorization, SQL transactions, migrations, durable jobs, idempotency | Crash after an action; restart and reconcile without duplicating it |
| Traditional ML | Train/validation/test, leakage, bias/variance, regularization, precision/recall/F1, imbalance, calibration | Train a TF-IDF + logistic-regression issue router and compare with the LLM |
| Math/statistics | Vectors, cosine similarity, probability, cross-entropy intuition, uncertainty | Explain why repeated trials of one scenario are not independent new scenarios |
| LLM fundamentals | Tokenization, attention intuition, pretraining vs instruction tuning, context limits, sampling, embeddings | Explain a context-loss failure and measure a fix; no pretraining project required |
| Retrieval | Lexical baseline, chunking, metadata/ACL filters, embeddings, hybrid search, reranking, provenance | Measure retrieval recall@k separately from answer quality |
| Memory | Run state vs history vs durable memory, TTL, deletion, scope, stale/poisoned content | Prove user isolation and that deletion prevents future retrieval |
| CS | Complexity, hash maps, heaps, BFS/DFS, DAGs; processes/threads, locks, event loops, transactions, DNS/TCP/TLS | Explain scheduling and a race condition in your worker; solve Python/SQL exercises |
| Web apps | Browser/server boundary, REST, cookies/tokens, CORS/CSRF, streaming, pagination | UI with progress, interruption and errors; no client-side provider secrets |
| Delivery | Containers, CI, secrets, health checks, migrations, rollback, cloud networking basics | Clean-checkout setup and documented recovery procedure |
| English | Primary docs, ADRs, bug reports, experiment reports | One short English design or experiment note weekly |

## Technology choices

| Layer | Main choice | Required depth |
|---|---|---|
| Language | Python, uv, pytest, Ruff, a type checker | Pin tested interpreter/package versions |
| Orchestration | LangGraph | Typed state, reducers, routing, checkpoints, interrupts/resume, bounded parallelism |
| Integrations | LangChain | Model/tool interfaces, structured outputs and errors beneath abstractions |
| Other SDK | OpenAI Agents SDK | P1: one small equivalent workflow; compare lifecycle/tracing, not a second full app |
| Agent interoperability | A2A | P2 unless required: discovery, remote task lifecycle, authentication |
| Tool interoperability | Official Python MCP SDK | P0: one server and client integration with contract tests |
| API/storage | FastAPI, Pydantic, PostgreSQL, SQLAlchemy, Alembic | Explicit job leases/action ledger; queue middleware only when needed |
| Retrieval | Lexical fixture search or PostgreSQL text search | Embeddings/pgvector after baseline evidence justifies them |
| Evaluation | pytest + versioned JSONL; optional LangSmith | Manifests, raw outcomes and one evaluation system initially |
| Tracing | OpenTelemetry; PipelineSentry-compatible export | Redacted evidence and state transitions; no hidden model reasoning requirement |
| UI/delivery | Streamlit initially; Docker Compose | React/TypeScript only if interaction needs justify the work |

MCP and A2A solve different interoperability problems; A2A is a protocol, not another name for an agent SDK. Checkpoints do not make external writes idempotent. Schema-valid output can still be factually wrong.

Do not make fine-tuning, Kubernetes, multiple vector databases or several full agent frameworks prerequisites. Add them for a measured need or an explicit role requirement.

## Primary references

- [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview): orchestration/runtime scope.
- [MCP architecture](https://modelcontextprotocol.io/docs/learn/architecture): protocol components; pin the adopted revision.
- [A2A protocol](https://a2a-protocol.org/): agent interoperability.
- [LangSmith evaluation](https://docs.langchain.com/langsmith/evaluation): dataset/evaluator concepts.

Continue with the [execution plan](./07-agent-engineer-execution-plan.md) and [main proposal](../proposals/agentops-workbench-proposal.md).
