# Cursor AI Bootcamp — Participant Resources

Everything you need to work through the bootcamp in one place: the course map, the five artifacts you'll submit, and a ready-to-use Cursor toolkit (skills, rules, MCP config).

**Start here, then keep this open all week.**

---

## The big picture

The bootcamp is **one continuous engineering story**, not nine separate Cursor topics. You follow an engineer joining a project and gradually building a mature AI-assisted delivery workflow:

```text
Task / Work Item
→ Spec
→ Plan
→ Context
→ Team Toolset
→ Verification
→ Safe Refactoring
→ MCP / Subagents
→ Release Readiness
→ Review & Merge Decision
```

The point isn't to generate more code with AI. It's to **operate AI as part of a controlled, reviewable, verifiable engineering workflow** — deciding not just *"can we build this?"* but *"should we, how much agency do we allow the agent, and when do we stop?"*

---

## How to use this repo

1. **Read the course map below** so you can see how each session hands off to the next and which artifact it feeds.
2. **Copy the toolkit into your project** — `skills/`, `rules/`, and `mcp.json` live under your repo's `.cursor/` directory (see [Toolkit](#toolkit)).
3. **Work the checklists** in [`artifacts-todo.md`](./artifacts-todo.md) — one per artifact, each ending with a self-check against the evaluation criteria.
4. **Record your demo** using the *Demo Video* section at the end of `artifacts-todo.md`.

Submission: **five artifacts by Friday 5 PM of Week 2**, with evidence links (not just prose).

---

## Course map — the 9 masterclasses

Each masterclass reveals the next engineering problem and adds evidence toward specific Week-2 artifacts.

| # | Masterclass | The problem it solves | Feeds |
|---|-------------|-----------------------|-------|
| MK1 | Everything Before Coding Is Context | First project, first task — you discover that everything before coding is context, and that *more* context isn't automatically better. | *(shared mental model)* |
| MK2 | Plan Mode & Controlled Implementation | Plan Mode can't invent missing business context. You improve the planning input, review the plan, cut scope creep, and approve only the first safe step. | Artifact 3, 5 |
| MK3 | Context Engineering: Hot / Warm / Cold Layers | A bug in an unfamiliar area — you build a reviewable context map instead of dumping everything in. | Artifact 3, 4 |
| MK4 | Cursor Team Toolset: Rules, AGENTS.md, Skills & Commands | The same guidance is retyped in every chat — you convert stable context into reusable project-level configuration. | Artifact 1 |
| MK5 | Verification-First Development with Lightweight Eval Rubrics | "Looks correct" isn't enough — you map acceptance criteria to proof and gate on evidence. | Artifact 3, 5 |
| MK6 | Safe Refactoring, Architecture & Migration Work | A refactor request — you classify the work, lock current behavior, stage it, and approve only the first safe step. | Artifact 3, 5 |
| MK7 | MCP & Subagents in Cursor | Manual copying of Jira/GitHub/logs — you choose CLI vs API vs MCP vs Subagent and build one bounded, safe capability. | Artifact 2 |
| MK8 | Safe Release for AI-Generated Code | Green checks aren't release readiness — you prepare observability, failure modes, flag decision, and rollback. | Artifact 5 (+ Artifact 4) |
| MK9 | AI-Assisted Code Review & Production-Ready PR | "Tests are green — can we merge?" — you review the evidence package, classify findings, and apply an explicit, human-owned merge decision. | Artifact 3, 5 |

Every session now follows the same rhythm: a realistic project moment → a first attempt that falls short → the framework → a live demo tied to a decision → an explicit human review point → a before/after → the artifact it feeds → a durable takeaway.

**Week 2** is your build sprint: turn this experience into the five submitted artifacts.

---

## The five artifacts

Full checklists and self-checks live in [`artifacts-todo.md`](./artifacts-todo.md).

| # | Artifact | What it is | Quality bar |
|---|----------|------------|-------------|
| 1 | Specs, Skills & Cursor Project Configuration | Reusable specs, `.cursor/rules`, `AGENTS.md`, Cursor Skills (`SKILL.md`), optional commands | Reusable by another engineer without extra explanation |
| 2 | Working Agents & MCP Integrations | At least one custom Cursor subagent or MCP integration | Safe by default; read-only preferred unless write is justified |
| 3 | Agentic Workflow End-to-End | Documented flow: spec → plan → code → tests/checks → deployable PR | Shows the full chain from story to production-ready PR |
| 4 | Use Case Backlog and Process Playbook | 5+ AI use cases with impact/risk ratings, a playbook, and a lightweight value stream map | Prioritized and actionable, not a generic brainstorm |
| 5 | Deployed Deliverable | Working code, deployed or deployable, with verification and rollback notes | Merge-ready or demo-ready with evidence it works |

---

## Toolkit

Copy these into your project's `.cursor/` directory so Cursor picks them up:

| In this repo | Copy to | What it is |
|--------------|---------|------------|
| `skills/` | `.cursor/skills/` | Reusable workflows — see the [skills catalog](./skills/README.md) |
| `rules/` | `.cursor/rules/` | Passive rules the agent follows automatically |
| `mcp.json` | `.cursor/mcp.json` | MCP servers (Atlassian, Miro) — complete OAuth in Cursor after copying |
| `agent.example.md` | `AGENTS.md` (adapt) | Example project-guidance file for the practice codebase |

Which skill supports which session:

| Masterclass | Skill |
|-------------|-------|
| MK2 — Plan Mode & Controlled Implementation | [`spec`](./skills/spec/SKILL.md) (planning input), [`plan`](./skills/plan/SKILL.md), [`plan-tdd`](./skills/plan-tdd/SKILL.md) |
| MK3 — Context Engineering | [`contextmap`](./skills/contextmap/SKILL.md) |
| MK5 — Verification-First Development | [`verification`](./skills/verification/SKILL.md) |
| MK6 — Safe Refactoring & Migration | [`plan-refactoring`](./skills/plan-refactoring/SKILL.md) |
| MK8 — Safe Release | [`release-strategy`](./skills/release-strategy/SKILL.md) |
| Value stream map & diagrams (Artifact 4) | [`miro`](./skills/miro/SKILL.md) |

---

## Where to start

- New here? Read this file top to bottom, then open [`artifacts-todo.md`](./artifacts-todo.md).
- Ready to configure your project? See [Toolkit](#toolkit) and the [skills catalog](./skills/README.md).
- Ready to record? Jump to *Demo Video* at the end of [`artifacts-todo.md`](./artifacts-todo.md).
