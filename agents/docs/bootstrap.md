# Bootstrap

This document is the source of truth for `skeleton` mode. It defines how to prepare this agent skeleton for a real project before switching to `project` mode.

## Purpose

Use bootstrap mode to configure the agent with enough verified project context to work without avoidable uncertainty. Bootstrap is not product implementation.

## Allowed Scope

In `skeleton` mode, changes are limited to agent and workflow setup unless the user explicitly expands the scope.

Allowed by default:
- `AGENTS.md`
- `agents/**`
- Documentation required to configure the agent workflow
- Task, plan, checklist, and source-of-truth templates

Not allowed by default:
- Product source code
- Application configuration
- Dependencies or lockfiles
- Database migrations or schema changes outside `agents/db/**` documentation
- Tests for product behavior
- Runtime, build, deployment, or infrastructure files

Only modify files outside the allowed scope when the user explicitly requests that change.

## Information To Collect

Before switching to `project` mode, fill the stable project context that applies:
- Product, domain, users, and goal in `AGENTS.md`
- Runtime/framework, package manager, database, test tools, deployment, and external services in `AGENTS.md`
- Real commands in the `Commands` section of `AGENTS.md`, using `not available` only when a command truly does not exist
- Testing rules in `agents/docs/testing.md`
- Definition of done in `agents/docs/DoD.md`
- Durable technical/product decisions in `agents/docs/decisions.md`
- API, database, domain, and design source-of-truth files when those areas apply

Do not infer missing facts from package files, filenames, or common conventions unless the user approves the inference. Treat blank fields, placeholders, and `not available` commands as missing configuration.

## Bootstrap Workflow

1. Identify missing project context from `AGENTS.md` and relevant files under `agents/**`.
2. Ask the user for missing facts or record clearly approved assumptions.
3. Update only the allowed setup files.
4. Validate that required project context is complete enough for product work.
5. Present a concise readiness summary to the user.
6. Ask for explicit approval before switching to `project` mode.

## Readiness Criteria

The repository is ready for `project` mode when:
- The user has confirmed the product identity, domain, users, and goal.
- The applicable stack fields are filled or intentionally marked unavailable.
- Install, test, lint, typecheck, build, and dev commands are configured or intentionally marked unavailable.
- Testing and definition-of-done documents are usable for validation.
- Known durable decisions are recorded or intentionally deferred.
- The user explicitly approves the transition.

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
