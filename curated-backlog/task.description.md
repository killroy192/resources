# Curated Backlog — Assignment Requirements

## Purpose

Between masterclass sessions, each mentee picks work from their own project and gets mentor approval before starting. The backlog is **one required primary task** plus **one optional** task (typically MCP / subagent) — enough to run the full agentic workflow (story → AI-ready spec → plan → context → implementation → verification → PR / release readiness).

## Backlog composition

| Required | Count | What it is |
|----------|-------|------------|
| **Primary task** | **1** | A real Jira (or equivalent) story that can carry Artifact 3 (+ evidence toward 1 and 5) end to end |
| **Optional second task** | 0–1 | Only if useful — typically MCP / subagent on a real workflow friction (often used *on* the same primary story) |

Mentor reviews and approves task selection and scope **before** work starts.

---

## 1 · Primary task — what “good enough” looks like in practice

**Goal:** One ticket complex enough that coding from the raw Jira text alone is likely to encode the **wrong** business rules or architecture — so a human-reviewed AI-ready spec is mandatory.

Successful bootcamp submissions clustered around these shapes (not toy “sort toggle” slices):

| Shape | What made it work |
|-------|-------------------|
| **Integration / new API op** | Ambiguous domain filters, multi-repo surface, consumer-facing contract |
| **API parity with existing UI** | CRUD/search that must mirror MainApp validation and conventions |
| **Read-model / UI expansion** | Large field surface, display rules, de-dupe, schema-first discovery |
| **Client UX on existing persistence** | Can work if AC + edge cases are real — weaker if “infrastructure already there” and little to decide |

The task should hit **at least two** of:

- Ambiguous or easy-to-misread domain rules (status vs watermark, whole-word match, license gates, …)
- Cross-module or multi-repo side effects (service + cloud router, UI + API mapping, …)
- A meaningful edge-case / validation surface
- A multi-step user or integrator flow
- Enough scope to stage into **3–5 phases** with usable intermediate states

**Good signals (from real tickets):**

- Jira AC that still leave open questions a PM/SME must lock
- “Follow the pattern of op/endpoint X” — but filters, payload, or semantics differ
- Schema or live DB must be checked before mapping (do not invent column names)
- Teammates would ask “but what happens when…?” more than twice
- First AI pass is likely to guess wrong without a critique / second round

**Too thin for a solo primary task (avoid as the only backlog item):**

- Pure polish with no decision surface
- Standalone debug ticket with no delivery story
- Pure refactor with no product outcome
- Six mini-tasks that only mirror masterclass demos

Thin work may appear *inside* the primary task (fix-up, small refactor phase, Rules/Skills while implementing) — not as separate required backlog slots.

### Card fields for mentor review

Write the primary task up so a mentor can approve without opening the whole epic. Mirror the story cards that worked in submissions:

1. **Source** — Jira/ADO key + link (required when it exists)
2. **User story** — As a / I want / So that
3. **Problem / context** — why today’s behavior fails the consumer
4. **Why a spec is required** — what would go wrong if you coded from Jira alone
5. **Acceptance criteria** — numbered, testable; note “Verifiable by” where useful
6. **Out of scope** — explicit non-goals / blocked siblings
7. **Suggested phases** — 3–5 steps with usable intermediate states
8. **Repos / surfaces** — which apps, layers, or contracts are in play

Filled-in references (condensed from real submission stories — use as **shape**, pick **your** ticket):

- [`task.example1.md`](./task.example1.md) — integration API with ambiguous fulfillment semantics (**FS07-3521**-shaped)
- [`task.example2.md`](./task.example2.md) — license Metrics / SiteMetrics expansion (**LBMH20-386**-shaped)

Also in the same complexity band: hand-written CRUD API with MainApp validation parity (**MFGR10-51092**-shaped). Favorites-only UX (**DIST06-5306**-shaped) can pass if AC/edge cases are solid, but prefer tickets where wrong assumptions are costly.

---

## 2 · Optional second task — MCP or custom subagent

Add a second backlog item only for Artifact 2 friction that is not already covered while delivering the primary task.

**Shape that matched submissions:**

- Concrete pain (manual Jira/SQL/Postman copy, pre-PR checklist, schema lookup, …)
- One bounded capability (MCP **or** subagent), preferably exercised **on the same primary story**
- Explicit allowed tools, forbidden actions, read/write boundary, human approval gates
- Prefer read-only unless write is justified

**Do not** invent a second feature for symmetry. Pulling the Jira story / live schema into the primary-task spec via MCP counts — document it on the primary card.

---