# Bootstrap

This document is the source of truth for `skeleton` mode. It defines how to prepare this agent skeleton for a real project before switching to `project` mode.

## Purpose

Use bootstrap mode to configure the agent with enough verified project context to work without avoidable uncertainty. Bootstrap is not product feature implementation.

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

## Skeleton Work Types

Skeleton mode supports three kinds of work. Keep them separate so the agent does not confuse setup with product delivery.

Agent bootstrap:
- Configure `AGENTS.md` and files under `agents/**`.
- Add or update agent skills, routing, lockfiles, templates, and workflow documentation.
- Record project facts, commands, testing rules, decisions, domain notes, API contracts, DB documentation, and design rules.

Existing project discovery:
- Read the existing repository to identify stack, commands, architecture, domain concepts, and validation rules.
- Update agent documentation with verified facts.
- Mark uncertain conclusions as assumptions and ask the user before treating them as authoritative.
- Do not modify product source code during discovery unless the user explicitly requests it.

New project initialization:
- Help the user choose and instantiate the technical base for a project starting from zero.
- Requires explicit user approval and a short initialization plan before touching files outside `agents/**`.
- May create infrastructure, configuration, dependencies, and scaffold files needed for the approved stack.
- Must not implement product features or domain behavior beyond minimal placeholders required by the scaffold.

## New Project Initialization

For projects starting from zero, skeleton mode may include stack selection and technical initialization. This work is allowed only after explicit user approval and a short initialization plan.

The initialization plan should specify:
- Product shape and target platform, such as web app, API, CLI, mobile app, desktop app, or library
- Recommended stack and main alternatives considered
- Package manager and runtime requirements
- Test, lint, typecheck, build, and dev-server setup
- Files and directories expected to be created or changed outside `agents/**`
- External services, databases, deployment targets, or secrets required now or deferred
- Validation commands to run after initialization

Allowed after approval:
- Choose framework, runtime, package manager, and supporting tools
- Initialize a project scaffold
- Add approved dependencies and lockfiles
- Configure tests, lint, typecheck, build, formatting, and dev scripts
- Create minimal technical structure and placeholder files required by the scaffold
- Update agent source-of-truth docs with the resulting stack, commands, and decisions

Not allowed during initialization unless explicitly planned and approved:
- Implement product features
- Implement domain workflows or user-facing behavior beyond scaffold placeholders
- Add authentication, authorization, payments, production data handling, or other security-sensitive flows
- Create irreversible infrastructure or deployment changes
- Add database migrations with product schema unless the user explicitly approves the schema and rollback notes
- Make durable architecture decisions without recording them in `agents/docs/decisions.md`

After initialization, update `AGENTS.md`, `agents/docs/testing.md`, `agents/docs/DoD.md`, and any applicable source-of-truth files before running the readiness check.

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
2. Determine whether the project is new, existing, or agent-maintenance only.
3. Ask the user for missing facts or record clearly approved assumptions.
4. For a new project that needs stack setup, propose an initialization plan and wait for approval before touching files outside `agents/**`.
5. Update only files allowed by the active skeleton work type.
6. Validate that required project context is complete enough for product work.
7. Present a concise readiness summary to the user.
8. Ask for explicit approval before switching to `project` mode.

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
