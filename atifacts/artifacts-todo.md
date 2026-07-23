# Cursor AI Bootcamp — Artifact Checklists

Work through each artifact top to bottom. Check off each box as you complete it. Every artifact ends with a self-check against the evaluation criteria — use it before you submit.

---

## Artifact 1 — Project Guidance Setup (Rules, AGENTS.md, Skill)

### To do

- [ ] Create a `.cursor/rules` file (or `.cursor/rules/*.mdc` files) with project rules
- [ ] Create `AGENTS.md` (or equivalent project guidance)
- [ ] Create at least one `SKILL.md` describing a repeatable workflow
- [ ] Organize the evidence: clear file locations, working links, tidy structure, see `./artifact1-tools/artifact.basic.template.md` as a basic example (modify according your needs)

### Self-check before submitting

- [ ] Are the rules short, scoped, actionable and non-conflicting?
- [ ] Does AGENTS.md provides valuable context that need to be loaded for every agent working in this repo, like project map comments, conventions and repo operation guidance?
- [ ] Is the SKILL.md workflow repeatable, with inputs, outputs and "when to use"?
- [ ] Is everything reusable, maintainable and shareable, not one-off?
- [ ] Is the evidence clean — links, locations and structure easy to follow?

---

## Artifact 2 — Custom Subagent and MCP Integration

### To do

