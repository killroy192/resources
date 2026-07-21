# Primary task example 1 — New integration API with ambiguous domain rules

> **Reference shape** condensed from a real bootcamp submission story (**FS07-3521** — ESN: fulfilled sales orders by equipment make).  
> Illustrative for mentees: copy the **card structure**, not the product. Your primary task must come from **your** backlog.

| Field | Value |
|-------|--------|
| **Type** | Primary task (full workflow) |
| **Source** | [FS07-3521](https://eci-solutions.atlassian.net/browse/FS07-3521) · Epic FS07-3442 |
| **Repos** | On-prem SOAP service + cloud router/Swagger · company DB procs |
| **Complexity signals** | Ambiguous domain rules · cross-repo side effects · edge-case filter surface · consumer contract |

---

## User story

**As a** downstream integration consumer,  
**I want to** retrieve fulfilled sales orders by equipment make (whole-word match) and a fulfillment watermark datetime,  
**So that** I can register accounts/devices from ship-to / bill-to / equipment identity without dual-entry.

---

## Problem / context

Existing sales-order operations return commerce-heavy payloads and do not match the consumer’s make + fulfillment-watermark shape. Jira AC mention “Fulfilled,” word match on Make / Make Description, delta filtering, and a compact registration-oriented response — but several rules are easy to implement **plausibly and wrongly** (wrong date basis, header-only status vs any fulfilled detail, substring vs whole-word, MySQL regex on SQL Server, wrong equipment join path).

---

## Why a spec is required before coding

Coding from the raw ticket produced a first-round prototype with reasonable but incorrect assumptions (lookback on create date, header status only, wrong equipment linkage). A PM walkthrough was required to lock Synappx registration intent: fulfill-activity watermark, partial fulfill allowed, one row per serial, fulfill-first parties. **Without that critique loop, the architecture and filters look “done” and still fail the consumer.**

---

## Acceptance criteria (ticket-shaped)

| ID | Scenario | Expected |
|----|----------|----------|
| AC1 | Fulfillment filter | Only orders with fulfilled equipment activity (clarify header-only vs any fulfilled detail with SME) |
| AC2–AC4 | Make word match | Match whole word on Make **or** Make Description; exclude substrings (`Sharp` ≠ `Sharpie`); case-insensitive |
| AC5 | Delta / watermark | Datetime compared against fulfillment activity; caller owns incremental sync clock |
| AC6–AC8 | Payload | Ship-to / bill-to addresses + equipment identity (serial, MAC, make/model fields) as specified |

---

## Out of scope

- Sibling REST / alternate API ticket blocked by this SOAP op
- Unrelated host/UI products
- Commerce amounts, pricing, full line catalogs, pagination (unless later required)

---

## Suggested phases (usable intermediate states)

1. **Spec + SME lock** — AI-ready spec; resolve fulfill vs watermark, match rules, row grain; human critique.
2. **On-prem contract + data path** — dedicated op + proc/DTO path; unit/integration tests for AC match & fan-out.
3. **Cloud route + docs** — authorize consumer; Swagger / completeness checks.
4. **Verification package** — AC ↔ tests/SQL evidence; known limitations.
5. **PR + release notes** — reviewable diff, rollback/deploy notes as required by the team.

---