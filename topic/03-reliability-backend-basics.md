---
title: Reliability and Backend Basics
created: 2026-09-08
---

# Reliability and Backend Basics

Do not drop backend fundamentals. Just keep them in service of the agent/security story.

## Topics to study

- FastAPI or equivalent web API design
- typed schemas with Pydantic
- async job execution
- idempotency and retries
- persistence and migrations
- background workers
- rate limiting and quotas
- structured error handling
- Docker and local reproducibility
- API versioning
- request validation and error envelopes
- job state transitions
- basic caching and queue semantics

## Priority order

1. API design and typed schemas
2. Persistence, migrations, and job state
3. Async work queues and retries
4. Error handling and observability
5. Docker and local reproducibility
6. Rate limits, quotas, and versioning

## Key subtopics

- request-response contracts
- background job lifecycle
- idempotency keys
- database schema for traces and evals
- retryable versus terminal failures
- how to keep the system debuggable
- what belongs in the API versus the worker

## What matters most

For this portfolio, backend skills matter because they support:

- tool orchestration
- trace persistence
- replay APIs
- evaluation endpoints
- approval flows

## What not to overinvest in

- generic e-commerce CRUD
- unstructured monolithic backend patterns
- overbuilt microservices
- premature distributed systems work

Keep the backend small, typed, and observable.

## Concrete portfolio output

- a clean API for runs, traces, flags, and replays
- a worker queue for async analysis jobs
- one database schema that supports both production data and eval data
- Docker compose for local reproduction
- error handling that makes failures easy to inspect
