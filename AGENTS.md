# AGENTS.md

This repository starts as an agent skeleton and can be prepared for active project work.

## Mode

Current mode: `skeleton`.

This repository is in agent bootstrap mode. Product feature implementation is not allowed.

For skeleton-mode scope, required setup information, validation, and transition to project mode, follow `agents/docs/bootstrap.md`.

Do not modify product source code or unrelated files unless `agents/docs/bootstrap.md` explicitly allows it or the user explicitly requests it.

## Project
Fill this section during bootstrap. Leave fields blank only while they are unknown or not configured yet.
- Product:
- Domain:
- Users:
- Goal:

## Stack
Fill only what applies during bootstrap.
- Runtime/framework:
- Package manager:
- Database:
- Test tools:
- Deployment:
- External services:

## Operating Rules
- Before modifying a source-of-truth document, check the Document Ownership table below to determine if explicit approval is needed.
- Product behavior changes require the SDD workflow below.
- Template/agent-maintenance changes may be done directly when the user explicitly asks.
- Skeleton maintenance is not product implementation and does not require a backlog task, plan, or checklist unless the user asks for that workflow.
- New project initialization in `skeleton` mode requires explicit user approval and must follow `agents/docs/bootstrap.md`.
- Exploratory, advisory, review-only, or planning-only requests do not change code unless the user asks for edits.
- Keep changes scoped to the active task or the explicitly requested maintenance.
- Prefer updating stable source-of-truth docs over duplicating instructions.
- Project source-of-truth docs and approved task plans override skill guidance when they conflict.
- Treat blank fields, placeholder markers, and `not available` commands as missing configuration, not as instructions to improvise.
- Archived bootstrap documents are historical references only and must not be followed unless the user explicitly requests bootstrap maintenance or review.

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
| Bootstrap | `agents/docs/bootstrap.md` | Skeleton-mode setup scope, readiness, and transition to project mode | Mode is `skeleton` or user requests bootstrap maintenance |
| Adoption | `agents/docs/adoption.md` | Existing-repo discovery and adoption flow for projects with pre-existing code | Mode is `skeleton` and the repo has existing code, or user requests adoption |
| Active task | `agents/task/backlog.md` | Queue and current task selection | Planning or implementing product work |
| Task plan | `agents/task/TASK-XXX-plan.md` | Approved scope and behavior contract | Implementing or validating the active task |
| Task checklist | `agents/task/TASK-XXX-checklist.md` | Execution ledger and resume point | Implementing or resuming the active task |
| Plan template | `agents/task/plan.md` | Template for task-specific plans | Creating a new task plan |
| Checklist template | `agents/task/checklist.md` | Template for task-specific checklists | Creating a new task checklist |
| Acceptance | `agents/docs/DoD.md` | Definition of done and closeout gates | Before validation and closeout |
| Testing | `agents/docs/testing.md` | Project-specific test commands, locations, fixtures, and validation rules | Adding/running tests or validating work |
| Decisions | `agents/docs/decisions.md` | Durable product, technical, and workflow decisions recorded as ADRs | Planning product work, a durable decision is needed, or past rationale matters |
| API contracts | `agents/docs/api.md` | Public routes, payloads, errors, compatibility | API routes, clients, payloads, or contracts are affected |
| DB schema | `agents/db/schema.sql` | Current database structure | Persistence, migrations, queries, or schema are affected |
| DB domain | `agents/db/domain.md` | Domain vocabulary, relationships, business rules | Data model or business rules are affected |
| UI design | `agents/docs/design.md` | Reusable UI rules, tokens, components, accessibility | UI, design system, or reusable UX behavior is affected |
| Archive | `agents/task/archive/` | Completed task plans and checklists | Current work depends on historical task context |

## Document Ownership
Use this table before modifying any source-of-truth document to determine if explicit approval is needed.

| Document | Owner | When modified | Requires approval |
|---|---|---|---|
| `AGENTS.md` | User/Team | Operating rules, stack, commands | Yes |
| `agents/docs/bootstrap.md` | Framework | Skeleton maintenance | No (template) |
| `agents/docs/adoption.md` | Framework | Adoption flow maintenance | No (template) |
| `agents/docs/testing.md` | Engineering | New commands, fixtures, validation rules | Only when validation behavior changes |
| `agents/docs/DoD.md` | User/Team | Acceptance criteria | Yes |
| `agents/docs/decisions.md` | User/Team | Durable ADR | Yes |
| `agents/docs/api.md` | Backend/API | Public contract changes | Yes |
| `agents/db/schema.sql` | Data/Backend | Migration or schema change | Yes |
| `agents/db/domain.md` | Data/Product | Domain rules | Yes |
| `agents/docs/design.md` | UI/Product | Reusable visual rules | Yes when design system changes |
| `agents/task/backlog.md` | User/Agent | Task selection and status | No |
| `agents/task/plan.md` | Framework | Plan template | No (template) |
| `agents/task/checklist.md` | Framework | Checklist template | No (template) |
| `agents/skills/*.md` | Framework | Skill maintenance | No (template) |
| `README.md` | User/Team | Product documentation | Yes |

