# Artifact 4 — Ship It (Working Result + Release Readiness)

> Purpose: prove a working, review-ready and release-ready result that matches the spec. A reviewer must see the working result, convincing verification, review notes (summary, blockers, gaps), release notes with a rollback plan, known risks, and a final merge / deployability decision.

---

## Working result (at a glance)

> One-row map of the deliverable so a reviewer can find each piece fast.

| Item | Location / link |
|------|-----------------|
| PR | `{PR link}` |
| Demo / deployment note | `{link}` |
| Verification | `{path}` |
| Review notes | `{path}` |
| Release notes | `{path}` |
| Chat logs | `{path}` |
| Final decision | {Merge / Deployable / Blocked} |

---

### Verification evidence

> Convincing proof the key behaviour works — automated checks on CI and/or manual QA.

| AC / behaviour | Proof (test name / manual step) | Result |
|----------------|--------------------------------|--------|
| {AC-1} | {evidence} | {pass / gap} |

- **Automated checks:** `{CI link / command + output location}`
- **Manual QA:** {what was checked by hand, and result}

---

### Review notes

- **Summary:** {overall verdict — is it ready?}
- **Blockers:** {anything preventing merge, or "none"}
- **Missing evidence / gaps:** {what's incomplete, or "none"}
- **Final decision:** {Merge / Deploy / Hold — and why}

---

### Release notes

- **Release notes:** {what changes for users / operators}
- **Risk control:** {what to do if something goes wrong on prod, rollback or rollforward plan}
- **Observability / flag decision:** {feature flag, metrics, logging, rollout strategy}
- **Known risks & limitations:** {what could break, edge cases, scope not covered}
