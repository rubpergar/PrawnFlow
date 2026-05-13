# Bootstrap

Source of truth for `skeleton` mode. Defines how to prepare the agent skeleton for a real project before switching to `project` mode.

## Purpose

Configure the agent with enough verified context to work without avoidable uncertainty. Bootstrap is not product implementation.

## Allowed Scope

Limited to agent and workflow setup unless the user explicitly expands scope.

**Allowed:**
- `AGENTS.md`, `agents/**`
- Agent workflow documentation, task/plan/checklist templates

**Not allowed:**
- Product source code, application config, dependencies, lockfiles
- DB migrations outside `agents/db/**`, product tests, runtime/build/deploy files

Only modify files outside allowed scope when the user requests it.

## Skeleton Work Types

Three kinds of work. Keep separate from product delivery.

**Agent bootstrap:**
- Configure `AGENTS.md` and files under `agents/**`.
- Add/update skills, routing, lockfiles, templates, workflow docs.
- Record project facts, commands, testing rules, decisions, domain notes, API contracts, DB docs, design rules.

**Existing project discovery:**
- Follow `agents/docs/adoption.md`.
- Read repo to identify stack, commands, architecture, domain, validation rules.
- Update agent docs with verified facts.
- Mark uncertain conclusions as assumptions; ask before treating as authoritative.
- Do not modify product source code unless the user explicitly requests it.

**New project initialization:**
- Help choose and instantiate the technical base for a zero-start project.
- Requires explicit user approval and a short plan before touching files outside `agents/**`.
- May create infra, config, dependencies, and scaffold files for the approved stack.
- Must not implement product features beyond minimal scaffold placeholders.

## New Project Initialization

For zero-start projects, skeleton mode may include stack selection and technical setup. Requires explicit user approval and a short initialization plan, then executes approved changes.

**Plan specifies:**
- Product shape and target platform (web app, API, CLI, mobile, desktop, library)
- Recommended stack and alternatives considered
- PM, runtime, test/lint/typecheck/build/dev setup
- Files/dirs to create outside `agents/**`
- External services, DB, deployment, secrets (now or deferred)
- Validation commands

**Allowed after approval:**
- Choose framework, runtime, PM, tools. Initialize scaffold, add deps and lockfiles.
- Configure tests, lint, typecheck, build, formatting, dev scripts.
- Create minimal technical structure and placeholders required by the scaffold.
- Update agent source-of-truth docs with resulting stack, commands, decisions.

**Not allowed unless explicitly planned and approved:**
- Product features, domain workflows, or user-facing behavior beyond scaffold placeholders.
- Auth, payments, production data, security-sensitive flows.
- Irreversible infra/deployment changes.
- DB migrations with product schema without explicit user approval of schema and rollback notes.
- Durable architecture decisions without recording in `agents/docs/decisions.md`.

After initialization, update `AGENTS.md`, `agents/docs/testing.md`, `agents/docs/DoD.md`, and applicable source-of-truth files before the readiness check.

## Information To Collect

Before switching to `project` mode, fill applicable fields:
- `AGENTS.md`: product info, stack, commands (use `not available` only when truly absent)
- `agents/docs/testing.md`: test commands, locations, services
- `agents/docs/DoD.md`: definition of done
- `agents/docs/decisions.md`: durable decisions
- `agents/docs/api.md`, `agents/db/schema.sql`, `agents/db/domain.md`, `agents/docs/design.md` when those areas apply
- `AGENTS.md` Document Ownership table: verify owners and approval requirements match the project team structure

Do not infer missing facts without user approval. Treat blanks and `not available` as missing config.

## Bootstrap Workflow

1. Determine project type (new / existing / agent-maintenance) from context.
2. Follow the applicable workflow:
   - **Existing**: `agents/docs/adoption.md`
   - **New**: New Project Initialization section above (propose plan, wait for approval)
   - **Maintenance**: edit directly
3. Ask user for missing facts; record approved assumptions.
4. Update only files allowed by the active skeleton work type.
5. Validate context is complete enough for product work.
6. Present readiness summary; ask for explicit approval before switching to `project` mode.

## Readiness Criteria

The repository is ready for `project` mode when:
- The user has confirmed the product identity, domain, users, and goal.
- The applicable stack fields are filled or intentionally marked unavailable.
- Install, test, lint, typecheck, build, and dev commands are configured or intentionally marked unavailable.
- Testing and definition-of-done documents are usable for validation.
- Known durable decisions are recorded or intentionally deferred.
- For new projects, any approved technical initialization has been validated or documented with known failures.
- The user explicitly approves the transition.

Project mode does not require every future product detail to be known. It requires enough verified context to run SDD/TDD safely. Missing details discovered during future tasks must be resolved in the task plan and documented when they become durable project knowledge.

## Transition To Project Mode

After user approval, perform the transition in one scoped maintenance step:
- Update `AGENTS.md` so `Current mode` is `project`.
- Replace the skeleton-mode message with the project-mode message.
- Remove active references that instruct the agent to follow bootstrap during normal work.
- Move this file from `agents/docs/bootstrap.md` to `agents/task/archive/bootstrap-YYYY-MM-DD.md`.
- Confirm that archived bootstrap documents are historical references only.

Use this project-mode message in `AGENTS.md`:

```md
## Mode

Current mode: `project`.

This repository is an active project. Use the SDD/TDD workflow and the source-of-truth documents under `agents/**`.

Bootstrap is complete. Archived bootstrap documents are historical references only and must not be followed unless the user explicitly requests bootstrap maintenance or review.
```

## Archived Bootstrap Documents

Archived bootstrap documents are historical references only. Do not follow them during project work unless the user explicitly asks to review bootstrap history or perform bootstrap maintenance.
