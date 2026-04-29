---
title: "Agentic Artifacts"
description: "Canonical artifact set for traceable agentic delivery from intent to verified release."
version: 1.0
kind: artifacts
---

# Agentic Artifacts

## Purpose
Define the minimum set of artifacts required to make agentic work legible, governable, and auditable.

## Artifact lifecycle
Backlog item -> Spec -> Implementation plan -> Prompt change request (when needed) -> Stepwise PRs -> Evidence package -> Verification record -> Deployment record -> Retrospective updates

## Required artifacts

### 1) Backlog item
**Contains**
- Outcome statement, priority, owner.
- Initial risk hint and dependencies.

**Owner**
- Human product/engineering owner.

### 2) Agentic specification
**Contains**
- Intent, non-goals, constraints.
- Policy/compliance boundaries.
- Risk tier and verification requirements.
- Rollback/restore expectations.

**Owner**
- Human accountable owner (agent may draft).

### 3) Implementation plan
**Contains**
- Ordered execution steps.
- Expected PR per step.
- Dependencies, assumptions, and escalation triggers.

**Owner**
- Agent executor drafts; engineering lead validates.

### 4) Step PR(s)
**Contains**
- Link to spec reference and plan step ID.
- Change summary and risk tier.
- Automated checks status and required reviewer fields.

**Owner**
- Agent executor authors; reviewer controls approval.

### 5) Prompt change request (prompt-control artifact)
**Contains**
- Prompt/config baseline reference and target revision.
- Intent type for the change request (one of: `debug_fix`, `configuration`, `fine_tuning`, `policy_hardening`, `cost_latency_optimization`, `style_alignment`, `tool_routing`).
- Summary of requested change and rationale.
- Failure/debug context (symptom, reproduction, observed behavior).
- Expected behavior after change and risk assessment.
- Manual session trace summary when human prompting sessions were used (session ID/time range, prompts summary, response summary, decisions made, and extracted follow-up actions).
- Linked spec IDs, plan step IDs, PR IDs, and evaluation evidence.

**Owner**
- Prompt debugger/configurator authors; responsible human owner approves per risk policy.

### 5.1) Manual prompt session trace (required when applicable)
**Contains**
- Session metadata (who ran it, when, environment/tooling used).
- Prompt summary (not necessarily full raw content if sensitive).
- Response summary and key observations.
- Decisions made and rationale.
- Linked prompt change request ID and linked spec/plan/PR IDs.

**Owner**
- Human operator who ran the manual prompting session.

### 6) Evidence package
**Contains**
- Test/build/lint results.
- Security and policy scan outputs.
- Traceability links (spec, plan, PR).
- Rollback/restore proof and runbook link.
- Operational/cost evidence where required.

**Owner**
- Platform automation generates; agent assembles; human validates completeness.

### 7) Verification decision record
**Contains**
- Reviewer decision (approved/rejected/conditional).
- Reasoning tied to risk and policy.
- Exceptions, if any, with owner and expiry.

**Owner**
- Responsible human reviewer.

### 8) Deployment and monitoring record
**Contains**
- Release metadata and environment scope.
- Observability checks and alert links.
- Rollback trigger criteria and status.

**Owner**
- Platform/operations with human go/no-go accountability.

### 9) Retrospective update artifact
**Contains**
- Issues observed, root causes, and actions.
- Template/policy/gate changes.
- Follow-up owners and due dates.

**Owner**
- Human leads; agent may draft.

## Artifact quality rules
- Every artifact has a clear owner and timestamp.
- Every PR is linked to both spec and plan step.
- Every prompt-control change is captured in a prompt change request artifact.
- Every manual prompting session that influences implementation or behavior is summarized in a trace artifact and linked to the prompt change request.
- Every high-risk change has explicit human sign-off.
- Every release has rollback/restore readiness evidence.
- Exceptions are explicit, time-bound, and auditable.
- Evidence artifacts must carry a retention class and retention duration according to policy.
- Manual prompt session traces must be redacted for sensitive data before broader reviewer distribution.
- Access to artifacts must be role-scoped; high-risk or sensitive traces are restricted to approved reviewer/owner groups.

## Minimum metadata schema (recommended)
Use these fields across artifacts:
- `artifact_id`
- `artifact_type`
- `owner`
- `risk_tier`
- `status`
- `linked_spec_id`
- `linked_plan_step_id`
- `linked_prompt_change_id` (nullable; required only when prompt-control changes are involved)
- `created_at`
- `updated_at`
- `retention_class`
- `retention_duration_days`
- `access_level`
- `contains_sensitive_prompt_context`

## Related documents
- `workflow.md`
- `agent-roles.md`
- `transition-plan.md`

