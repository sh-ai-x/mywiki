# AI Agent Engineer: Eight-Week Execution Plan

Assumption: 20–25 hours weekly and basic Python already familiar. This is a workload estimate, not a hiring timeline. If Python/HTTP/SQL exercises are difficult, add a foundation block. Deliverables and reports should be in English.

| Week | Study and implement | Exit evidence |
|---|---|---|
| 1 | Python async, HTTP/SQL, Pydantic; domain/schema; 12 reviewed cases; fixed workflow | Typed request produces a cited response and local ticket draft; tests and clean setup |
| 2 | LangChain tools/structured outputs; LangGraph state/routing/checkpoints; FastAPI | Durable run, failure/cancellation states and three-minute demo; begin applications |
| 3 | MCP discovery, schemas, transports/errors; custom and existing server | Valid call, malformed output, timeout, disconnect and unauthorized-request tests |
| 4 | Prompt experiments; ML router baseline; benchmark generation/review/splits | Baseline scorecard and versioned dataset; no held-out tuning |
| 5 | Fixed workflow vs tool agent vs bounded planner; state/retry recovery | Paired validation comparison with equal budgets and an architecture decision |
| 6 | Node/task evaluation, tracing, failure analysis | Trace → confirmed failure → reviewed regression; judge disagreements recorded |
| 7 | Authorization, action-bound approval, memory isolation, deployment | Direct bypass and restart tests; reproducible release |
| 8 | Frozen evaluation, README, demo, project interview | Raw held-out results including misses; five-minute demo; evidence card |

## LangGraph / LangChain mastery checklist

- [ ] Explain state schema, reducers, branching and termination using your graph.
- [ ] Resume an interrupted run using the correct thread identity and durable state.
- [ ] Show why retrying a node with an external write needs action idempotency.
- [ ] Handle invalid arguments, unavailable tools and structured-output errors.
- [ ] Distinguish retrieved content, tool responses, user input and privileged instructions.
- [ ] Explain checkpoint history versus application memory versus traces.
- [ ] Reproduce a failure with fake responses and explain what that replay cannot prove.
- [ ] Replace a model adapter without rewriting domain contracts.

## Weekly rhythm and readiness

Allocate approximately 13–15 hours to implementation, 5–6 to Python/SQL/CS/ML exercises and 3–4 to applications and interviews. Write one English ADR or experiment note weekly. Every two weeks, explain the app from a blank diagram without generated documentation.

Apply once the Week 2 workflow is runnable and you can explain your code. Stronger project interviews benefit from Week 5 experiments and Week 7 reliability evidence. Do not wait for every optional SDK.

Track eligibility, applications, recruiter screens, technical screens and project interviews separately. Use actual feedback to choose the next task. Framework accumulation does not resolve missing fundamentals or ineligible targeting.
