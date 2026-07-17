---
name: generate-plan
description: Turns spec into a structured implementation plan. Use when the user asks to create a plan or uses plan mode.
disable-model-invocation: true
---

# Generate Plan

Use Plan Mode to produce **.md file only** — a structured implementation plan. Another agent uses plan and spec (already created) to create a context map and verification plan.

## Hard rules

- **Do not implement** — no application code, tests, config, or migrations.
- **Do not propose code changes** — no diffs, snippets, or “change line X to Y”.

## Inputs

| Input | Required | Notes |
|-------|----------|--------|
| Feature spec | Yes | Under `docs/` or pasted in chat |

## Outputs

| Artefact | Default path |
|----------|----------------|
| Implementation Plan | `docs/<feature-slug>.plan.md` |

---

## Workflow

Before planning:

- inspect relevant files
- ask blocking technical questions if needed
The plan must include:
- confirmed facts
- assumptions
- files/modules involved
- Atomic, unambiguous implementation steps that clearly describe what needs to change. Avoid premature implementation details.
- risks
- explicit non-goals
- verification mapped to acceptance criteria