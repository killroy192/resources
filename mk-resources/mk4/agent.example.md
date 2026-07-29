# Agent Guide

Guidance for AI agents working in this repository. Prefer this file over inventing new patterns.

---

## Project overview

**tududi** is a self-hosted productivity app for organizing life and work without surrendering data to a SaaS vendor. The core idea is a *life management system* — not a flat to-do list — where broad domains (areas), outcomes (goals), initiatives (projects), and actionable items (tasks/subtasks) stay connected so daily work stays aligned with longer-term intent.

Users capture ideas quickly (inbox, quick add, Telegram), then process them into structured work. Day-to-day focus comes from time-based views (Today, Upcoming, Someday); recurring tasks, tags, and notes support ongoing habits and reference material. Project sharing enables small-team collaboration; CalDAV, API keys, OIDC/SSO, and an optional AI assistant / MCP surface let people use tududi inside their existing toolchain while keeping data on their own infrastructure.

**Feature surface:** tasks (subtasks, recurrence), projects, areas, notes, tags, views, goals/habits, inbox capture, Telegram, CalDAV, OIDC/SSO.

Domain hierarchy: **User → Area → Project → Task → Subtask**, with tags and notes linked across entities.

---

## Repository map

Max depth 2 (top-level → immediate children). Deeper layout is discovered in-repo.

```
tududi-agentic/
├── frontend/                 # React app
│   ├── components/           # UI by feature (Task, Project, Area, Inbox, …)
│   ├── entities/             # TypeScript domain types
│   ├── store/                # Zustand
│   ├── hooks/                # React hooks
│   ├── contexts/             # React contexts
│   ├── utils/                # Shared frontend helpers
│   ├── styles/               # Global / shared styles
│   └── __tests__/            # Jest setup only (`setup.ts`)
├── backend/
│   ├── app.js                # Express entry (middleware, sessions, module mount)
│   ├── modules/              # Feature modules (routes, repository, operations, …); model new work on `tasks/`
│   ├── models/               # Sequelize models
│   ├── migrations/           # DB migrations
│   ├── seeders/              # DB seeders
│   ├── middleware/           # Express middleware
│   ├── services/             # Cross-cutting services
│   ├── shared/               # Shared backend utilities
│   ├── utils/                # Backend helpers
│   └── tests/                # Jest unit + integration (`unit/`, `integration/`)
├── e2e/                      # Playwright (`tests/`, `helpers/`)
├── public/                   # Static assets + locales
├── scripts/                  # Dev/docker helpers
├── package.json              # Root scripts (monorepo-style)
└── .github/                  # CONTRIBUTING, PR template, workflows
```

When unsure where logic belongs: **routes → repository / operations → models**; UI state in Zustand or SWR; shared types in `frontend/entities/`.

---

## Common commands

Env: copy/configure `backend/.env` from `backend/.env.example`. Never commit secrets.

```bash
# Setup
npm install

# Day-to-day
npm start                    # frontend + backend
npm run frontend:dev         # :8080
npm run backend:dev          # :3002

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
```

---

## Approval gates

Stop and get explicit human approval (or an existing linked/approved issue) before:

1. **Breaking API or data-model changes** — including irreversible migrations, auth/session behavior, and CalDAV/OIDC contracts.
2. **Security-sensitive work** — authz/authn, secrets handling, file upload rules, rate limits, CORS, or changing how credentials are stored. Never commit `.env` or secrets. Vulnerabilities → private report per `SECURITY.md`, not public issues.
3. **Dependency / infra shifts** — major upgrades, new runtime services, Docker/compose changes that affect production deploy.
4. **Scope expansion** — drive-by refactors, unrelated file edits, or broad “cleanup” outside the assigned task.
5. **Destructive git / ops** — force push, hard reset, dropping DBs, or rewriting published migrations.
6. **User-facing copy / i18n bulk changes** — sync strategy and locale updates after English keys are agreed.

Safe to proceed without a gate when the task is a **bug fix**, **docs**, **tests**, or a **small enhancement** clearly tied to an issue, and changes stay local to the feature with conventions and tests above.

When blocked, ask a short clarifying question rather than guessing product intent.

## Testing expectations

- **Bug fixes:** include a test that would have failed before the fix (failing test → fix → pass).
- **New features:** include unit and/or integration coverage for the changed paths.
- Pattern: Arrange–Act–Assert.
- Backend tests under `backend/tests/unit/` and `backend/tests/integration/` mirroring modules.
- Frontend tests: co-locate next to the code under test — prefer `frontend/**/__tests__/*.{test,spec}.{ts,tsx}` (e.g. `frontend/components/Task/TaskDetails/__tests__/`), or a sibling `*.test.ts(x)` / `*.spec.ts(x)` (e.g. `frontend/utils/dateUtils.test.ts`). `frontend/__tests__/` holds Jest setup only, not feature tests.
- E2E for critical user flows when behavior is user-visible and not covered by API tests alone (`e2e/`).
- Before considering work done: relevant Jest suites green;