- [ ] Pick a **real workflow problem** (not a demo for demo's sake)
- [ ] Build one custom subagent and MCP integration for it
- [ ] Organize the evidence: clear file locations, working links, tidy structure, see `./artifact2-mcp-subagents/artifact.basic.template.md` as a basic example (modify according your needs)

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
- [ ] Create an AI-ready spec from the story
- [ ] Run Plan Mode and save the plan output
- [ ] Create a context map (which files/docs the AI needed and why — hot/warm/cold)
- [ ] Review the spec and plan as a human and save review notes
- [ ] Document the human decisions you made on the spec and plan (what you accepted, changed, rejected — and why)
- [ ] Implement the change and verify it locally
- [ ] Collect verification evidence: tie each AC to proof (test name / manual step), collected locally
- [ ] Export/save the chat logs from the spec and plan sessions

### Self-check before submitting

- [ ] Can a reviewer trace story → spec → plan without gaps?
- [ ] Is the spec high quality (clear, complete, testable)?
- [ ] Is the plan high quality?
- [ ] Is the context map complete and accurate?
- [ ] Is the verification evidence convincing?
- [ ] Do the review summary and final decision clearly explain the outcome?

---

## Artifact 4 — Ship It (Working Result + Release Readiness)

### To do

- [ ] Produce a working result: PR link, demo link, deployment note or deployability note
- [ ] Collect verification evidence: tie each AC to proof — automated checks on CI and/or manual QA
- [ ] Write review notes: summary, blockers, missing evidence / gaps
- [ ] Write release notes (what changes for users / operators)
- [ ] Document risk control: rollback / rollforward plan if something goes wrong on prod
- [ ] Record the observability / feature-flag / rollout decision
- [ ] Document known risks and limitations
- [ ] Record the final merge or deployability decision
- [ ] Export/save the chat logs

### Self-check before submitting

- [ ] Does the working result exist and match the spec?
- [ ] Does the verification evidence prove the key behavior?
- [ ] Is it review-ready: summary, blockers, missing evidence, final decision?
- [ ] Is it release-ready: notes, observability/flag decision, rollout thinking?
- [ ] Is rollback / risk control covered?
- [ ] Was scope kept disciplined and the result maintainable?

---

## Artifact 5 — Prioritized AI Use Cases for Your Team

### To do

- [ ] Collect initial data
  - [ ] Create SDLC (states) for medium-size feature using [elivery-model.engx](https://delivery-model.engx.me/)
  - [ ] Describe the steps included in each state.
  - [ ] Add measurements, comments, and gateways for each step.
  - [ ] Save the result as SDLC.json — this is your value stream map and the source of truth for every metric.
- [ ] Derive Findings from the measured signals in SDLC.json (a Finding = a fact + its consequence, not a use case)
  - [ ] Code each Finding to exactly one station (state) on the map
  - [ ] Cite the exact metric from the JSON as evidence (label unmeasured metrics "not measured", never guess)
  - [ ] Aim for 3–6 crisp Findings; distinguish "healthy / leave alone" from "fix this"
- [ ] Identify **at least 5** AI-assisted engineering use cases, one per fixable Finding (or cluster)
- [ ] Make each use case the right shape:
  - [ ] Specific team workflow — not vague like "use AI for tests"
  - [ ] Clear before/after process step
  - [ ] Risk and verification described up front
  - [ ] Small enough for a real team to actually try
- [ ] For each use case, provide:
  - [ ] Link to the Finding and station it addresses
  - [ ] Impact rating (H/M/L)
  - [ ] Risk rating (H/M/L)
  - [ ] Effort rating (H/M/L)
  - [ ] Recommended AI workflow pattern
  - [ ] Required context (what the AI needs to know)
  - [ ] Verification approach (AC → test / manual step, metric baseline → target, mandatory human gate)
- [ ] Prioritize the use cases into a ranked backlog
  - [ ] Order by Impact · Risk · Effort (high impact + low risk + low effort first)
  - [ ] Give each a measurable "Done when…" exit criterion
  - [ ] Sequence dependencies explicitly (no gate enabled before its prerequisite)

### Self-check before submitting

- [ ] Are the use cases real, specific and relevant?
- [ ] Does every Finding cite a real metric from the JSON (no invented numbers; unmeasured labelled "not measured")?
- [ ] Does every Finding map to exactly one station and at least one use case?
- [ ] Is the impact / risk / effort scoring reasoned, not arbitrary?
- [ ] Does the chosen workflow pattern fit each use case?
- [ ] Does every use case have Impact · Risk · Effort and a verifiable "Done when"?
- [ ] Does the value stream map (SDLC.json) show real process integration?
- [ ] Does prioritisation respect dependencies (no gate enabled before its prerequisite)?
- [ ] Are the next steps actionable and prioritized?

---

## Demo Video — 10-minute walkthrough

After your five artifacts are done, record a **~10-minute screen walkthrough**. Open your repo, show the files, talk through what you built. No slides, no formal intro — just show the work.

**Record with Teams** (start a meeting with yourself) or any tool that gives an auto-transcript. Don't edit the transcript with an agent — we check.

### Structure (10 minutes)

- [ ] **0:00–2:00 · Artifact 1 — your AI toolkit.** Open your repo and show your tools. For each: what it does and when it's used. Skills/commands ("handles X, I invoke it when…"), rules ("runs passively whenever the agent touches [area]"), AGENTS.md (open it, point out 2–3 things and why the agent needs them).
- [ ] **2:00–4:00 · Artifact 2 — agents.** Show your agent/sub-agent setup: read the title line, show the chain if it calls others, show one example running (screenshot, formatted chat log, or quick live demo).
- [ ] **4:00–6:00 · Artifact 3 — agentic workflow (the main one).** Show the evidence chain: spec (business problem + what "done" looks like), plan (steps, TDD checkpoints / human approval gates), context package (hot/warm/cold if you have a context map), checks & review (one verification output — what you kept, what you fixed). **Connect back to Artifact 1** — point to where your tools actually showed up.
- [ ] **6:00–7:30 · Artifact 4 — the deliverable (actual code).** Show it running or ready to merge: the PR/diff, tests passing (screenshot is fine), release notes + rollback plan (one sentence each on risk and rollback).
- [ ] **7:30–9:30 · Artifact 5 — AI in your SDLC.** Walk your 5 use cases fast, one sentence each. Call out any case where AI improves something *other* than writing code, or where you use AI to build a deterministic tool you later remove AI from.
- [ ] **9:30–10:00 · One thing you'd do differently.** Optional, but likely a Viva question. If you have a genuine one, say it; otherwise end at 9:30.

### Before you record

- [ ] Repo is open, files load fast — no hunting around during the video
- [ ] You can show the implementation ran (PR, diff, or test output)
- [ ] You know which 1–2 moments in Artifact 3 directly use tools from Artifact 1
- [ ] One practice run out loud — 9:30–10:00 is the sweet spot

### Quick reminders

- **Show the file, don't describe it.** "Here's my skill" while pointing at a bullet list ≠ opening the skill file.
- **The thread matters.** The same story runs through all 5 — we check that what you built in Artifact 1 actually appears in Artifact 3.
