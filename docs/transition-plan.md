---
title: "Transition Plan for an Agentic Organization"
description: "A phased plan to move from traditional software delivery to an agentic operating model."
version: 1.0
kind: plan
---

# Transition Plan for an Agentic Organization

## Objective
Move from ad-hoc AI-assisted development to a scalable, governed agentic operating model where:
- humans remain accountable for high-stakes decisions,
- agents execute routine implementation work,
- all changes are traceable from intent to verified outcome.

## Guiding outcomes (what success looks like)
- Faster cycle time for low/medium-risk changes without increasing incident rate.
- Consistent spec -> plan -> PR traceability across teams.
- Risk-based verification paths enforced by automation.
- Clear ownership boundaries between product, engineering, security, and platform.

## Scope and assumptions
- This plan applies to software/product teams, platform teams, and governance functions.
- Existing CI/CD and code review systems remain in place.
- Rollout is incremental; legacy workflows can coexist during transition.

## Operating model target state
- **Execution unit:** agentic specification.
- **Delivery unit:** reviewable PR(s) tied to spec and plan step.
- **Definition of done:** verified change (automated gates + required human decision points + evidence package).
- **Control model:** risk-tiered policies (`low`, `medium`, `high`) with explicit approval matrix.

## Phased transition plan

## Phase 0 (Weeks 0-2): Mobilize and baseline
### Goals
- Establish leadership alignment, ownership, and measurable baseline.

### Actions
- Form a transition working group: engineering, product, security, platform, compliance.
- Define baseline metrics from current workflow:
  - lead time,
  - PR size and review time,
  - change failure rate,
  - rollback frequency,
  - security/policy exceptions.
- Select 2-3 pilot teams with different risk profiles.

### Deliverables
- Transition charter and RACI.
- Baseline metrics report.
- Pilot team selection and timeline.

### Exit criteria (must pass)
- Transition working group staffed with named owners for engineering, product, security, and platform.
- Baseline metrics captured for at least the last two delivery cycles for each pilot team.
- Pilot teams approved with explicit risk-profile coverage (`low`, `medium`, `high` representative workload).

## Phase 1 (Weeks 3-6): Define standards and guardrails
### Goals
- Standardize artifacts, approvals, and minimum controls before broad rollout.

### Actions
- Publish standard templates:
  - agentic specification template,
  - implementation plan template,
  - PR template with required fields (spec link, plan step, risk tier, evidence, rollback notes).
- Define risk-tier policy matrix:
  - `low`: mostly automated path, sampled human review,
  - `medium`: required reviewer + full evidence checks,
  - `high`: explicit pre-approval + strict deployment controls.
- Define approval matrix by change type (security boundary, data model, customer behavior, infrastructure).
- Add branch protection and CI policy checks for mandatory metadata.

### Deliverables
- Organization-wide templates and policy matrix.
- Approval matrix and reviewer responsibilities.
- Automated policy enforcement in pilot repositories.

### Exit criteria (must pass)
- Standard templates published and adopted in 100% of pilot repositories.
- Branch protection and mandatory metadata checks enabled in 100% of pilot repositories.
- Approval matrix ratified by engineering leadership and security/compliance.

## Phase 2 (Weeks 7-10): Pilot execution
### Goals
- Validate that the operating model works in real delivery contexts.

### Actions
- Run pilot teams through full flow: spec -> plan -> stepwise PRs -> verified release.
- Enforce risk-tier pathways; no bypass without logged exception.
- Hold weekly pilot review for blockers, false positives, and policy friction.
- Track quality and throughput against baseline metrics.

### Deliverables
- Pilot scorecard (speed, quality, security, operational outcomes).
- Exception log and root-cause analysis.
- Draft improvements to templates, gates, and approval routing.

### Exit criteria (must pass)
- 100% of pilot changes follow spec -> plan -> stepwise PR linkage.
- Policy exception rate is stable or declining across the phase.
- Change failure rate and rollback rate are non-inferior to baseline for pilot teams.
- Reviewer capacity supports median time-to-verify within agreed SLO.

## Phase 3 (Weeks 11-14): Platform hardening
### Goals
- Convert pilot learnings into stable organizational capabilities.

### Actions
- Productize paved roads:
  - repo scaffolds with templates preinstalled,
  - PR bots for spec/plan linkage validation,
  - evidence collection and release checklists.
