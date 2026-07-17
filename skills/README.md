# Skills Catalog

Reusable Cursor workflows for the bootcamp. Copy this `skills/` folder into your project's `.cursor/skills/` directory so Cursor can load them. Each skill is a `SKILL.md` with a `name` (how it's invoked) and a `description` (when it triggers).

Most planning/spec skills are set to `disable-model-invocation: true` — you invoke them explicitly rather than letting the model auto-trigger.

| Skill (folder) | Invoke as | What it does | When to use it |
|----------------|-----------|--------------|----------------|
| [`spec`](./spec/SKILL.md) | `generate-spec` | Turns a user story into a structured, AI-ready spec (no code) — 9 fixed sections from business goal to acceptance criteria and assumptions. | The planning input for MK2 (Plan Mode & Controlled Implementation). Feeds Artifact 3. |
| [`plan`](./plan/SKILL.md) | `generate-plan` | Turns a spec into a structured implementation plan: confirmed facts, assumptions, files, atomic steps, risks, non-goals, verification. | After the spec — MK2 (Plan Mode). Feeds Artifact 3. |
| [`plan-tdd`](./plan-tdd/SKILL.md) | `generate-plan-tdd` | Same as `plan`, but interleaves unit-test creation after each step (TDD). | When you want a test-first plan — MK2 / MK5. |
| [`plan-refactoring`](./plan-refactoring/SKILL.md) | `generate-refactoring-plan` | A refactor-specific plan that preserves observable behavior: current-behavior map, staged TDD plan, behavior verification map, rollback. | Refactor or migration work — MK6. |
| [`contextmap`](./contextmap/SKILL.md) | `generate-context-map` | Produces a hot / warm / cold context map for a feature, plus what to ignore. | Working in large codebases — MK3 (Context Engineering). Feeds Artifact 3. |
| [`verification`](./verification/SKILL.md) | `generate-verification-plan` | Maps each acceptance criterion to a verification method across 6 gates and scores it. | Before you call work done — MK5 (Verification-First). Feeds Artifact 3 / 5. |
| [`release-strategy`](./release-strategy/SKILL.md) | `release-strategy` | Produces a release-strategy doc: blast-radius/impact analysis, metrics, rollback plan, risk management. | Before releasing a change — MK8 (Safe Release). Feeds Artifact 4 / 5. |
| [`miro`](./miro/SKILL.md) | `miro-mcp` | How to use the Miro MCP to create/read diagrams, docs, and tables (e.g. a value stream map). | Building the VSM or diagrams — Artifact 4. Requires the Miro MCP (see `mcp.json`). |

## The workflow these skills form

For a full feature, the spec/plan skills chain together — each produces a `.md` another step consumes:

```
story → spec → plan (or plan-tdd) → context-map → implement → verification → release-strategy → review/PR
```

That chain is exactly what Artifact 3 (Agentic Workflow End-to-End) documents.
