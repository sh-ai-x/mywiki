---
title: Agent Security Foundations
created: 2026-09-08
---

# Agent Security Foundations

This is the minimum security stack you should know for an agent engineer portfolio.

## Topics to study

- prompt injection and indirect prompt injection
- tool poisoning and tool shadowing
- excessive agency and least privilege
- action allowlisting
- per-tool scope and bounded authority
- human approval gates for irreversible actions
- sandboxing and network egress control
- audit logs and replay
- red-team testing for agent flows

## Priority order

1. Tool allowlisting and least privilege
2. Prompt injection and indirect injection
3. Human approval gates for unsafe actions
4. Sandboxing and egress restriction
5. Audit logging and replay
6. Red-team tests and regression suites

## Key subtopics

- threat modeling for agent workflows
- trust boundaries between user, model, tools, and memory
- typed tool schemas instead of free-form commands
- safe defaults when policy is uncertain
- approval UX for irreversible actions
- separation between reasoning, policy, and execution

## Why these matter

The most important failure mode in agent systems is not a bad answer. It is an unsafe action taken with valid permissions.

That means your project should prove:

- the model is untrusted
- the code layer enforces policy
- tool calls are typed and bounded
- dangerous actions are gated
- every action can be replayed later

## Practical study order

1. OWASP-style LLM threat modeling
2. Tool allowlisting and scope checks
3. Prompt-injection and indirect-injection defense
4. Audit logging and incident replay
5. Sandbox boundaries for external tools
6. Red-team tests and regression suites

## What to implement in the portfolio

- a tool registry with explicit allowlist
- per-tool authorization policy
- blocked actions with reason codes
- approval flow for risky actions
- deterministic replay of tool decisions
- failure taxonomy for security incidents
- red-team scenarios that prove the controls actually work
- regression tests that fail when a blocked action starts passing

## Concrete portfolio output

- one-page threat model for your agent
- a policy matrix for each tool
- a replayable security incident trace
- a test suite covering prompt injection, tool abuse, and approval bypass
- a short write-up explaining why the model is treated as untrusted

## Evidence from your wiki

Use these notes as the source set for the project narrative:

- `wiki/ai-agent-wiki/core-ai-security/essential/action-allowlisting.md`
- `wiki/ai-agent-wiki/core-ai-security/practical/defense-in-depth-architecture.md`
- `wiki/ai-agent-wiki/core-ai-security/specialized/agent-specific-threats.md`
