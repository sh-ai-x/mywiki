---
title: AI Engineer Study Roadmap
created: 2026-09-08
---

# AI Engineer Study Roadmap

This is the order I would study in if the goal is to maximize interview readiness for AI engineer roles while keeping the agent security angle.

For the supplied job description, use the detailed [competency map](./06-agent-engineer-competency-map.md) and [eight-week execution plan](./07-agent-engineer-execution-plan.md). They add ML/CS fundamentals, optimization experiments, benchmark generation, MCP integration and completion criteria to this overview.

## Phase 1: Core AI Engineering

- LLM APIs and structured outputs
- prompt design and context management
- tool calling and function schemas
- retrieval basics
- orchestration loops
- error handling around model calls

## Phase 2: Agent Systems

- LangGraph as the primary orchestration layer
- LangChain for tool abstraction and ecosystem compatibility
- agent planning and control flow
- tool registry and allowlists
- memory design and memory hygiene
- multi-step workflows
- approval gates
- human review points

## Phase 3: Evaluation and Observability

- traces and spans
- failure logging
- eval dataset creation
- replay harness
- regression testing
- calibration and confidence

## Phase 4: Security and Safety

- prompt injection
- indirect injection
- tool poisoning
- privilege boundaries
- sandboxing
- audit logs

## Phase 5: Delivery and Reliability

- FastAPI
- background workers
- idempotency
- retries
- persistence
- local reproduction

## What to build while studying

For each phase, produce one artifact:

1. Core AI Engineering: a small agent workflow with structured outputs
2. Agent Systems: a LangGraph orchestration demo with tools and memory
3. Evaluation and Observability: a trace explorer
4. Security and Safety: a blocked-action test suite
5. Delivery and Reliability: a reproducible local app with worker jobs

## Tooling baseline

Treat these as baseline tools rather than optional extras:

- LangGraph
- LangChain
- Pydantic
- FastAPI
- OpenAI or another model API
- a vector store or retrieval layer if the project needs it

## Recommended study principle

Turn applied topics into visible artifacts. Reserve time for Python, SQL, algorithms, operating systems, web fundamentals and traditional ML even when they do not immediately add a portfolio feature; they are explicit interview and job requirements.
