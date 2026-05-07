<p align="center">
  <img width="180" height="180" alt="PrawnFlow" src="https://github.com/user-attachments/assets/343504e5-96bf-4d0d-adb1-a3c732ce0c17" />
</p>

<h1 align="center">PrawnFlow</h1>

<p align="center">
  Spec-driven agent workflow template for structured, test-first software development.
</p>

---

# Agent Project Template

Reusable starter for projects that want an agent to work with spec-driven development (SDD), test-driven development (TDD), scoped source-of-truth docs, and resumable task files.

## Structure

| Path | Purpose |
|---|---|
| `AGENTS.md` | Operating rules, routing, SDD workflow, boundaries, commands |
| `agents/task/` | Backlog, task plan template, checklist template, archive |
| `agents/docs/` | Durable project docs: API, design, testing, DoD, decisions |
| `agents/db/` | Schema and domain notes when persistent data exists |
| `agents/skills/` | Optional procedures for TDD, UI/UX, UI review, and SEO |

## Setup

1. Copy the template into a project.
2. Fill `AGENTS.md`: product, stack, commands, security boundaries, project structure.
3. Fill `agents/docs/testing.md` with real validation commands before product implementation.
4. Mark unused source-of-truth docs as `Not applicable` instead of leaving misleading examples.
5. Add exactly one task under `## Current` in `agents/task/backlog.md` when implementation should begin.
6. Create and approve `agents/task/TASK-XXX-plan.md`.
7. Create `agents/task/TASK-XXX-checklist.md`.
8. Load the TDD skill for implementation, validate against `agents/docs/DoD.md`, then ask before backlog closeout/archive moves.

## Core Rule

Product work requires:
- one current backlog task,
- an approved task-specific plan,
- a task-specific checklist,
- TDD unless the approved plan documents an exception.

Template maintenance may be done directly only when the user explicitly asks to improve the agent model itself.

## Request Routing

| Request | Behavior |
|---|---|
| Feature, bug fix, refactor | Use SDD + TDD |
| Docs-only project change | Update relevant source-of-truth docs; no TDD |
| Template maintenance | Edit template files directly when requested |
| Review/audit | Report findings first; edit only if requested |
| Exploration/planning | Gather context and propose next steps; do not implement unless asked |

## Context Budget

Keep reads narrow:
- Implementation: `AGENTS.md`, backlog current entry, task plan, task checklist, TDD skill, `DoD.md`, `testing.md`, plus affected source-of-truth docs.
- API only: add `agents/docs/api.md`.
- DB only: add `agents/db/*`.
- UI only: add `agents/docs/design.md` and one matching UI skill.
- Archive only: read when history affects the current task.

## Ready Checklist

The template is ready for a real project when:
- `AGENTS.md` has real commands, stack, and security boundaries.
- `agents/docs/testing.md` has targeted and full validation commands.
- Unused docs are marked `Not applicable`.
- The backlog has no more than one current task.
- Plan/checklist templates match the team's expected level of detail.
- Security-sensitive areas and public API/DB/UI ownership are explicit.
