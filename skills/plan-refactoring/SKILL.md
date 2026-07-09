---
name: generate-plan
description: Turns spec into a structured refactoring implementation plan. Use when the user asks to create a refactoring plan.
disable-model-invocation: true
---

# Generate Spec

Use Plan Mode. This is a refactor of <target>. Do not edit any files — produce a plan only. Observable behavior must remain unchanged.

Read the actual code first. Base every statement on what you found, cite file paths, and label anything unconfirmed as an assumption.

## Hard rules

- **Do not implement** — no application code, tests, config, or migrations.
- **Do not propose code changes** — no diffs, snippets, or “change line X to Y”.

## Inputs

Refactoring task description

## Outputs

| Artefact | Default path |
|----------|----------------|
| Implementation Plan | `docs/<feature-slug>.refactroing-plan.md` |

---

## Workflow

Before planning:

- inspect relevant files
- ask blocking tehnical questions if needed

The plan must include:

  1. Change type & goal — what kind of refactor this is, what it improves, and what's explicitly out of scope.

  2. Current behavior map — what the code observably does today:
      - inputs/outputs at the boundary
      - entry points (all real callers, not just exports)
      - side effects (writes, events, external calls)
      - flags/config that branch behavior
      - contracts and invariants callers rely on
      - existing tests that pin this behavior — and behaviors with no coverage

  3. Context pack — files the implementer will need: what will change, what guards it, what to consult only if surprised, what to ignore.

  4. Staged plan (TDD) — small stages, each leaving the repo green. Before moving code with no coverage, add characterization tests first. Name the check that gates each stage.

  5. Behavior verification map — every behavior from #2 mapped to how it gets verified after the refactor, including edge cases (empty inputs, error paths, flag combinations). Flag anything unverifiable.

  6. Risks & assumptions — ranked risks with mitigations, assumptions a human should confirm, and how to roll back mid-refactor.