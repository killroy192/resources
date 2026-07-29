Use only with [plan skill](./SKILL.md). Section titles must match exactly.

### Confirmed Facts

Facts verified from the specification and codebase.

### Assumptions

Technical assumptions made while planning.

### Files / Modules Involved

List the areas of the codebase that will likely be modified or added.

### Implementation Plan

Break the work into small, atomic, dependency-ordered steps. Each step should clearly describe what needs to change and why, without prescribing low-level implementation details or code.

When defining implementation steps, follow these principles:

1. Build incrementally. Start with the simplest implementation that satisfies the current objective, then iterate by adding functionality, handling edge cases, and improving robustness. Each step should leave the system in a working, testable state. This enables validating the solution in realistic conditions before adding complexity.
2. Follow a Test-Driven Development (TDD) approach whenever practical. Before each implementation step, include a testing step that defines how the expected behavior will be verified. Depending on the change, this may be a unit, integration, or end-to-end test. Implementation should follow the tests so that each increment is validated before moving to the next step. Avoid large batches of changes that cannot be verified until the end.

### Risks

Potential technical risks, dependencies, migrations, or compatibility concerns.

### Out Of Scope

Explicitly list work that is intentionally excluded from this implementation.

### Verification

Map each Acceptance Criterion from the specification to one or more verification activities (manual test, automated test, API check, integration test, etc.), ensuring every criterion is covered.

Present them as a table with the following columns:

ID | Acceptance Criterion | Verifiable By

"Verifiable By" should contain values such as Manual Test, Automated Test, API Check, UI Check, or Integration Test.
