# Artifacts for cursor AI bootcamp


## Artifact 1:

### Required  evidence

- .cursor/rules file.
- AGENTS.md or equivalent project guidance.
- At least one SKILL.md.
- Optional slash command.

### Evaluation

- Cursor rules quality: short, scoped, actionable, non-conflicting
- AGENTS.md / project guidance: project map, conventions, repo operation
- SKILL.md workflow: repeatable steps, inputs, outputs and when to use
- Reusability and maintainability
- Evidence hygiene: links, locations and structure

## Artifact 2

### Required  evidence

- One custom subagent or MCP integration.
- Designed for a real workflow problem.
- Includes explicit responsibility, boundaries and working evidence.

Likely locations:

- .cursor/agents/
- .cursor/mcp.json
- /evidence/agent-or-mcp.md
- Example output or demo note

Content:

- Purpose and use case.
- Clear responsibility and scope.
- Allowed tools.
- Forbidden actions.
- Read/write boundary.
- Human approval gates.
- Security/data notes.
- Working evidence (chat logs)
- safe demo output.

### Evaluation

- Usefulness: solves a real workflow problem, not demo complexity
- Clear responsibility and scope
- Working evidence: config, command, output, demo or safe execution proof
- Safety boundaries: allowed tools, forbidden actions, read/write limits
- Approval and security design
- Documentation and reusability

## Artifact 3

### Required  evidence

- Original work item / story
- AI-ready spec
- Plan Mode output
- Context map
- Human plan review notes
- Explanation of human decisions
- PR link
- Tests/checks evidence
- Verification step output
- Chat logs



### Evaluation

- Traceability: story → spec → plan
- Spec quality
- Plan quality
- Context map quality
- Verification evidence quality
- Review summary and final decision


## Artifact 4

### Required  evidence

- At least 5 Prioritized AI-assisted engineering use cases.
- Impact rating.
- Risk rating.
- Effort rating.
- Recommended AI workflow pattern.
- Required context.
- Verification approach.
- Value stream map.

Good ue case shape:

• Specific team workflow: not “use AI for tests.”
• Clear before/after process step.
• Risk and verification described up front.
• Small enough to be tried by a real team.

### Evaluation

Use case quality: real, specific, relevant
Impact / risk / effort scoring
Workflow pattern selection
Value stream map / process integration
Actionability and prioritized next steps

## Artifact 5

### Required  evidence

- PR link, demo link, deployment note or deployability note.
- Implementation diff.
- Tests/checks evidence.
- Review notes.
- Release notes including Rollback plan if needed
- Known risks / limitations.
- Final merge or deployability decision.

### Evaluation

- Working result: PR/demo/deployable output exists and matches spec
- Verification evidence: tests/checks/manual QA prove key behavior
- Review readiness: summary, blockers, missing evidence, final decision
- Release readiness: notes, observability/flag decision, rollout thinking
- Rollback/risk control
- Scope discipline and maintainability

