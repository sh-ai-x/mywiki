---
title: "AI Penetration Testing & Autonomous Security"
source: "https://www.strix.ai/blog/context-aware-pentesting"
author:
  - "[[Strix]]"
published: 2026-04-16
created: 2026-09-07
description: "Strix now builds a living threat model of your organization and learns from every finding, so each pentest picks up where the last one left off."
tags:
  - "clippings"
---
Today we're rolling out **context-aware pentesting** in Strix - a persistent memory layer that gives every run full knowledge of your organization's stack, architecture, and business logic, and that learns from every finding and every fix so each pentest builds on the last.

Most automated pentesting starts from zero every time. It doesn't know which services exist, how they're wired together, which endpoints are intentional, or which classes of bug your team has already eliminated. The result is generic testing that finds generic bugs, while the issues that actually depend on understanding the environment stay invisible.

## Context is the limiting factor

The bugs that matter most in modern applications are almost never syntactic. Broken access control, IDOR, tenant isolation failures, auth bypasses, business logic flaws - these are the issues that dominate bounty reports and incident postmortems, and none of them can be found by pattern matching. They're only visible to a tester who understands what the system is *supposed* to do.

A request that returns another tenant's data is only a bug if you know tenants are supposed to be isolated. An endpoint that accepts an arbitrary user ID is only a bug if you know the product intends it to be scoped to the caller. A discount code that stacks with itself is only a bug if you know the business rule says it shouldn't. Without that context, the same request looks like normal behavior and gets skipped.

This is the real frontier for automated pentesting. Coverage and speed are largely solved problems - Strix already runs thousands of agents in parallel across huge surfaces. What actually gates finding the next class of bug is how much the system knows about the environment it's testing, and how much it remembers from one run to the next.

## Organization-wide knowledge

Strix builds a threat model of your organization the same way a pentester does: by actually using the application. As agents test, they map the services, the user flows, the roles, the tenancy boundaries, and the business rules that govern what each action is supposed to do. That threat model is written down, kept up to date, and loaded into every pentest that follows.

With that context, agents can tell the difference between a request that technically works and one that violates what the product intends. That's where business logic bugs live, and it's the class of issue automated testing has historically been worst at.

The threat model grows with the product. New services, new flows, new roles - all of it gets picked up the next time Strix runs. The context deepens with every pentest.

## Continuous learning from findings and fixes

Strix remembers what it finds. When a vulnerability gets reported, triaged, fixed, or dismissed as a false positive, that outcome feeds back into the threat model. Over time Strix learns which patterns are real in your codebase, which classes of bug your team has already eliminated, and which areas keep regressing across releases.

Each pentest builds on the last. If a bug was fixed two months ago, Strix knows and verifies the fix held instead of re-reporting near-misses. If the same class of issue keeps showing up in one service, Strix weights its testing there. Triage time stops being spent on findings the team has already moved past.

The loop closes the other direction too. When a developer pushes a fix, Strix re-tests the exact path that produced the original finding and confirms the vulnerability is gone - no separate verification cycle, no waiting for the next scheduled run.

---

Context-aware pentesting is rolling out now to all Strix organizations. Every pentest you run from today forward feeds into your organization's threat model, and every run after that starts with the full context loaded.

[Get started →](https://app.strix.ai/)