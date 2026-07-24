# Agent Guide — tududi

Guidance for AI agents working in this repository. Prefer this file plus `docs/` over inventing new patterns.

---

## Project overview

**tududi** is a self-hosted productivity app for organizing life and work without surrendering data to a SaaS vendor. The core idea is a *life management system* — not a flat to-do list — where broad domains (areas), outcomes (goals), initiatives (projects), and actionable items (tasks/subtasks) stay connected so daily work stays aligned with longer-term intent.

Users capture ideas quickly (inbox, quick add, Telegram), then process them into structured work. Day-to-day focus comes from time-based views (Today, Upcoming, Someday); recurring tasks, tags, and notes support ongoing habits and reference material. Project sharing enables small-team collaboration; CalDAV, API keys, OIDC/SSO, and an optional AI assistant / MCP surface let people use tududi inside their existing toolchain while keeping data on their own infrastructure.

**Feature surface:** tasks (subtasks, recurrence), projects, areas, notes, tags, views, goals/habits, inbox capture, Telegram, CalDAV, OIDC/SSO.

Domain hierarchy: **User → Area → Project → Task → Subtask**, with tags and notes linked across entities.

---

## Repository map

```
tududi-agentic/
├── frontend/                 # React app
│   ├── components/           # UI by feature (Task, Project, Area, Inbox, …)
│   ├── entities/             # TypeScript domain types
│   ├── store/                # Zustand
│   ├── hooks/, contexts/, utils/
│   └── __tests__/            # Frontend Jest tests
├── backend/
│   ├── app.js                # Express entry (middleware, sessions, module mount)
│   ├── modules/              # Feature modules (routes, repository, operations, …)
│   │   ├── tasks/            # Largest module — model new features on this pattern
│   │   ├── projects/, areas/, notes/, tags/, inbox/, views/, …
│   │   ├── auth/, oauth/, oidc/, users/, shares/
│   │   ├── caldav/, telegram/, ai-assistant/, mcp/, …
│   ├── models/, migrations/, seeders/
│   ├── middleware/, services/, shared/, utils/
│   └── tests/{unit,integration}/
├── e2e/                      # Playwright
├── public/                   # Static assets + locales (`public/locales/en/…`)
├── docs/                     # Architecture & product behavior
├── scripts/                  # Dev/docker helpers
├── package.json              # Root scripts (monorepo-style)
└── .github/                  # CONTRIBUTING, PR template, workflows
```

When unsure where logic belongs: **routes → repository / operations → models**; UI state in Zustand or SWR; shared types in `frontend/entities/`.

---

## Common commands

```bash
# Setup
npm install
npm run db:init
npm run user:create          # optional

# Day-to-day
npm start                    # frontend + backend
npm run frontend:dev         # :8080
npm run backend:dev          # :3002
npm run kill:all             # free 8080 / 3002

# Quality
npm run lint / lint:fix
npm run format / format:fix
npm test                     # backend Jest
npm run frontend:test
npm run test:ui              # Playwright
npm run test:coverage
npm run pre-push             # lint-staged (use before push)
npm run pre-release          # lint + format + unit + e2e

# Database
npm run db:migrate | db:seed | db:reset | db:status
npm run migration:create -- --name <name>
npm run migration:run | migration:undo | migration:status

# Misc
npm run frontend:build
npm run mcp:dev
```

Env: copy/configure `backend/.env` from `backend/.env.example`. Never commit secrets.

---

## Testing expectations

- **Bug fixes:** include a test that would have failed before the fix (failing test → fix → pass).
- **New features:** include unit and/or integration coverage for the changed paths.
- Pattern: Arrange–Act–Assert.
- Backend tests under `backend/tests/unit/` and `backend/tests/integration/` mirroring modules.
- Frontend: `frontend/__tests__/` or colocated `*.test.tsx`.
- E2E for critical user flows when behavior is user-visible and not covered by API tests alone (`e2e/`).
- Before considering work done: relevant Jest suites green; run `npm run pre-push` (or lint/format/tests equivalent) when preparing a PR.
- Do not weaken or skip tests to make CI pass.

See `docs/testing.md`.

---

## Approval gates

Stop and get explicit human approval (or an existing linked/approved issue) before:

1. **New features** — Feature PRs need prior discussion / an approved GitHub issue (see `.github/CONTRIBUTING.md`). Do not implement large product features without that alignment.
2. **Breaking API or data-model changes** — including irreversible migrations, auth/session behavior, and CalDAV/OIDC contracts.
3. **Security-sensitive work** — authz/authn, secrets handling, file upload rules, rate limits, CORS, or changing how credentials are stored. Never commit `.env` or secrets. Vulnerabilities → private report per `SECURITY.md`, not public issues.
4. **Dependency / infra shifts** — major upgrades, new runtime services, Docker/compose changes that affect production deploy.
5. **Scope expansion** — drive-by refactors, unrelated file edits, or broad “cleanup” outside the assigned task.
6. **Destructive git / ops** — force push, hard reset, dropping DBs, or rewriting published migrations.
7. **User-facing copy / i18n bulk changes** — sync strategy and locale updates after English keys are agreed.

Safe to proceed without a gate when the task is a **bug fix**, **docs**, **tests**, or a **small enhancement** clearly tied to an issue, and changes stay local to the feature with conventions and tests above.

When blocked, ask a short clarifying question rather than guessing product intent.
