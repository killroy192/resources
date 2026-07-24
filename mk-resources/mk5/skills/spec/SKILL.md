---
name: generate-spec
description: Turns a user story into a structured implementation spec (no code). Use to cover request to generate a spec, write a story spec or prepare work for an implementation-plan agent.
disable-model-invocation: true
---

# Generate Spec

Produce **.md file only** — a structured spec. Another agent uses these to write a safe implementation plan.

## Hard rules

- **Do not implement** — no application code, tests, config, or migrations.
- **Do not propose code changes** — no diffs, snippets, pseudocode patches, or “change line X to Y”.
- **Do not write an implementation plan** — no step-by-step coding tasks, file edit sequences, or PR breakdowns.
- **Clarify, don’t build** — inventory behavior, scope, risks, and verification so a later agent can plan safely.

## Inputs

User story description

## Outputs

| Artefact | Default path |
|----------|----------------|
| Spec | `docs/<feature-slug>.spec.md` |

---

## Workflow

1. Run a grill-me session to fully understand the task. Ask focused questions until you have enough information about the business goal, current behavior, expected behavior, constraints, edge cases, and any ambiguities. Challenge vague requirements and identify missing information.
2. When you have enough context, summarize your understanding and ask for my confirmation. Do not generate the specification until I confirm.
3. I confirm, produce a specification using exactly the following structure. The specification should be implementation-agnostic, precise, complete, and suitable for product, engineering, and QA alignment before implementation begins. Use the [spec template](./spec.template.md). Keep the spec readable for product and engineering.
4. Run subagent to review and critique the spec, list blocking findings. Find:
  4.1 Blocking questions
  4.2 Conflicting business context
  4.3 Scope creep risks
  4.4 Risky assumptions
  4.5 Weak acceptance criteria
  4.6 Suggested improvements
