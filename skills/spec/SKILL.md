---
name: generate-spec
description: Turns a user story into a structured implementation spec (no code). Use when the user asks to generate a spec, write a story spec or prepare work for an implementation-plan agent.
disable-model-invocation: true
---

# Generate Spec

Produce **.md file only** — a structured spec. Another agent uses these to write a safe implementation plan.

## Hard rules

- **Do not implement** — no application code, tests, config, or migrations.
- **Do not propose code changes** — no diffs, snippets, pseudocode patches, or “change line X to Y”.
- **Do not write an implementation plan** — no step-by-step coding tasks, file edit sequences, or PR breakdowns.
- **Clarify, don’t build** — inventory behavior, scope, risks, and verification so a later agent can plan safely.

If the user asks to implement in the same turn, complete spec artefact first and stop unless they explicitly cancel spec-only mode.

## Inputs

User story description

## Outputs

| Artefact | Default path |
|----------|----------------|
| Spec | `docs/<feature-slug>.spec.md` |

---

## Workflow

Copy and track progress:

```
Spec generation:
- [ ] Step 1 — Read story description and explore available resources
- [ ] Step 2 - Ask questions about task. Try to understand business context and use-case scenarios as detailed as possible.
- [ ] Step 3 — Write structured spec from story
- [ ] Step 4 — Critique and Self-check (no implementation leakage)
```

### Step 3 Details — Structured spec from story

Transform the story into a spec using **exactly** these sections (headings and order):

1. **Business Goal**
2. **User / System Problem**
3. **Current Behavior**
4. **Expected Behavior**
5. **Technical Scope**
6. **Out of scope**
7. **Constraints**
8. **Acceptance Criteria**
9. **Assumptions**

Use the [spec section guide](spec-section-guide.md) for what belongs in each section. Keep the spec readable for product and engineering.

### Step 4 — Critique and Self-check

Review this spec as if you are the engineer who will later create a development plan. Do not implement anything. Find:

1. Blocking questions
2. Conflicting business context
3. Scope creep risks
4. Risky assumptions
5. Weak acceptance criteria
6. Suggested improvements
