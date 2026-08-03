# Artifact 2 — Custom Subagent AND MCP Integration

> Purpose: prove at least one custom subagent AND at least one MCP integration, each solving a REAL workflow problem (not a demo for demo's sake). Each must have clear scope, explicit safety boundaries, and working evidence someone else could reuse.

---

## Inventory

> Quick map of what you built — at least one row for a subagent and one for an MCP integration.

| Deliverable | Type | Location | Location Example | Solves | Used when |
|-------------|------|----------|----------|--------|-----------|
| {name} | Subagent | {path} | `./agents/{name}.md` | {problem} | {trigger} |
| {name} | MCP integration | {path} | `./mcp/mcp.json` | {problem} | {trigger} |

---

## Subagent

- **Name:** {subagent name}
- **Problem:** {the real workflow pain this attacks, who hits it / how often}
- **Why a subagent fits:** {why a subagent is the right shape here}
- **Running mode**: {Do we need it locally or as a cloud agent in CI}
- **Chain (if it calls other agents):** {parent → child flow, or "standalone"}
- **Configuration setup reasoning:**
  - Allowed tools
  - Forbidden actions
  - Read/write boundary
  - Human approval gates
  - Security / data notes

### Evidence

| Item | Path |
|------|-------------|
| Config file | `./agents/{name}.md` |
| Chat log / transcript | `./agents/{name}.transcript.md` |
| Refusal log (demo named forbidden action + what it does instead)​ | `./agents/{name}.refusal-log.md` |

---

## MCP integration

- **Name:** {subagent name}
- **Problem:** {the real workflow pain this attacks, who hits it / how often}
- **Why MCP fits:** {why an external tool/service integration is the right shape here}
- **Server / tools exposed:** {which MCP server + which tools you actually use}
- **Auth / connection:** {how it connects — env vars, token, local vs remote}
- **Configuration setup reasoning:**
  - Allowed tools
  - Forbidden actions
  - Read/write boundary
  - Human approval gates
  - Security / data notes

### Evidence

| Item | Link / path |
|------|-------------|
| Config file | `./mcp/mcp.json` |
| Chat log / transcript | `./mcp/transcript.md` |
| Refusal log (demo named forbidden action + what it does instead)​ | `./mcp/refusal-log.md` |

