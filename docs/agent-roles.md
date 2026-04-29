---
title: "Agent Roles"
description: "Role definitions and decision rights for humans, agents, and platform systems in the agentic workflow."
version: 1.0
kind: roles
---

# Agent Roles

## Purpose
Define who does what in an agentic organization, including ownership boundaries and approval rights.

## Role model

### 1) Product owner (human)
**Owns**
- Outcome definition, scope boundaries, and priority.
- Acceptance criteria and business risk framing.

**Approves**
- Spec readiness for work that changes customer behavior.
- Major scope or requirement changes.

### 2) Engineering lead (human)
**Owns**
- Technical direction and architecture constraints.
- Risk tier assignment with security/compliance input.

**Approves**
- High-risk technical decisions.
- Readiness for deployment in high-impact scenarios.

### 3) Responsible reviewer (human)
**Owns**
- Final risk-based verification decision.
- Confirmation that change matches spec and policy.

**Approves**
- Required sign-offs before merge/release.
- Exception handling when policy bypass is requested.

### 4) Security/compliance reviewer (human, as required)
**Owns**
- Validation of security/privacy/compliance controls.
- Guidance for high-risk categories and regulated domains.

**Approves**
- Mandatory checks for high-risk and regulated changes.

### 5) Agent executor (AI agent)
**Owns**
- Drafting or updating specs and implementation plans.
- Implementing plan steps and opening traceable PRs.
- Assembling evidence artifacts for verification.

**Does not own**
- Final sign-off, policy exceptions, or accountability transfer.

### 6) Platform automation (systems/tooling)
**Owns**
- Enforcement of mechanical gates (CI, policy, scanning).
- Evidence collection, trace metadata, and reporting.
- Controlled deployment pipeline behaviors.

**Does not own**
- Product or business judgment decisions.

### 7) Prompt debugger/configurator (human or designated agent)
**Owns**
- Diagnosing prompt failures, drift, and unsafe behaviors.
- Proposing prompt-control updates with explicit intent and risk notes.
- Producing a traceable prompt change artifact linked to affected specs/PRs.
- Maintaining intent taxonomy for prompt-control work (for example: `debug_fix`, `configuration`, `fine_tuning`, `policy_hardening`, `cost_latency_optimization`, `style_alignment`, `tool_routing`).
- Ensuring human manual prompting sessions are summarized in trace artifacts when they influence implementation decisions.

**Approves**
- Prompt/config changes only when the approver is a designated human owner.
- Escalation requests for high-risk prompt changes for routing to required human approvers.

**Approval guardrail**
- AI agents may draft recommendations and evidence, but final approval/sign-off authority for prompt-control changes remains human at every risk tier.

## Decision rights (RACI-style shorthand)
- **Spec authoring:** Agent (R), Human owner (A).
- **Risk tier assignment:** Engineering lead + security (A), Agent (R support).
- **Implementation planning:** Agent (R), Engineering lead (A).
- **PR execution:** Agent (R), Reviewer (A for merge readiness).
- **Prompt/config change request authoring:** Prompt debugger/configurator (R), Human owner (A).
- **Verification sign-off:** Responsible reviewer (A), automation/agent provide evidence (R support).
- **Deployment go/no-go:** Engineering lead or delegated human approver (A).

## Escalation triggers
Escalate to synchronous human review when:
- risk tier changes upward,
- customer-visible behavior changes unexpectedly,
- security/policy checks fail repeatedly,
- rollback confidence is low,
- incident risk or blast radius grows.

## Separation of duties
- The same actor should not both generate and solely approve high-risk changes.
- High-risk approvals require at least one independent human reviewer.
- Policy exceptions must be logged with owner and expiration.
- Human-accountability principle applies to all sign-off decisions, including prompt-control updates.

## Related documents
- `workflow.md`
- `agentic-artifacts.md`
- `transition-plan.md`

