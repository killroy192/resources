---
name: generate-plan
description: Turns spec into a structured implementation plan. Use to cover request to create a plan or when plan mode is enabled.
disable-model-invocation: true
---

# Generate Plan (TDD)

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

1. Inspect spec for task
2. Inspect the relevant parts of the codebase.
3. Identify the files, modules, and components involved.
4. Ask only blocking technical questions if something cannot be determined from the codebase or specification. Otherwise, make reasonable assumptions and state them explicitly.
5. Produce the plan. The plan should be implementation-ready, unambiguous, incremental, and focused on minimizing risk while leaving implementation details to the coding phase. Use the following structure:

