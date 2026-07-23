# Artifact 3 — Story → Spec → Plan → PR (Full Traceability)

> Purpose: prove a complete, gap-free chain from an original story to a merged PR — spec, plan, context map, human decisions, implementation, and verification. A reviewer must be able to trace story → spec → plan without gaps.

---

## Traceability chain (at a glance)

> One-row map of the whole chain so a reviewer can follow it fast.

| Stage | Artefact | Location / link |
|-------|----------|-----------------|
| Story | {original work item} | `{link}` |
| Spec | AI-ready spec | `{path}` |
| Spec creation review/chat logs | exported session | `{link}` |
| Plan | Plan Mode output | `{path}` |
| Plan review/chat logs | exported session | `{link}` |
| Context map | hot/warm/cold files | `{path}` |
| Verification | AC↔evidence table | `{path}` |
| Review notes | human review + decisions | `{path}` |
| PR | implementation | `{PR link}` |

---

### Verification

> Convincing evidence the key behaviour works. Tie each AC to proof.

| AC | Proof (test name / manual step) | Result |
|----|--------------------------------|--------|
| AC-1 | {evidence} | {pass / gap} |

- **Command(s) run:** `{command}`
- **Output:** `{link or paste location}`

---

### Human decisions & review notes

> Document what you accepted, changed, rejected — and why. This is where human judgement is visible.

| Decision | Accepted / Changed / Rejected | Why |
|----------|-------------------------------|-----|
| {decision} | {choice} | {reasoning} |

- **Review summary:** {overall verdict on the plan/implementation}

---