# Task Checklist Template

Copy to `agents/task/TASK-XXX-checklist.md` after the task plan is approved. Do not implement from this template.

## Source
- Task: TASK-XXX
- Plan: `agents/task/TASK-XXX-plan.md`

## Rules
- Work in order unless blocked.
- Keep items derived from the approved plan.
- Mark completed items during implementation.

## Checklist

### 1. Context
- [ ] Read the approved plan and referenced source-of-truth docs.
- [ ] Read and apply `agents/skills/test-driven-development/SKILL.md`, or record why it does not apply.
- [ ] Confirm no open questions block implementation.

### 2. TDD Ledger
Track each behavior/subtask from the plan through RED → GREEN → REFACTOR cycles.

- [ ] Behavior/subtask 1:
- [ ] Behavior/subtask 2:
- [ ] ...

### 3. Scope and Docs
- [ ] All TDD cycles complete or documented as approved exceptions.
- [ ] Changes stayed within approved scope. No unrelated refactors.
- [ ] Out-of-scope findings registered in `agents/docs/debt.md`.
- [ ] Sync check: compare implemented code against affected source-of-truth docs from the plan.
      Discrepancies → stop and ask user. Resolve before proceeding.
- [ ] Durable docs updated (`agents/docs/api.md`, `agents/db/schema.sql`, `agents/docs/design.md`, etc.) as needed.

### 4. Validation (→ validated)
- [ ] Targeted tests:
- [ ] Full test suite:
- [ ] Lint:
- [ ] Typecheck:
- [ ] Build:
- [ ] DoD validated criteria checked:

### 5. Closeout (→ closed)
- [ ] Ask user before marking backlog task done.
- [ ] Move task files to `agents/task/archive/` after user approves.

## States Reached
- [ ] Implemented (sections 1-3 complete)
- [ ] Validated (section 4 complete)
- [ ] Closed (section 5 complete + user approval)

## Resume Notes
...
