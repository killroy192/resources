# Portal AI Use Case Playbook (A4)

**From:** five AS-IS **Findings** · [`as-is-value-stream.md`](as-is-value-stream.md) / SVG  
**Metrics:** [`LBMH.Services.Portal-SDLC.json`](LBMH.Services.Portal-SDLC.json) · **2026-06-16 → 2026-07-16** · adequacy **93** · pulled **2026-07-16**  
**Exemplar:** LBMH20-386 Dev+Prod App **29594/29598** + Api **29595/29599** ✅ · [PR 9220](https://dev.azure.com/ECI-LBMH/LBMH-Spruce/_git/LBMH.Services.Portal/pullrequest/9220)  
**Copies:** `dmares/artifacts/a4-use-case-playbook/` · `.portal-work/LBMH20-386/`

Findings = diagnosis. Use cases = prescription (before→after + proof).  
Ratings **H/M/L:** Impact · Risk · Effort (one Portal squad).

---

## UC-3 vs UC-4 (read first)

| | **UC-3 Story AC proof (`verification.md`)** | **UC-4 Hard Sonar gate (Sonar + lint + ≥90%)** |
|--|---------------------------------------------|---------------------------|
| **One sentence** | For *this* story: run the tests that prove the ACs; paste commands + green output into `verification.md`. | Make ADO **require** Sonar + lint + Coverlet ≥90% before merge. |
| **Scope** | One story / one PR | Whole repo / every PR |
| **Sonar?** | **No** | **Yes** — this is the **only** Sonar UC |
| **Why both?** | Coverlet is ~**87.7%** today — turning on UC-4 tomorrow freezes merges. UC-3 is how we prove ACs **now** (and still after UC-4 — a green fleet gate ≠ “these ACs passed”). | Phase A: raise Coverlet to ≥90%. Phase B: require the checks. |

**Say it out loud:** UC-3 = write the AC proof file · UC-4 = Hard Sonar gate on every PR.

---

## Finding → use case

| Finding | Plain meaning | Use case |
|---------|---------------|----------|
| **1** | Don’t **skip** a written spec (Spec↔Jira order is fine) | **UC-1** |
| **2** | ~3h human review is fine; optional Lore + `/pre-pr-review` | **UC-2** |
| **3** | No required PR checks; Sonar ≠ `/deploy` | **UC-4** Hard Sonar gate |
| **4** | Coverlet ~87.7% — can’t trust hard ≥90% yet | **UC-3** Story AC proof now · **UC-4** Phase A then B |
| **5** | Merge doesn’t deploy → auto **Dev** 472/440 | **UC-5** |

---

## Backlog index

| ID | Title | Finding(s) | Where | Impact | Risk | Effort | On 386? |
|----|-------|------------|-------|--------|------|--------|---------|
| **UC-1** | Don’t skip the written spec | 1 | Laptop | H | L | L | ✅ `/portal-spec` |
| **UC-2** | Lore + `/pre-pr-review` before Ready | 2 | PR | M | L | L–M | ✅ + harden |
| **UC-3** | Story AC proof (`verification.md`) | 4 | Laptop + PR | H | L | L | ✅ Phase 6 |
| **UC-4** | Hard Sonar gate (Sonar + lint + ≥90%) | 3, 4 | PR checks | H | M | M | Not yet |
| **UC-5** | Auto-queue Dev after merge | 5 | main → deploy | H | M | M | Manual `/deploy` ✅ |

---

## UC-1 — Don’t skip the written spec

**Where:** Laptop · **Finding:** 1

Jumping ticket → code drops `/api/`, mocks, schema gaps into review. Preferred for tech-heavy Portal work: **spec → Jira → plan → code**. Class/386 **Jira → spec** is fine when the ticket exists. Fight **missing** the spec, not the order.

| Before | After |
|--------|-------|
| Ticket → code | Written `spec.md` → plan → code |

**AI pattern:** `/portal-spec` → human approve → Plan Mode → `/portal-context` → implement  
**Context:** Hot = Jira + `spec.md` · Warm = `agents.md`, schema/verify rules · Cold = rest of repo  
**Done when:** AC IDs in plan + verification; diff inside plan; human approve before code  
**Ratings:** Impact **H** · Risk **L** · Effort **L**

---

## UC-2 — Lore + `/pre-pr-review` before Ready (optional)

**Where:** PR · **Finding:** 2

Non-instant PRs ~**2.8h** open — mostly human review. That’s **pretty good**. Optional: Lore + `/pre-pr-review` catch DI/fixture nits before humans. Humans still merge. No auto-merge.

| Before | After |
|--------|-------|
| Open PR → humans find checklist nits | UC-3 AC proof green → optional Lore → `/pre-pr-review` → Ready → human review |

**AI pattern:** Lore (optional) → `/pre-pr-review {KEY}` → APPROVED / WITH CONDITIONS / NOT APPROVED  
**Context:** Hot = spec, plan, verification, diff · Warm = past PR threads · Cold = unrelated PRs  
**Done when:** Explicit gate status; fewer nit threads; ~3h stays healthy  
**Ratings:** Impact **M** · Risk **L** · Effort **L–M**

---

## UC-3 — Story AC proof (`verification.md`)

**Where:** Laptop + PR · **Finding:** 4  
**Title means:** prove **this story’s acceptance criteria** with scoped tests, and save the evidence in `verification.md`.  
**Not** Sonar. **Not** a fleet Coverlet %. **Not** UC-4.

**What you do (before Ready):**

1. Kill the running API (file locks).  
2. Run the filtered tests that map to the ACs.  
3. Write **commands + green output** into `.portal-work/{KEY}/verification.md` (AC → evidence matrix).  
4. Note known fleet debt (e.g. Coverlet ~87.7%) — don’t pretend the whole suite is at 90%.

That’s how **386** shipped (Phase 6). Optional QC **445** (~80% red from Coverlet) is **not** the story AC proof.

**Still needed after UC-4:** UC-4 Hard Sonar gate = “repo checks are green.” UC-3 = “**these** ACs for **this** change are proven.” Different jobs.

| Before | After |
|--------|-------|
| “Tests passed” with no file / shrug at red 445 | Every ≥3-AC story: scoped green commands + `verification.md` |

**AI pattern:** `portal-verification.mdc` → scoped commands → AC → evidence matrix  
**Context:** Hot = ACs + test filters · Warm = prior verification files · Cold = full Coverlet report  
**Done when:** Matrix filled; scoped exit 0 — **proven** on 386  
**Ratings:** Impact **H** · Risk **L** · Effort **L**

---

## UC-4 — Hard Sonar gate (Sonar + lint + ≥90%)

**Where:** Required **PR** checks · **not** `/deploy` · **Findings:** 3, 4  
**Title means:** ADO **requires** Sonar quality gate + lint (when Web touched) + Coverlet ≥90% before merge.  
**This is the only Sonar / quality-gates use case.**

Today: no required checks on `main`; human review only. Sonar is **not** on 440/441/472. Coverlet ~**87.7%** → requiring ≥90% **tomorrow** freezes the team.

| Phase | Do | Then |
|-------|----|------|
| **A — Hygiene** | Dedicated work: Api.Tests Coverlet ≥90% (not inside a feature PR) | 445 coverage green a few times |
| **B — Flip switch** | Require on PR: **Sonar** + lint (when Web touched) + Coverlet ≥90% | UC-3 Story AC proof stays as every-story habit |

| Before | After |
|--------|-------|
| Merge on human review only | Phase A healthy → Phase B required Hard Sonar gate |

**AI pattern:** AI-assisted coverage gaps → prove 445 → branch policy  
**Context:** Hot = Coverlet, branch policies, Sonar key · Warm = 445 YAML · Cold = old 445 logs  
**Done when:** Phase A green streak; PRs can’t complete without checks; early fail rate stays low  
**Ratings:** Impact **H** · Risk **M** (skip Phase A → freeze) · Effort **M**

---

## UC-5 — Auto-queue **Dev** after merge

**Where:** main → Manual `/deploy` · **Finding:** 5

App **0%** fail (**33/33**, ~74s) · Api **0%** (**45/45**, ~616s). 386 Dev+Prod all green same day. Pain = **memory** — merge starts nothing. Fix: on **merge to main**, auto-queue **Dev** 472/440. **Prod stays manual.** Never default Infra **441** (Dev Infra ~23% fail).

| Before | After |
|--------|-------|
| Hope someone runs `/deploy` | Merge → auto Dev 472/440 → human promotes Prod |

**Pattern:** Path classifier + ADO queue (extend `/deploy` skill)  
**Context:** Hot = paths, pipeline IDs, `awsAccount` · Warm = deploy docs · Cold = old CDK failures  
**Done when:** Classifier accurate; measure merge → Dev start; Dev green before Prod  
**Ratings:** Impact **H** · Risk **M** · Effort **M**

---

## Don’t do these

| Temptation | Why not |
|------------|---------|
| Two Sonar UCs | Deploy never runs Sonar; **only UC-4** |
| Turn on ≥90% + Sonar tomorrow | Coverlet ~87.7% freezes merges — Phase A first |
| Call UC-3 a coverage % | UC-3 = Story AC proof (`verification.md`); % is UC-4 |
| Auto-Prod on merge | Promote Prod after Dev smoke |
| Auto 441 every merge | Dev Infra fails too often |
| Call ~3h review broken | It’s fine; UC-2 is optional help |

---

## What to do next

| P | Do | UC | Done when… |
|---|----|-----|------------|
| P0 | Written spec before coding | UC-1 | Spec exists before implement |
| P0 | Story AC proof on feature PRs | UC-3 | `verification.md` + green scoped commands |
| P1 | Lore + `/pre-pr-review` before Ready | UC-2 | Pre-PR on 2 agent PRs; humans merge |
| P1 | Coverlet ≥90% | UC-4 Phase A | 445 coverage green 3× |
| P2 | Require Hard Sonar gate on PR | UC-4 Phase B | After Phase A; no merge freeze |
| P2 | Auto-queue Dev 472/440 on merge | UC-5 | Classifier ≥95% |

---

## Grader order

1. SDLC JSON (30d metrics)  
2. AS-IS md + SVG (Findings 1–5)  
3. This playbook (UC-1…5)