- Build org dashboards for:
  - spec coverage,
  - policy pass/fail rates,
  - time-to-verify,
  - rollback and incident indicators,
  - agentic cost signals (compute/tokens/licenses where applicable).
- Add training for reviewers and team leads on risk-based verification.

### Deliverables
- Hardened platform toolchain and onboarding kit.
- Shared dashboards and weekly governance report.
- Reviewer enablement material.

### Exit criteria (must pass)
- Paved-road scaffolds and PR/evidence bots are available and documented for all onboarded domains.
- Governance dashboards report flow, quality, control, risk, and cost metrics with weekly refresh.
- Reviewer training completion reaches agreed minimum coverage for participating teams.

## Phase 4 (Weeks 15-20): Scale-out
### Goals
- Expand to all eligible teams with federated governance.

### Actions
- Roll out by domain waves (e.g., internal tools -> product surfaces -> regulated workloads).
- Require minimum controls org-wide; allow domains to add stricter controls.
- Create monthly operating review:
  - throughput and reliability trends,
  - policy exceptions,
  - incident learnings,
  - cost/governance posture.

### Deliverables
- Organization-wide adoption plan completion.
- Domain-level control profiles.
- Monthly operating review cadence.

### Wave pause/rollback criteria
Pause new domain onboarding and require remediation when any condition is met:
- change failure rate regresses beyond agreed threshold for two consecutive reporting periods,
- policy exception rate rises above agreed threshold without corrective trend,
- audit completeness drops below required minimum for regulated/high-risk domains,
- reviewer queue breaches time-to-verify SLO for two consecutive periods.

Resume scale-out only after corrective actions are implemented and one full reporting cycle returns to threshold compliance.

### Exit criteria (must pass)
- All eligible domains onboarded with minimum controls enabled.
- Domain-level stricter control profiles documented where applicable.
- Monthly operating review is active with named owners and action tracking.

## Phase 5 (Ongoing): Continuous optimization
### Goals
- Improve speed and safety without policy drift.

### Actions
- Run recurring retrospectives on failed gates, incidents, and bottlenecks.
- Tune risk-tier rules and review load balancing.
- Retire unnecessary controls and tighten weak controls based on evidence.
- Update templates and training quarterly.
- Run formal risk-tier calibration quarterly (engineering leadership + security + platform) using incident, exception, and near-miss trends.

### Deliverables
- Quarterly policy/version updates.
- Control effectiveness report.
- Updated onboarding and playbooks.

### Ongoing health criteria
- Risk-tier calibration decisions are logged with rationale and effective date.
- Control changes include before/after metric impact in quarterly reports.

## Governance model (practical)
- **Central platform/governance owns:** minimum controls, policy engines, shared tooling, metrics standards.
- **Domain teams own:** delivery outcomes, domain-specific stricter controls, execution quality.
- **Security/compliance owns:** control validation for high-risk categories and regulatory alignment.
- **Engineering leadership owns:** accountability model, staffing of reviewers, incentive alignment.

## Metrics and KPIs
- **Flow metrics:** lead time, PR review time, deployment frequency, time-to-verify.
- **Quality metrics:** change failure rate, rollback rate, escaped defects.
- **Control metrics:** policy pass rate, exception rate, audit completeness.
- **Risk metrics:** high-risk change volume, high-risk incident count.
- **Cost metrics:** compute/token/license spend per delivered outcome (where measurable).

## Risk register and mitigations
- **Over-governance slows delivery**
  - Mitigation: strict risk-tiering; automate low-risk paths; review exception trends monthly.
- **Inconsistent adoption across teams**
  - Mitigation: mandatory templates, repo scaffolds, onboarding playbook, adoption scorecards.
- **Reviewer bottlenecks**
  - Mitigation: approval matrix, reviewer pools, load balancing, asynchronous evidence-first reviews.
- **Shadow workflows bypass controls**
  - Mitigation: branch protections, policy-as-code gates, transparent exception logging.
- **Tooling fragmentation**
  - Mitigation: paved-road defaults with limited approved variants.

## Implementation checklist
- [ ] Transition working group formed and chartered.
- [ ] Baseline metrics captured and pilot teams selected.
- [ ] Templates and risk-tier matrix published.
- [ ] Policy checks enforced in pilot repos.
- [ ] Pilot scorecard reviewed and adjustments made.
- [ ] Platform hardening completed (bots, dashboards, scaffolds).
- [ ] Organization-wide wave rollout complete.
- [ ] Quarterly optimization loop active.

