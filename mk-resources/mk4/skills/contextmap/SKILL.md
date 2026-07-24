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

Using the feature name, inspect the relevant resources and produce a context map using the following structure:

**Hot context** — directly required for the feature right now:

* Current spec and plan
* Active files
* Logs/screenshots

**Warm context** — reusable guidance relevant to the feature:

* AGENTS.md / rules / skills
* Team conventions
* ADRs
* Known constraints

**Cold context** — investigate only if needed:

* Relevant repo areas
* Documentation
* Past PRs
* Monitoring/logs
* Story tickets

**Resources to ignore:**

* Deprecated documentation
* Generated files
* Unrelated modules