# A5 — Use Case Backlog & Process Playbook

**Proves:** Where this team should use AI/automation next — derived from a **measured** Portal SDLC, not a generic list.

---

## Checklist

- [x] SDLC JSON — live ADO metrics + Findings / UCs
- [x] AS-IS value stream — narrative (5 Findings)
- [x] Playbook — 5 use cases (impact · risk · effort · proof)
- [x] Findings ↔ UCs aligned across json / md / / playbook

---

## How to read this

1. **SDLC** — what the path is and what the last 30 days measured.  
2. **AS-IS md** — five Findings coded on the map (diagnosis).  
3. **Playbook** — five use cases that attack those Findings (prescription).

Findings ≠ use cases. Finding = what’s true. Use case = before→after + how we’d prove it.

---

| Finding | Plain meaning | Use case |
|---------|---------------|----------|
| **1** | Don’t **skip** the written spec | **UC-1** |
| **2** | ~3h review is fine; optional Lore + `/pre-pr-review` | **UC-2** |
| **3** | No required PR checks; Sonar ≠ deploy | **UC-4** Hard Sonar gate (Sonar + lint + ≥90%) |
| **4** | Coverlet ~87.7% blocks that gate for now | **UC-3** Story AC proof · **UC-4** Phase A→B |
| **5** | Deploy after merge is Manual → auto **Dev** | **UC-5** |

### UC-3 vs UC-4

- **UC-3 Story AC proof (`verification.md`)** = scoped tests that prove **this story’s ACs**, saved in `verification.md`. **Not Sonar. Not a coverage %.**  
- **UC-4 Hard Sonar gate (Sonar + lint + ≥90%)** = require those checks on every PR (hygiene first, then require).  
- **Only one Sonar UC: UC-4.**

**Say it out loud:** UC-3 = write the AC proof file · UC-4 = Hard Sonar gate on every PR.

Detail: [`ai-use-case-playbook.md`](ai-use-case-playbook.md).

---

## What’s in each file

| File | Role |
|------|------|
| [`LBMH.Services.Portal-SDLC.json`](LBMH.Services.Portal-SDLC.json) | Machine metrics + Findings/UC strings |
| [`as-is-value-stream.md`](as-is-value-stream.md) | Full narrative + Findings |
| [`ai-use-case-playbook.md`](ai-use-case-playbook.md) | UC-1…5 backlog + priority |
