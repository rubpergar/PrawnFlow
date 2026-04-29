# AGENTS.md

## Project summary
Breve descripción del producto, dominio y objetivo.

## Stack
Frameworks, runtime, DB, testing, package manager.

## Source of truth map
| Area | File | Purpose | Read when |
|---|---|---|---|
| Product/task spec | `agent/plan.md` | Current task specification | Before coding |
| Task execution | `agent/task.md` | Implementation checklist | During coding |
| Acceptance | `agent/DoD.md` | Completion rules | Before and after implementation |
| Database schema | `agent/schema.sql` | Current DB structure | When DB/data model is involved |
| UI design | `agent/design.md` | UI conventions and design system | When frontend/UI is involved |
| Backlog/history | `agent/backlog.md` | Past and pending work | When planning or checking context |

## Skills
| Skill | Path | Use when | Avoid when |
|---|---|---|---|
| Frontend Component | `agent/skills/frontend-design/SKILL.md` | Creating or modifying UI components | Backend-only tasks |
| API Endpoint | `agent/skills/api-endpoint/SKILL.md` | Adding/changing API routes, handlers, controllers | Pure UI changes |
| Database Migration | `agent/skills/database-migration/SKILL.md` | Changing schema, queries, models, persistence | No DB impact |
| Bugfix | `agent/skills/bugfix/SKILL.md` | Fixing incorrect behavior | New feature work |
| Refactor | `agent/skills/refactor/SKILL.md` | Internal structure changes without behavior changes | Feature or bugfix work |
| Auth Change | `agent/skills/auth-change/SKILL.md` | Login, sessions, permissions, roles, tokens | Non-security changes |
| Test Writing | `agent/skills/test-writing/SKILL.md` | Adding or modifying tests | Docs-only changes |

## Agent workflow

### Phase 1: Understand
- Read `plan.md`.
- Read only referenced files from the source-of-truth map.
- Do not scan unrelated folders.
- If the plan is incomplete, update `plan.md` before implementation.

### Phase 2: Plan execution
- Create or update `task.md` from `plan.md`.
- Break work into test, DB, implementation, UI, validation and documentation tasks.
- Do not add scope beyond `plan.md`.

### Phase 3: TDD
- Add or update failing tests first when feasible.
- Confirm failure reason.
- Implement the smallest passing change.
- Refactor only after tests pass.

### Phase 4: Validate
- Run relevant tests.
- Run lint/typecheck/build when applicable.
- Check `DoD.md`.

### Phase 5: Document
- Update `schema.sql` if DB changed.
- Update `design.md` if reusable UI rules changed.
- Update `decisions.md` if a lasting technical/product decision was made.
- Update `backlog.md`.

## Boundaries
- Do not modify X without explicit approval.
- Do not change public APIs unless specified in `plan.md`.
- Do not alter DB schema without producing migration SQL.
- Do not refactor unrelated code.
- Do not introduce new dependencies without justification.

## Hard boundaries
The agent must not:
- Change unrelated files.
- Perform broad refactors during feature work.
- Introduce dependencies without documenting why.
- Modify authentication, authorization, payments, migrations, or security-sensitive logic without explicit plan coverage.
- Delete tests unless replacing them with equivalent or better coverage.
- Change public API contracts without updating `api.md`.
- Change DB schema without migration SQL and rollback SQL.
- Invent missing requirements.

## Commands
Install, test, lint, typecheck, build.

## Code conventions
Short rules only. Detailed rules should live elsewhere if large.

## Security
Secrets, env vars, logging, PII, auth boundaries.

## Project structure
- `/src/app`: application routes
- `/src/components`: reusable UI components
- `/src/lib`: shared utilities
- `/src/server`: backend/server logic
- `/tests`: test suites
- `/agent`: agent documentation