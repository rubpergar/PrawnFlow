# AGENTS.md

Placeholders in this file must be filled in after copying the template into a real project. They provide the minimum project context the agent needs to work correctly. Delete this message after completion.

## Project
Fill this section after copying the template into a real project.
- Product:
- Domain:
- Users:
- Goal:

## Stack
Fill only what applies.
- Runtime/framework:
- Package manager:
- Database:
- Test tools:
- Deployment:
- External services:

## Operating Rules
- Product behavior changes require the SDD workflow below.
- Template/agent-maintenance changes may be done directly when the user explicitly asks.
- Exploratory, advisory, review-only, or planning-only requests do not change code unless the user asks for edits.
- Keep changes scoped to the active task or the explicitly requested maintenance.
- Prefer updating stable source-of-truth docs over duplicating instructions.

## Token Budget
- Communicate with the user in Spanish unless they request another language.
- Keep progress updates brief and only send them for meaningful discoveries, blockers, edits, or validation results.
- Avoid restating context already present in the conversation.
- Prefer concise final responses: outcome, changed files, validation, and relevant caveats.
- Do not use intentionally degraded or overly terse language if it reduces correctness or clarity.

## Source of Truth Map
Read the smallest useful set. Use this table to decide what to open, not as a mandatory read list.

| Area | File | Purpose | Read when |
|---|---|---|---|
| Active task | `agents/task/backlog.md` | Queue and current task selection | Planning or implementing product work |
| Task plan | `agents/task/TASK-XXX-plan.md` | Approved scope and behavior contract | Implementing or validating the active task |
| Task checklist | `agents/task/TASK-XXX-checklist.md` | Execution ledger and resume point | Implementing or resuming the active task |
| Plan template | `agents/task/plan.md` | Template for task-specific plans | Creating a new task plan |
| Checklist template | `agents/task/checklist.md` | Template for task-specific checklists | Creating a new task checklist |
| Acceptance | `agents/docs/DoD.md` | Definition of done and closeout gates | Before validation and closeout |
| Testing | `agents/docs/testing.md` | Test commands, locations, fixtures, validation rules | Adding/running tests or validating work |
| Decisions | `agents/docs/decisions.md` | Durable product, technical, and workflow decisions | A decision is needed or past rationale matters |
| API contracts | `agents/docs/api.md` | Public routes, payloads, errors, compatibility | API routes, clients, payloads, or contracts are affected |
| DB schema | `agents/db/schema.sql` | Current database structure | Persistence, migrations, queries, or schema are affected |
| DB domain | `agents/db/domain.md` | Domain vocabulary, relationships, business rules | Data model or business rules are affected |
| UI design | `agents/docs/design.md` | Reusable UI rules, tokens, components, accessibility | UI, design system, or reusable UX behavior is affected |
| Archive | `agents/task/archive/` | Completed task plans and checklists | Current work depends on historical task context |

## Skills
Use a skill only when its trigger matches the request. Project stack and source-of-truth docs override skill assumptions.

| Skill | Path | Use when | Avoid when |
|---|---|---|---|
| Test-Driven Development | `agents/skills/test-driven-development/SKILL.md` | Implementing features, bug fixes, behavior changes, or behavior-preserving refactors | Docs-only, planning-only, config-only changes with no behavior |
| UI/UX Pro Max | `agents/skills/ui-ux-pro-max/SKILL.md` | Designing or improving flows, navigation, forms, dashboards, responsive behavior, accessibility, or product UX | Backend-only work, small isolated logic changes, SEO-only audits |
| Frontend Design | `agents/skills/frontend-design/SKILL.md` | Creating or polishing UI components, pages, layout, typography, spacing, motion, or visual hierarchy | Backend-only, test-only, or purely technical SEO work |
| Web Design Guidelines | `agents/skills/web-design-guidelines/SKILL.md` | Reviewing UI/accessibility/usability before shipping, or when explicitly asked for a UI review | Early ideation, backend-only work, non-UI changes |
| SEO Audit | `agents/skills/seo-audit/SKILL.md` | Auditing public pages for crawlability, indexation, metadata, content structure, Core Web Vitals, internal links, schema, or rankings | Private dashboards, backend-only work, UI polish without SEO scope |
| Code Review Excellence | `agents/skills/code-review-excellence/SKILL.md` | Reviewing code changes, PRs, architecture-sensitive diffs, or when explicitly asked for a code review | Implementing code directly, formatting-only checks, or replacing automated lint/tests |
| Security Review | `agents/skills/security-review/SKILL.md` | Reviewing authentication, authorization, data flow, secrets, user input, API security, infrastructure config, or when explicitly asked for a security review | Theoretical hardening without code context, test-only files unless requested, or broad security rewrites outside an approved plan |
| Performance | `agents/skills/performance/SKILL.md` | Auditing or improving page load, Core Web Vitals, bundle/resource loading, runtime jank, images, fonts, caching, or web performance regressions | Premature optimization, backend-only work with no web performance impact, or memoization/refactors without measured bottlenecks |
| Accessibility | `agents/skills/accessibility/SKILL.md` | Auditing or improving WCAG/accessibility, keyboard behavior, focus, semantic HTML, forms, ARIA, contrast, motion, or UI accessibility regressions | Backend-only work, purely visual polish without accessibility impact, or replacing project design rules |
| Conventional Commit | `agents/skills/conventional-commit/SKILL.md` | Only when the user asks to make a commit | Any request that does not explicitly ask for a commit |

