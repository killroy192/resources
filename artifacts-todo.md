# Cursor AI Bootcamp — Artifact Checklists

Work through each artifact top to bottom. Check off each box as you complete it. Every artifact ends with a self-check against the evaluation criteria — use it before you submit.

---

## Artifact 1 — Project Guidance Setup (Rules, AGENTS.md, Skill)

### To do

- [ ] Create a `.cursor/rules` file (or `.cursor/rules/*.mdc` files) with project rules
  - [ ] Keep each rule short, scoped and actionable
  - [ ] Make sure rules don't conflict with each other
- [ ] Create `AGENTS.md` (or equivalent project guidance) containing:
  - [ ] A project map (what lives where)
  - [ ] Coding conventions
  - [ ] How to operate the repo (build, run, test)
- [ ] Create at least one `SKILL.md` describing a repeatable workflow:
  - [ ] Steps to follow
  - [ ] Inputs and outputs
  - [ ] When to use it
- [ ] (Optional) Add a slash command
- [ ] Organize the evidence: clear file locations, working links, tidy structure

### Self-check before submitting

- [ ] Are the rules short, scoped, actionable and non-conflicting?
- [ ] Does AGENTS.md give a project map, conventions and repo operation guidance?
- [ ] Is the SKILL.md workflow repeatable, with inputs, outputs and "when to use"?
- [ ] Is everything reusable and maintainable, not one-off?
- [ ] Is the evidence clean — links, locations and structure easy to follow?

---

## Artifact 2 — Custom Subagent or MCP Integration

### To do

