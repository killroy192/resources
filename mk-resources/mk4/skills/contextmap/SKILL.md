---
name: generate-context-map
description: Turns a feature spec and implementation plan into a structured context map document (no code). 
disable-model-invocation: true
---

# Generate Context Map

Produce **.md file only** — a structured context map. Another agent uses these as part of implementation context package.

## Hard rules

- **Do not implement** — no application code, tests, config, or migrations.
- **Do not propose code changes** — no diffs, snippets, pseudocode patches, or “change line X to Y”.

## Inputs

Current task

## Outputs

| Artefact | Default path |
|----------|----------------|
| Context map | `docs/context-maps/<feature-slug>.contextmap.md` |

---

## Workflow

Using the feature name

1. inspect the relevant resources  
2. produce a context map using [context map template](./contextmap.template.md)