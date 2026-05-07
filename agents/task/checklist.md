# Task Checklist Template

Copy to `agents/task/TASK-XXX-checklist.md` after the task plan is approved. Do not implement from this template.

## Source
- Task: TASK-XXX
- Plan: `agents/task/TASK-XXX-plan.md`
- Plan status: approved
- Approval evidence:

## Rules
- Work in order unless blocked.
- Keep items derived from the approved plan.
- Mark completed items during implementation.
- If an item changes, keep a note explaining why.
- Record commands that cannot run, the reason, and residual risk.

## Checklist

### 1. Context
- [ ] Read the approved plan.
- [ ] Read referenced source-of-truth docs.
- [ ] Read `agents/docs/testing.md`.
- [ ] Read `agents/docs/DoD.md`.
- [ ] Confirm no open questions block implementation.
- [ ] Check for relevant unexpected worktree changes.

### 2. Tests First
- [ ] Identify the first behavior to test.
- [ ] Add failing test for:
- [ ] Confirm failure is expected.
- [ ] Add edge-case tests from the plan.
- [ ] Record approved TDD exceptions:

### 3. Implementation
- [ ] Implement the smallest passing change.
- [ ] Re-run targeted tests.
- [ ] Repeat red/green/refactor for remaining behavior.
- [ ] Refactor only while tests stay green.
- [ ] Keep changes within scope.

### 4. Data/API/UI/Docs
- [ ] DB changes done, migration and rollback notes recorded, or not applicable.
- [ ] API contracts updated, or not applicable.
- [ ] UI follows `agents/docs/design.md` and relevant skill, or not applicable.
- [ ] Durable decisions documented, or not applicable.

### 5. Validation
- [ ] Targeted tests:
- [ ] Full test suite:
- [ ] Lint:
- [ ] Typecheck:
- [ ] Build:
- [ ] DoD checked:

### 6. Closeout
- [ ] Plan status updated to `validated`, or remaining validation gap documented.
- [ ] Final response includes changes, validation, and residual risk.
- [ ] Ask user before marking backlog task done.
- [ ] Move task files to `agents/task/archive/` after the user approves marking the task done.

## Resume Notes
...
