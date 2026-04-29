---
title: "Agentic Workflow"
description: "Reference workflow for running agentic software delivery with risk-based controls."
version: 1.0
kind: workflow
---

# Agentic Workflow

## Purpose
Define the standard end-to-end flow for agentic software delivery so work is fast, reviewable, and safe to operate.

## Inputs
- Prioritized backlog item or requested outcome.
- Applicable policies, compliance constraints, and architecture standards.
- Available templates: spec, implementation plan, prompt change request (for prompt-control updates), PR, and evidence package.

## Outputs
- Verified change(s) linked to a governing spec state.
- Deployment record and monitoring expectations.
- Retrospective updates to templates, protocols, or gates.

## Core principles
- The execution unit is an **agentic specification**.
- The delivery unit is **stepwise PRs** tied to plan steps.
- "Done" means **verified**, not merely implemented or merged.
- Human decisions are **risk-based** and explicit.

## Workflow stages

### 1) Intake and risk classification
- Capture outcome, scope, and constraints.
- Assign risk tier: `low`, `medium`, or `high`.
- Route high-impact requests to pre-approval paths.

### 2) Spec shaping
- Create or update the agentic spec with:
  - intent and non-goals,
  - constraints and boundaries,
  - verification requirements,
  - rollback/restore expectations.
- Confirm spec owner and approving role.

### 3) Implementation planning
- Break spec into execution steps.
- Define expected PR for each step.
- Mark dependencies, ordering, and escalation triggers.

### 4) Agent execution
- Agent executes one plan step at a time.
- If prompt-control tuning is needed, create/update a prompt change request artifact before code/config/model updates.
- Valid prompt-control intentions include: `debug_fix`, `configuration`, `fine_tuning`, `policy_hardening`, `cost_latency_optimization`, `style_alignment`, and `tool_routing`.
- If humans run manual prompting sessions, record a manual session trace summary and link it to the active prompt change request.
- Prompt/model revisions must be versioned and pinned in the execution environment for reproducibility.
- Open PR tied to:
  - spec ID/reference,
  - plan step ID,
  - prompt change request ID (if applicable),
  - risk tier,
  - required evidence checklist.

### 5) Verification gates
- Automated gates: build, tests, lint, security/policy checks.
- Human gates (risk-based): reviewer sign-off where required.
- Evidence gates: traceability, auditability, and restore path present.

### 6) Merge and release
- Merge only after required gates pass.
- Deploy through controlled pipeline.
- Record monitoring expectations and rollback conditions.
- Include prompt-control revision references in the deployment record when prompt-control changes were part of the release.

### 7) Learn and update
- Review failures, exceptions, and near-misses.
- Update templates, protocol rules, and gate policies.
- Feed lessons into future specs and planning.

## Risk-based control model
- **Low risk:** automated path with sampled human review.
- **Medium risk:** required reviewer plus full evidence package.
- **High risk:** pre-approval, strict sign-off path, and tightened release controls.

## Prompt-control promotion and rollback protocol
- Promotion order is `dev -> staging -> prod`; skipping stages requires a logged exception with human approver.
- Each environment must pin the approved prompt-control revision before validation or rollout.
- Staging validation must include behavior checks tied to the prompt change request acceptance criteria.
- High-risk prompt-control changes require explicit human pre-approval before production promotion.
- Production rollback path must support reverting to the last known-good prompt-control revision without requiring new code deployment.
- Rollback triggers include safety/policy regression, reliability degradation, or evidence of unexpected behavior drift.

## Minimum definition of done
A change is done only if it:
- is linked to the active spec state,
- maps to a plan step and PR,
- passes required automated and human gates,
- includes evidence and rollback/restore readiness,
- is deployable and monitorable through the controlled pipeline.

## Related documents
- `agent-roles.md`
- `agentic-artifacts.md`
- `transition-plan.md`
- `agentic-programming-manifesto.md`

