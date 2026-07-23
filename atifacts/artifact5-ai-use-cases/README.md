# A4 — Use Case Backlog & Process Playbook (15%)

**Graders:** [`../README.md`](../README.md)

**Proves:** Where this team should use AI/automation next — derived from a **measured** Portal SDLC, not a generic list.

**Metrics:** **2026-06-16 → 2026-07-16** · adequacy **93** · pulled **2026-07-16**  
**Exemplar deploy (same window):** LBMH20-386 Dev+Prod App **29594/29598** + Api **29595/29599** ✅  
**Identical copies:** [`.portal-work/LBMH20-386/`](../../../.portal-work/LBMH20-386/) (same four files)

---

## Checklist

- [x] SDLC JSON — live ADO metrics + Findings / UCs
- [x] AS-IS value stream — narrative + SVG (5 Findings)
- [x] Playbook — 5 use cases (impact · risk · effort · proof)
- [x] Findings ↔ UCs aligned across json / md / svg / playbook
- [x] Synced to `.portal-work/LBMH20-386/`

---

## A4 evidence chain

Open in order. Numbers lock across all four files.

| # | Item | Location | What it is |
|---|------|----------|------------|
| 1 | SDLC | [`LBMH.Services.Portal-SDLC.json`](LBMH.Services.Portal-SDLC.json) | Physical delivery path + **30d** station metrics · `asIsFindings` · `recommendedUseCases` |
| 2 | AS-IS diagram | [`Portal-AS-IS-Value-Stream.svg`](Portal-AS-IS-Value-Stream.svg) | Practice-style feedback diagram: M/A states, gates, **5 yellow Finding cards** |
| 3 | AS-IS narrative | [`as-is-value-stream.md`](as-is-value-stream.md) | Same states/numbers + live 386 Dev+Prod run table + Finding write-ups |
| 4 | Playbook | [`ai-use-case-playbook.md`](ai-use-case-playbook.md) | **UC-1…5** — start with the **UC-3 vs UC-4** box |

**Lock:** json = svg = md = playbook. **AS-IS only** — TO-BE = adopt UC-1…UC-5.

**Story / PR context:** [LBMH20-386](https://eci-solutions.atlassian.net/browse/LBMH20-386) · [PR 9220](https://dev.azure.com/ECI-LBMH/LBMH-Spruce/_git/LBMH.Services.Portal/pullrequest/9220)

---

## How to read this (3 minutes)

1. **SDLC** — what the path is and what the last 30 days measured.  
2. **SVG + AS-IS md** — five Findings coded on the map (diagnosis).  
3. **Playbook** — five use cases that attack those Findings (prescription).

Findings ≠ use cases. Finding = what’s true. Use case = before→after + how we’d prove it.

---

## 30d scoreboard

| Signal | Value |
|--------|-------|
| App **472** | **0%** fail · **33/33** · med **~74s** |
| Api **440** | **0%** fail · **45/45** · med **~616s** |
| Infra **441** | **17.6%** fail · Dev **23.1%** |
| QC **445** | **~80%** fail · Coverlet **~87.7%** |
| PR reviewish | **~2.8h** (n=8 excl-&lt;5m) |
| Required PR checks | **none** |
| Post-merge CD | **Manual** (`trigger: none`) |

---

## The five Findings → use cases

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
| [`Portal-AS-IS-Value-Stream.svg`](Portal-AS-IS-Value-Stream.svg) | One-page visual AS-IS |
| [`as-is-value-stream.md`](as-is-value-stream.md) | Full narrative + Findings |
| [`ai-use-case-playbook.md`](ai-use-case-playbook.md) | UC-1…5 backlog + priority |

---

## Changelog

| Date | Change |
|------|--------|
| 2026-07-17 | README → A1-style evidence chain; UC-3/UC-4 clarity |
| 2026-07-16 | Metrics window locked; 386 Dev+Prod exemplar runs |
| 2026-07-15 | AS-IS practice format + 5 UCs |
