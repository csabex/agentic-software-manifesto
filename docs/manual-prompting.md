---
title: "Manual Prompting in an Agentic Workflow"
description: "Process definition for human manual prompting sessions, required artifacts, and integration with automated agentic delivery."
version: 1.0
kind: process
---

# Manual Prompting in an Agentic Workflow

## Purpose
Define how human manual prompting sessions are used safely and traceably inside an otherwise automated agentic workflow.

## Scope
This process applies when a human directly prompts an AI system and that session influences:
- implementation decisions,
- prompt-control behavior,
- architecture or policy interpretation,
- PR content, verification, or release decisions.

## Principles
- Manual prompting is allowed, but not "off-ledger."
- Any manual session that changes outcomes must be traceable.
- Human accountability remains explicit for high-stakes decisions.
- Manual and automated work follow the same risk-based controls.

## When to use manual prompting
- Ambiguous behavior that needs rapid exploratory debugging.
- Prompt/control tuning that benefits from iterative human judgment.
- Complex failure analysis where automated runs lack enough context.
- Domain/style alignment requiring human curation.
- Pre-work for `fine_tuning` or `tool_routing` changes.

## Required artifacts

### 1) Prompt change request (existing)
Use `prompt-change-request-example.md` pattern and include:
- intent type (`debug_fix`, `configuration`, `fine_tuning`, `policy_hardening`, `cost_latency_optimization`, `style_alignment`, `tool_routing`),
- linked spec and plan step,
- risk tier and expected impact.

### 2) Manual prompt session trace (required when applicable)
Create one trace per meaningful session or session batch.

Recommended fields:
- `manual_prompt_session_trace_id`
- `prompt_change_id`
- `session_owner`
- `started_at` / `ended_at`
- `environment` (tool/model/version)
- `prompt_summary`
- `response_summary`
- `decisions_made`
- `follow_up_actions`
- `linked_spec_id`
- `linked_plan_step_id`
- `linked_pr_ids`
- `risk_tier`
- `status`

### 3) PR linkage updates
Related PRs must include:
- `prompt_change_id`
- `prompt_change_version`
- `manual_prompt_session_trace_id` (if manual prompting influenced the PR)
- short summary of decisions derived from manual session(s)

## Process steps

### Step 1: Open or update prompt change request
- Define the prompt-control intent and success criteria.
- Assign risk tier and owner.
- Link governing spec and plan step.

### Step 2: Run manual prompting session(s)
- Human operator runs exploratory/diagnostic prompting.
- Capture concise prompt/response summaries (full transcripts optional, based on sensitivity rules).

### Step 3: Record session trace artifact
- Create/update `manual_prompt_session_trace` with decisions and follow-up actions.
- Link it to prompt change request and relevant spec/plan references.

### Step 4: Convert decisions into implementation deltas
- Translate manual session outcomes into concrete code/config/model changes.
- Ensure planned PR step remains aligned with governing spec and policy.

### Step 5: Execute automated path
- Agent and/or human opens stepwise PR(s).
- CI/policy/security gates run as normal.
- Reviewer validates traceability from manual session -> prompt change -> PR -> evidence.

### Step 6: Verify and close
- Verification decision references prompt change and manual session trace IDs.
- Close session trace as `verified` or `superseded`.
- Capture lessons in retrospective artifacts.

## Integration with automated agentic workflow
- Manual prompting is an extension of **Step 4: Agent execution** in `workflow.md`, not a bypass.
- Automated gates are unchanged by manual involvement.
- Risk escalation rules are unchanged; manual sessions can trigger higher review paths.
- "Done" still requires full evidence, traceability, and rollback/restore readiness.

## Risk and governance rules
- High-risk manual prompt outcomes require explicit human approver sign-off.
- Policy exceptions must be documented with owner and expiration.
- Sensitive data in prompts/responses must be redacted per security policy.
- Same actor should not solely generate and approve high-risk manual prompt changes.

## Minimal manual session trace template
```md
# Manual Prompt Session Trace
- manual_prompt_session_trace_id:
- prompt_change_id:
- session_owner:
- started_at:
- ended_at:
- environment:
- prompt_summary:
- response_summary:
- decisions_made:
- follow_up_actions:
- linked_spec_id:
- linked_plan_step_id:
- linked_pr_ids:
- risk_tier:
- status:
```

## Related documents
- `workflow.md`
- `agent-roles.md`
- `agentic-artifacts.md`
- `prompt-change-request-example.md`
- `agentic-specification-example.md`

