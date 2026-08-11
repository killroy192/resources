---
name: generate-verification-plan
description: Turns a spec, context map and implementation plan into a structured verification plan. Use when the user asks to create a verification plan
disable-model-invocation: true
---

## Hard rules

- **Do not evaluate** — create only evaluation plan.
- **Do not propose code changes** — no diffs, snippets, pseudocode patches, or “change line X to Y”.

## Inputs

| Input | Required | Notes |
|-------|----------|--------|
| Feature spec | Yes | Under `docs/` or pasted in chat |
| Feature implementation plan | Yes | Under `docs/` or pasted in chat |
---

## Output

Verfication plan .md file in `docs` folder

---

## Workflow

1. Analyze the specification, implementation plan, and code diff.
2. Identify the repository commands for type checking, linting, building, smoke testing and code complexity analyzing.
3. Create an evaluation plan following verification gates. For each gate:

   * Assign a score from **0–2** (0 = fails, 1 = partially meets, 2 = fully meets).
   * List the tools, commands, or scripts used during the evaluation (for example, the eslint command used to lint TypeScript files, the test runner used for validation, or build/typecheck commands).
   * Briefly explain the reasoning behind the score.
   * Describe the actions required to achieve a full score, if applicable.

Verification gates:

* **Specification compliance** – Does the implementation satisfy every acceptance criterion defined in the specification?
* **Scope control** – Does the change include only what was requested, without unnecessary additions or unrelated modifications?
* **Test quality** – Do the tests validate the expected behavior including edge cases (not just increase code coverage), and would they fail if the implementation were incorrect?
* **Risk** – Does the change introduce any security, performance, reliability, data integrity, or rollout risks?
* **Maintainability** – Is the implementation easy to understand, maintain, and extend for a developer unfamiliar with the codebase?
* **Evidence** – Is there sufficient evidence (tests, logs, screenshots, or other artifacts) for a reviewer to verify the change without re-reading the entire implementation?