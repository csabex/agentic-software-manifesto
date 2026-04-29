---
title: "Agentic Specification Example (Versioned)"
description: "Example of a production-ready agentic specification with versioning and revision history."
spec_id: "SPEC-PROJ-CSV-EXPORT"
version: "1.0"
kind: specification
status: ready
owner: "product-owner@company.com"
tech_owner: "eng-lead@company.com"
last_updated: "2026-04-29"
---

# Agentic Specification Example (Versioned)

## 0) Specification metadata
- **Spec ID:** `SPEC-PROJ-CSV-EXPORT`
- **Current version:** `1.2.0`
- **Status:** `ready`
- **Risk tier:** `medium`
- **Domain:** `projects`
- **Linked backlog item:** `BL-4312`
- **Linked implementation plan:** `PLAN-PROJ-CSV-EXPORT-v1`
- **Linked prompt change request:** `PCR-PROJ-CSV-EXPORT-ESCAPING-01` (if applicable)

## 1) Versioning policy
- **Version format:** `MAJOR.MINOR.PATCH`
- **MAJOR:** breaking change to intent/scope, risk model, or acceptance criteria.
- **MINOR:** additive behavior, new non-breaking requirements, or extra checks.
- **PATCH:** wording fixes, clarifications, typo fixes, no behavioral change.
- Every merged PR must reference both `spec_id` and `spec_version`.

## 2) Revision history
| Version | Date | Author | Change type | Summary |
|---|---|---|---|---|
| `1.0.0` | 2026-04-20 | product-owner | MAJOR | Initial approved spec for CSV export capability. |
| `1.1.0` | 2026-04-24 | eng-lead | MINOR | Added audit logging and filename determinism requirements. |
| `1.1.1` | 2026-04-25 | agent-executor | PATCH | Clarified escaping rules; no behavior change. |
| `1.2.0` | 2026-04-29 | security-reviewer | MINOR | Added restricted-field policy checks and medium-risk verification gate updates. |

## 3) Intent
Enable users to export the filtered Projects table as CSV while preserving authorization boundaries, auditability, and operational safety.

## 4) Non-goals
- Redesigning the Projects page.
- Changing filtering/sorting semantics.
- Supporting custom CSV schemas per user.

## 5) Scope
### In scope
- Add `Export CSV` action to Projects UI.
- Add backend endpoint for CSV generation.
- Preserve existing filters/sort behavior in export.
- Emit audit events for success/failure.
- Add automated tests and policy checks.

### Out of scope
- New permissions model.
- Bulk background exports.
- Third-party storage integrations.

## 6) Inputs and constraints
- Inputs:
  - current filter/sort params from table query state,
  - authenticated user/session context,
  - tenant/workspace context.
- Constraints:
  - exclude restricted fields by policy,
  - enforce max row limit,
  - handle escaping/quoting correctly,
  - maintain bounded memory usage.

## 7) Required protocol
1. Agent updates implementation plan step statuses before coding.
2. Agent opens stepwise PRs tied to `spec_id` + plan step ID.
3. CI gates must pass before reviewer sign-off.
4. Required evidence package must be attached to each PR.
5. Human reviewer approves merge based on risk-tier policy.

## 8) Implementation plan linkage
- **Plan ID:** `PLAN-PROJ-CSV-EXPORT-v1`
- **Planned steps:**
  1. UI button and loading/error states.
  2. Backend endpoint and CSV generation logic.
  3. Policy enforcement and audit events.
  4. Tests, docs, and rollout notes.

## 8.1) Prompt debug/config linkage (optional)
- **Prompt change request ID:** `PCR-PROJ-CSV-EXPORT-ESCAPING-01`
- **Prompt artifact version:** `0.3.0`
- **Reason:** Debugging inconsistent escaping behavior for multi-line fields in agent-generated code paths.
- **Expected impact:** Stable escaping behavior with no restricted field leakage.
- **Change summary requirement:** PR must include a short summary of requested prompt-control changes and why they were needed.

## 9) PR linkage requirements
Each PR must include:
- `spec_id: SPEC-PROJ-CSV-EXPORT`
- `spec_version: 1.2.0`
- `plan_step: <step-id>`
- `prompt_change_id: <pcr-id>` (if prompt-control was changed)
- `risk_tier: medium`
- evidence links (tests/security/policy/audit)
- rollback notes

## 10) Verification gates (medium risk)
### Automated gates
- unit/integration tests pass,
- lint/build pass,
- security/policy scans pass,
- restricted-field checks pass.

### Human gates
- responsible reviewer validates spec/protocol compliance,
- security reviewer sign-off required if field policy changes.

### Operational gates
- deployment via controlled pipeline,
- monitoring checks in place,
- rollback path validated.

## 11) Evidence package requirements
- Test report links.
- Security/policy scan output links.
- Audit event examples (success + failure).
- Traceability links: spec -> plan step -> PR -> release.
- Rollback/restore procedure link.

## 12) Acceptance criteria
- `Export CSV` is visible and functional for authorized users.
- Export respects active filter/sort state.
- Restricted fields never appear in output.
- Audit events are emitted for success and failure.
- Verification gates are passed and evidence is complete.

## 13) Change control rules
- Any scope/behavior change requires spec version update before merge.
- PRs referencing stale spec versions must fail policy checks.
- High-impact changes can be paused pending synchronous review.

## 14) Status lifecycle
`draft` -> `ready` -> `in_execution` -> `verified` -> `superseded`

## 15) Supersession
When replaced, set:
- `status: superseded`
- `superseded_by: <new-spec-id>@<new-version>`
- keep immutable revision history for audit.

