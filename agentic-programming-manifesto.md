---
title: "Agentic Programming Manifesto — Short"
description: "A compact, agile-inspired manifesto for agentic programming with AI code generation."
version: 1.0
kind: manifesto
---

# Agentic Programming Manifesto — Short
*2026 — inspired by the Agile Manifesto (2001)*

We are discovering better ways to build software with AI-powered agents by combining automation with human accountability. Through this work, we have come to value:

## Values
**Human accountability and direction** over autonomous, unreviewed agent output.

**Verified, auditable delivery through controlled pipelines** over informal "works on my machine" merges.

**Intent-traceable execution (spec -> plan -> stepwise PRs)** over monolithic, context-poor changes.

**Governed prompt/config lifecycle and evidence stewardship** over ad-hoc tuning and unmanaged traces.

That is, while there is value in the items on the right, we value the items on the left more.

## Principles
We follow these principles:

- Humans own high-stakes decisions, final approvals, and policy exceptions.
- Every meaningful change is linked to a governing spec state and implementation plan step.
- Risk-tiered controls determine verification depth, reviewer requirements, and release strictness.
- Small, reviewable PRs are the default delivery unit.
- Prompt/config changes are versioned, promoted across staged environments, and rollback-ready.
- Evidence is complete, inspectable, retained by policy, and protected with role-scoped access and redaction where needed.
- Separation of duties is maintained for high-risk work.
- Teams optimize for fast feedback loops without bypassing core controls.
- Done means deployable, monitorable, and restorable, not only implemented.
- Learning loops continuously improve templates, protocols, and guardrails from outcomes.

## What “done” means (in practice)
Done means the change is linked to the governing spec state, passes the controlled pipeline, is backed by evidence, and is inspectable and restorable, with humans owning high-stakes decisions.