Frontend precedence: `ui-ux-pro-max` for product UX, `frontend-design` for visual implementation, `web-design-guidelines` for review. Do not load every UI skill by default.
Quality precedence: use `security-review` for exploitable security analysis, `performance` for measured web performance work, `accessibility` for WCAG/accessibility concerns, and `code-review-excellence` for general code review. Project source-of-truth docs and approved task plans override skill assumptions.

## SDD Workflow
Product implementation starts only when there is exactly one task under `## Current` in `agents/task/backlog.md`.

1. Select task
   - Read `agents/task/backlog.md`.
   - If `## Current` has zero or multiple tasks, ask the user to select or create one.

2. Plan
   - Create/update `agents/task/TASK-XXX-plan.md` from `agents/task/plan.md`.
   - Resolve behavior, data, security, API, and user-facing UX questions before implementation.
   - Do not implement until the user approves the task-specific plan.

3. Checklist
   - Create/update `agents/task/TASK-XXX-checklist.md` from `agents/task/checklist.md`.
   - Derive checklist items from the approved plan only.

4. Implement with TDD
   - Read the task plan, checklist, `agents/docs/testing.md`, and relevant source-of-truth files.
   - Add or update a failing test first when feasible.
   - Confirm the failure reason, implement the smallest passing change, then refactor while green.
   - Mark checklist items as they are completed.
   - If TDD is not feasible, use only exceptions documented in the approved plan.

5. Validate
   - Run targeted tests, then full validation commands when available.
   - Run lint/typecheck/build when relevant.
   - Report unrelated failures before broadening scope.
   - Check `agents/docs/DoD.md`.

6. Document
   - Update source-of-truth docs only when the durable project contract changes.
   - API changes update `agents/docs/api.md`.
   - DB changes update `agents/db/schema.sql` and rollback/migration notes.
   - Reusable UI rules update `agents/docs/design.md`.
   - Before adding a lasting decision to `agents/docs/decisions.md`, ask the user for approval and include a short summary of the decision that would be recorded.
   - Add the decision to `agents/docs/decisions.md` only after the user approves it.

7. Close out
   - Ask before marking the backlog task done.
   - Ask before moving task files to `agents/task/archive/`.
   - Do not create branches or commits unless the user asks.

## Boundaries
- Do not invent missing requirements.
- Do not change unrelated files.
- Do not perform broad refactors during feature work.
- Do not introduce dependencies without documenting why.
- Do not change public APIs unless the approved plan says so.
- Do not change authentication, authorization, payments, migrations, or other security-sensitive behavior without explicit plan coverage.
- Do not delete tests unless replacing them with equivalent or better coverage.
- Do not change DB schema without migration and rollback notes.
- Never expose secrets, tokens, credentials, private keys, or production-like sensitive data.

## Commands
Replace placeholders during project setup.

| Purpose | Command | Notes |
|---|---|---|
| Install | ... | Package manager and lockfile policy |
| Dev server | ... | Port and env requirements |
| Targeted tests | ... | Example command required |
| Full test suite | ... | Required services/fixtures |
| Lint | ... | Required before closeout when available |
| Typecheck | ... | Required before closeout when available |
| Build | ... | Required for UI/API changes when available |

## Code Conventions
- Prefer existing patterns and local helpers.
- Keep changes small, intentional, and task-scoped.
- Add comments only for non-obvious logic.
- Move detailed conventions into source-of-truth docs when they become durable project rules.

## Project Structure
Add only primary routes with their purpose.
