# Cursor AI Bootcamp — Participant Resources

Everything you need to work through the bootcamp in one place: the course map, masterclass assets, curated backlog examples, and five artifact templates.

**Start here, then keep this open all week.**

---

## The big picture

The bootcamp is **one continuous engineering story**. You follow an engineer joining a project and gradually building a mature AI-assisted delivery workflow:

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

---

## How to use this repo

1. **Read the course map below** to see how each session hands off to the next and which artifact it feeds.
2. **Select a ticket for implementation** using the [curated backlog description and examples](./curated-backlog/).
3. **Work through the checklists** in [`artifacts-todo.md`](./atifacts/artifacts-todo.md) — one per artifact, each ending with a self-check against the evaluation criteria.
4. **Optional: review the masterclass resources** in the [`mk-resources`](./mk-resources/) folder.

Submission: **five artifacts by 5 PM on Friday of Week 2**, with evidence links (not just prose).

---

## Course map — the 9 masterclasses

Each masterclass reveals the next engineering problem and adds evidence toward specific Week-2 artifacts.

| # | Masterclass | The problem it solves | Feeds |
|---|-------------|-----------------------|-------|
| MK1 | Everything Before Coding Is Context | First project, first task — you discover that everything before coding is context, and that *more* context isn't automatically better. | *(shared mental model)* |
| MK2 | Plan Mode & Controlled Implementation | Plan Mode can't invent missing business context. You improve the planning input, review the plan, cut scope creep, and approve only the first safe step. | Artifact 3, 4 |
| MK3 | Context Engineering: Hot / Warm / Cold Layers | A bug in an unfamiliar area — you build a reviewable context map instead of dumping everything in. | Artifact 3, 5 |
| MK4 | Cursor Team Toolset: Rules, AGENTS.md, Skills & Commands | The same guidance is retyped in every chat — you convert stable context into reusable project-level configuration. | Artifact 1 |
| MK5 | Verification-First Development with Lightweight Eval Rubrics | "Looks correct" isn't enough — you map acceptance criteria to proof and gate on evidence. | Artifact 3, 4 |
| MK6 | Safe Refactoring, Architecture & Migration Work | A refactor request — you classify the work, lock current behavior, stage it, and approve only the first safe step. | Artifact 3, 4 |
| MK7 | MCP & Subagents in Cursor | Manual copying of Jira/GitHub/logs — you choose CLI vs API vs MCP vs Subagent and build one bounded, safe capability. | Artifact 2 |
| MK8 | Safe Release for AI-Generated Code | Green checks aren't release readiness — you prepare observability, failure modes, flag decision, and rollback. | Artifact 4 (+ Artifact 5) |
| MK9 | AI-Assisted Code Review & Production-Ready PR | "Tests are green — can we merge?" — you review the evidence package, classify findings, and apply an explicit, human-owned merge decision. | Artifact 3, 4 |

Every session now follows the same rhythm: a realistic project moment → a first attempt that falls short → the framework → a live demo tied to a decision → an explicit human review point → a before/after → the artifact it feeds → a durable takeaway.

**Week 2** is your build sprint: turn this experience into the five submitted artifacts.

---

## The five artifacts

Full checklists and self-checks are in [`artifacts-todo.md`](./atifacts/artifacts-todo.md).

| # | Artifact | What it is | Quality bar |
|---|----------|------------|-------------|
| 1 | Specs, Skills & Cursor Project Configuration | Reusable specs, `.cursor/rules`, `AGENTS.md`, Cursor Skills (`SKILL.md`), optional commands | Reusable by another engineer without extra explanation |
| 2 | Working Agents & MCP Integrations | At least one custom Cursor subagent or MCP integration | Safe by default; read-only preferred unless write is justified |
| 3 | Agentic Workflow End-to-End | Documented flow: spec → plan → code → tests/checks → deployable PR | Shows the full chain from story to production-ready PR |
| 4 | Deployed Deliverable (Ship It) | Working code, deployed or deployable, with verification, release notes and a rollback plan | Merge-ready or demo-ready with evidence it works |
| 5 | Prioritized AI Use Cases & Value Stream Map | 5+ AI use cases with impact/risk/effort ratings, a playbook, and a value stream map (SDLC.json) | Prioritized and actionable, not a generic brainstorm |
