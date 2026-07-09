# Spec Section Guide

Use with [SKILL.md](SKILL.md). Section titles must match exactly.

## Business Goal

Well detailed and structured answer to the question: why this work matters to users or the product. Outcome-focused, not technical.

## User / System Problem

Pain today: what users cannot do, or what the system lacks. Tie to observable behavior.

## Current Behavior

Factual inventory from the codebase. Split by layer if helpful (frontend, API, data). No “should” language.

## Expected Behavior

User-visible and system-visible outcomes after the story is done. Bullet list is fine. Avoid naming specific functions or line numbers.

## Technical Scope

Bounded work: layers likely touched, kinds of changes (new UI control, new endpoint parameter)

Do **not** include code, diffs, or ordered implementation steps. High-level overview only.

## Out Of Scope

Explicit exclusions to prevent scope creep (other features, refactors, URL state, backend if frontend-only, etc.).

## Constraints

Stack, patterns, data limits, compatibility requirements, tests that must keep passing. Facts from the repo, not preferences.

## Acceptance Criteria

Numbered, testable statements (AC-1, AC-2, …). Prefer a table with a “Verifiable by” column (test, manual, API check).

Each criterion should be independently checkable.

## Assumptions

Beliefs taken as true for this spec (exact match vs range, sync vs async, no new dependencies). Distinguish from constraints (hard limits).