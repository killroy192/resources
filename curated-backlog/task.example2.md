# Primary task example 2 — Expand an existing read model with strict display rules

> **Reference shape** condensed from a real bootcamp submission story (**LBMH20-386** — Portal: expand SiteMetrics on license record detail).  
> Illustrative for mentees: copy the **card structure**, not the product. Pick **one** primary task from **your** backlog (not both examples).

| Field | Value |
|-------|--------|
| **Type** | Primary task (full workflow) |
| **Source** | [LBMH20-386](https://eci-solutions.atlassian.net/browse/LBMH20-386) |
| **Repos** | License detail Metrics tab · existing SiteMetrics API · live DB schema |
| **Complexity signals** | Large field surface · de-dupe / exclude rules · schema-first discovery · cross-layer mapping + UI |

---

## User story

**As a** support engineer on the license detail page,  
**I want to** see the SiteMetrics values I already use elsewhere (especially EDI configuration) on the Metrics tab,  
**So that** I can answer routine customer questions without leaving the page for a fleet export or dashboard.

---

## Problem / context

The Metrics tab only shows a subset of SiteMetrics (snapshot, hard-coded features, remote-client cards). EDI enablement / last-used dates and many other categorized columns already exist in `SiteMetrics` and on the fleet dashboard, but are missing on the license page. A licensing-side `ediNames` string on another tab is a **different source** and does not replace SiteMetrics EDI flags.

---

## Why a spec is required before coding

Jira says “show additional SiteMetrics fields,” but delivery fails without locked rules:

- Full intended set vs “EDI only”
- Which columns are internal/ingest and must stay hidden
- No duplicates with the four existing cards
- Boolean / empty / sentinel-date display (`Yes`/`No`/`-`, muted styling for disabled)
- Schema-first column names (do not invent from naming alone)
- Coverage and test-path NFRs on **new/changed** code

Skipping the spec produces either a partial EDI card that still disappoints the requester, or a dump of the wrong columns.

---

## Acceptance criteria (ticket-shaped)

| ID | Criterion | Verifiable by |
|----|-----------|----------------|
| AC1 | Metrics section shows additional SiteMetrics fields already in DB (including EDI values expected by the requester) | Manual + mapping tests |
| AC2 | Values render as simple name/value pairs (no drill-in on this page) | UI |
| AC3 | No database schema changes | Review |
| AC4 | Unit tests for mapping; UI/smoke coverage for expanded grid / styling rules | `dotnet test` / frontend CI |
| AC5 | Team NFRs (e.g. coverage on new/changed code, zero new warnings) as stated on the ticket | Pipeline / local verify |

*Human interpretation locked in spec (example):* remaining category-backed fields after de-dupe + internal exclude; metadata-category cards; Yes/No with muted **No**; `-` for null/empty/sentinel dates.

---

## Out of scope

- Schema/migrations, CDK/pipeline changes
- Drill-in from license Metrics into the fleet dashboard
- Editing SiteMetrics; replacing the existing four cards
- Showing internal identity/ingest columns

---

## Suggested phases (usable intermediate states)

1. **Spec + schema discovery** — INFORMATION_SCHEMA / metadata categories; lock include/exclude and display rules; scope cap.
2. **Mapping / API payload** — extend site SiteMetrics response groups; unit tests (happy, disabled, empty, not-found).
3. **Metrics UI cards** — category cards, Yes/No/`-`, muted styling; smoke tests; mock fixtures parity.
4. **Pre-PR verification** — story AC proof, coverage on changed surface, human review gates.
5. **PR → approve → deploy** — release/rollback notes; demo evidence on the same story.

---