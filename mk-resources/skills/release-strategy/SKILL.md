---
name: release-strategy
description: Produces a release strategy document (impact analysis, metrics, rollback plan, risk management) for a set of changes before release. Use when the user asks to plan a release, assess release risk, or design a rollback/feature-flag strategy.
disable-model-invocation: true
---

# Release Strategy

Analyze a change (diff, PR, or feature) and produce a Release Strategy document covering impact, metrics, rollback, and risk management.

## Hard rules

- **Do not implement** — no application code, tests, config, or migrations.
- **Read-only research** — delegated subagents must not modify files.
- Every checklist answer must cite evidence (file/line or command output), not guesses.

## Inputs

| Input | Required | Notes |
|-------|----------|-------|
| Diff / PR / branch / feature description | Yes | What is being released |
| Target environment or rollout constraints | No | e.g. multi-tenant, self-hosted, single deploy |

---

## Workflow

Copy this checklist and track progress:

```
Release Strategy Progress:
- [ ] Step 1: Change analysis (subagent)
- [ ] Step 2: Metrics (subagent + synthesis)
- [ ] Step 3: Rollback strategy (subagent + synthesis)
- [ ] Step 4: Risk management (synthesis)
- [ ] Step 5: Save document
```

### Step 1: Change analysis — delegate to an `explore` subagent

Give the subagent the diff/branch/feature scope and ask it to return, with file/line citations:

- **Blast radius**: changed files/modules/services, their dependents, existing test coverage.
- **Impact checklist**, each answered `true`/`false` + one-line comment with evidence:
  1. Affects critical/core functionality (auth, billing, primary data write paths)?
  2. Affects data integrity (migrations, irreversible writes, backfills)?
  3. Backward compatible (API contracts, DB schema, config defaults)?
  4. Affects security posture (authn/authz, secrets, input validation, CORS)?
  5. Affects performance/scalability (hot paths, added latency, N+1 queries)?
  6. Affects third-party/external contracts (webhooks, integrations, sync protocols)?
  7. Cleanly reversible without data loss?
  8. Covered by existing automated tests (unit/integration/e2e)?
  9. Requires a database migration?
  10. Touches multiple user-facing surfaces at once (web, API, mobile, bot, etc.)?
- Add any other question relevant to this specific change, same true/false + comment format.

### Step 2: Metrics — delegate research, then synthesize

- Delegate to an `explore` subagent (can run in parallel with Step 1 and Step 3's research): find existing observability relevant to the changed area — logs, counters/metrics, dashboards, alerts, SLOs.
- Main agent: propose new metrics/logs to add. Each proposed metric must map to a risk flagged `true` in Step 1 — no speculative metrics for risks that don't apply.

### Step 3: Rollback strategy — delegate research, then synthesize

- Delegate to an `explore` subagent (can run in parallel with Steps 1–2): identify what rollback mechanisms actually exist in this repo — deploy/revert process, migration undo commands, feature-flag system, cache/queue infra.
- Main agent, using Step 2's metrics and Step 3's research:
  - **Trigger conditions**: which metric thresholds/signals should trigger a rollback.
  - **Rollback action list**: ordered, concrete steps (e.g. revert deploy, run migration undo, disable flag, purge cache, notify stakeholders).
  - **Post-rollback verification**: metrics/tests that must pass to confirm the rollback succeeded.

### Step 4: Risk management — main agent only, no subagent

Judgment call based on Step 1's blast radius/impact — do not delegate:

- Feature flag: yes/no + justification.
- Alternative rollout recommendation (canary, blue-green, phased rollout, overnight/off-peak build) with reasoning tied to blast radius and rollback complexity.

### Step 5: Save the document

Write the result to `docs/releases/<change-slug>.md` using the template below, then confirm the path to the user.

---

## Document template

```markdown
# Release Strategy: <change name>

## 1. Change Analysis
- Blast radius: ...
- Impact checklist:
  | # | Question | True/False | Comment |
  |---|----------|-------------|---------|

## 2. Metrics
- Existing metrics tracked: ...
- New metrics to add: ... (mapped to risk #)

## 3. Rollback Strategy
- Trigger conditions: ...
- Rollback actions:
  1. ...
- Post-rollback verification: ...

## 4. Risk Management
- Feature flag: yes/no — justification
- Rollout recommendation: ... — reasoning
```