## Skills
Use a skill only when its trigger matches the request. Project stack and source-of-truth docs override skill assumptions.

| Skill | Path | Use when | Avoid when |
|---|---|---|---|
| Test-Driven Development | `agents/skills/test-driven-development/SKILL.md` | Load once before implementation code for features, bug fixes, behavior changes, or behavior-preserving refactors; it is the TDD methodology authority | Docs-only, planning-only, config-only changes with no behavior |
| Interface Design | `agents/skills/interface-design/SKILL.md` | Designing, implementing, improving, or reviewing UI/UX, frontend visuals, responsive behavior, interaction states, forms, navigation, dashboards, components, and accessibility tied to UI | Backend-only work, SEO-only audits, security review, brand identity-only work, image generation, or measured performance optimization |
| SEO Audit | `agents/skills/seo-audit/SKILL.md` | Auditing public pages for crawlability, indexation, metadata, content structure, Core Web Vitals, internal links, schema, or rankings | Private dashboards, backend-only work, UI polish without SEO scope |
| Code Review Excellence | `agents/skills/code-review-excellence/SKILL.md` | Reviewing code changes, PRs, architecture-sensitive diffs, or when explicitly asked for a code review | Implementing code directly, formatting-only checks, or replacing automated lint/tests |
| Security Review | `agents/skills/security-review/SKILL.md` | Reviewing authentication, authorization, data flow, secrets, user input, API security, infrastructure config, or when explicitly asked for a security review | Theoretical hardening without code context, test-only files unless requested, or broad security rewrites outside an approved plan |
| Performance | `agents/skills/performance/SKILL.md` | Auditing or improving page load, Core Web Vitals, bundle/resource loading, runtime jank, images, fonts, caching, or web performance regressions | Premature optimization, backend-only work with no web performance impact, or memoization/refactors without measured bottlenecks |
| Context7 MCP | `agents/skills/context7-mcp/SKILL.md` | Library, framework, SDK, API, CLI, or cloud-service documentation and examples | Business-logic debugging, refactoring, review, or non-library programming concepts |
| Find Skills | `agents/skills/find-skills/SKILL.md` | Discovering or installing agent skills for a capability | Direct implementation when no skill discovery is requested |

Frontend precedence: use only `interface-design` for UI/UX, frontend visuals, responsive behavior, interaction states, forms, navigation, components, accessibility tied to UI, and UI review. Do not load separate UI skills.
Quality precedence: use `security-review` for exploitable security analysis, `performance` for measured web performance work, and `code-review-excellence` for general code review. UI accessibility is handled by `interface-design` unless the project later adds a separate specialist accessibility workflow. Project source-of-truth docs and approved task plans override skill assumptions.

## SDD Workflow
Product implementation starts only when there is exactly one task under `## Current` in `agents/task/backlog.md`.

1. Select task
   - Read `agents/task/backlog.md`.
   - If `## Current` has zero or multiple tasks, ask the user to select or create one.

2. Plan
   - Read relevant accepted ADRs in `agents/docs/decisions.md` before proposing behavior or implementation choices.
   - Create/update `agents/task/TASK-XXX-plan.md` from `agents/task/plan.md`.
   - Resolve behavior, data, security, API, and user-facing UX questions before implementation.
   - If a durable decision may be needed, include an ADR proposal in the plan instead of writing directly to `agents/docs/decisions.md`.
   - Do not implement until the user approves the task-specific plan.

3. Checklist
   - Create/update `agents/task/TASK-XXX-checklist.md` from `agents/task/checklist.md`.
   - Derive checklist items from the approved plan only.

4. Implement with TDD
   - Load `agents/skills/test-driven-development/SKILL.md` once at the start of implementation and follow it for the red/green/refactor process.
   - Read the approved task plan, checklist, `agents/docs/testing.md`, and relevant source-of-truth files.
   - Use `agents/docs/testing.md` only for project-specific commands, locations, fixtures, and validation requirements.
   - Mark checklist items as they are completed.
   - If test-first work is not feasible, stop unless the exception is already documented in the approved plan and checklist.

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
   - Lasting decisions may update `agents/docs/decisions.md` only after explicit user approval.

7. Close out
   - Ask before marking the backlog task done.
   - When the user approves marking a task done, move its task plan/checklist files to `agents/task/archive/` in the same closeout step.
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
Replace skeleton values during project setup. Use `not available` when a command does not exist, with a short fallback note.

| Purpose | Command | Notes |
|---|---|---|
| Install | not configured | Package manager and lockfile policy |
| Dev server | not configured | Port and env requirements |
| Targeted tests | not configured | Example command required |
| Full test suite | not configured | Required services/fixtures |
| Lint | not configured | Required before closeout when available |
| Typecheck | not configured | Required before closeout when available |
| Build | not configured | Required for UI/API changes when available |

## Code Conventions
- Prefer existing patterns and local helpers.
- Keep changes small, intentional, and task-scoped.
- Add comments only for non-obvious logic.
- Move detailed conventions into source-of-truth docs when they become durable project rules.

## Project Structure
Add only primary routes with their purpose.