- [ ] Pick a **real workflow problem** (not a demo for demo's sake)
- [ ] Build one custom subagent or MCP integration for it
- [ ] Place the files in the expected locations:
  - [ ] `.cursor/agents/` (for a subagent) or `.cursor/mcp.json` (for MCP)
  - [ ] `/evidence/agent-or-mcp.md` (documentation)
  - [ ] Example output or demo note
- [ ] In the documentation, cover:
  - [ ] Purpose and use case
  - [ ] Clear responsibility and scope
  - [ ] Allowed tools
  - [ ] Forbidden actions
  - [ ] Read/write boundary
  - [ ] Human approval gates
  - [ ] Security / data notes
- [ ] Capture working evidence: chat logs and a safe demo output

### Self-check before submitting

- [ ] Does it solve a real workflow problem, not just show off complexity?
- [ ] Is the responsibility and scope clearly defined?
- [ ] Is there working evidence — config, command, output, demo or safe execution proof?
- [ ] Are safety boundaries explicit (allowed tools, forbidden actions, read/write limits)?
- [ ] Is the approval and security design thought through?
- [ ] Is it documented well enough for someone else to reuse?

---

## Artifact 3 — Story → Spec → Plan → PR (Full Traceability)

### To do

- [ ] Start from an original work item / story and save it
- [ ] Write an AI-ready spec from the story
- [ ] Run Plan Mode and save the plan output
- [ ] Create a context map (which files/docs the AI needed and why)
- [ ] Review the plan as a human and write review notes
- [ ] Document the human decisions you made (what you accepted, changed, rejected — and why)
- [ ] Implement and open a PR; save the PR link
- [ ] Collect tests/checks evidence
- [ ] Capture the verification step output
- [ ] Export/save the chat logs

### Self-check before submitting

- [ ] Can a reviewer trace story → spec → plan without gaps?
- [ ] Is the spec high quality (clear, complete, testable)?
- [ ] Is the plan high quality?
- [ ] Is the context map complete and accurate?
- [ ] Is the verification evidence convincing?
- [ ] Do the review summary and final decision clearly explain the outcome?

---

## Artifact 4 — Prioritized AI Use Cases for Your Team

### To do

- [ ] Identify **at least 5** AI-assisted engineering use cases for a real team
- [ ] Make each use case the right shape:
  - [ ] Specific team workflow — not vague like "use AI for tests"
  - [ ] Clear before/after process step
  - [ ] Risk and verification described up front
  - [ ] Small enough for a real team to actually try
- [ ] For each use case, provide:
  - [ ] Impact rating
  - [ ] Risk rating
  - [ ] Effort rating
  - [ ] Recommended AI workflow pattern
  - [ ] Required context (what the AI needs to know)
  - [ ] Verification approach
- [ ] Prioritize the use cases
- [ ] Create a value stream map showing where the use cases fit in the process

### Self-check before submitting

- [ ] Are the use cases real, specific and relevant?
- [ ] Is the impact / risk / effort scoring reasoned, not arbitrary?
- [ ] Does the chosen workflow pattern fit each use case?
- [ ] Does the value stream map show real process integration?
- [ ] Are the next steps actionable and prioritized?

---

## Artifact 5 — Ship It (Working Result + Release Readiness)

### To do

- [ ] Produce a working result: PR link, demo link, deployment note or deployability note
- [ ] Include the implementation diff
- [ ] Collect tests/checks evidence (automated checks and/or manual QA)
- [ ] Write review notes: summary, blockers, anything missing
- [ ] Write release notes, including a rollback plan if needed
- [ ] Document known risks and limitations
- [ ] Record the final merge or deployability decision

### Self-check before submitting

- [ ] Does the working result exist and match the spec?
- [ ] Does the verification evidence prove the key behavior?
- [ ] Is it review-ready: summary, blockers, missing evidence, final decision?
- [ ] Is it release-ready: notes, observability/flag decision, rollout thinking?
- [ ] Is rollback / risk control covered?
- [ ] Was scope kept disciplined and the result maintainable?

---

## Demo Video — 10-minute walkthrough

After your five artifacts are done, record a **~10-minute screen walkthrough**. Open your repo, show the files, talk through what you built. No slides, no formal intro — just show the work.

**Record with Teams** (start a meeting with yourself) or any tool that gives an auto-transcript. Don't edit the transcript with an agent — we check.

### Structure (10 minutes)

- [ ] **0:00–2:00 · Artifact 1 — your AI toolkit.** Open your repo and show your tools. For each: what it does and when it's used. Skills/commands ("handles X, I invoke it when…"), rules ("runs passively whenever the agent touches [area]"), AGENTS.md (open it, point out 2–3 things and why the agent needs them).
- [ ] **2:00–4:00 · Artifact 2 — agents.** Show your agent/sub-agent setup: read the title line, show the chain if it calls others, show one example running (screenshot, formatted chat log, or quick live demo).
- [ ] **4:00–6:00 · Artifact 3 — agentic workflow (the main one).** Show the evidence chain: spec (business problem + what "done" looks like), plan (steps, TDD checkpoints / human approval gates), context package (hot/warm/cold if you have a context map), checks & review (one verification output — what you kept, what you fixed). **Connect back to Artifact 1** — point to where your tools actually showed up.
- [ ] **6:00–7:30 · Artifact 4 — AI in your SDLC.** Walk your 5 use cases fast, one sentence each. Call out any case where AI improves something *other* than writing code, or where you use AI to build a deterministic tool you later remove AI from.
- [ ] **7:30–9:30 · Artifact 5 — the deliverable (actual code).** Show it running or ready to merge: the PR/diff, tests passing (screenshot is fine), release notes + rollback plan (one sentence each on risk and rollback).
- [ ] **9:30–10:00 · One thing you'd do differently.** Optional, but likely a Viva question. If you have a genuine one, say it; otherwise end at 9:30.

### Before you record

- [ ] Repo is open, files load fast — no hunting around during the video
- [ ] You can show the implementation ran (PR, diff, or test output)
- [ ] You know which 1–2 moments in Artifact 3 directly use tools from Artifact 1
- [ ] One practice run out loud — 9:30–10:00 is the sweet spot

### Quick reminders

- **Show the file, don't describe it.** "Here's my skill" while pointing at a bullet list ≠ opening the skill file.
- **The thread matters.** The same story runs through all 5 — we check that what you built in Artifact 1 actually appears in Artifact 3.
- **Skip the apologies.** "This is still a bit rough" wastes time. Just show what you have.
