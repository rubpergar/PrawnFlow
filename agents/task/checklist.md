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
- Add one TDD ledger row per planned behavior/subtask; keep details short unless blocked or exceptional.

## Checklist

### 1. Context
- [ ] Read the approved plan.
- [ ] Read referenced source-of-truth docs.
- [ ] Load `agents/skills/test-driven-development/SKILL.md`, or record why it does not apply.
- [ ] Read `agents/docs/testing.md`.
- [ ] Read `agents/docs/DoD.md`.
- [ ] Confirm no open questions block implementation.
- [ ] Check for relevant unexpected worktree changes.

### 2. TDD Ledger

Add one row per behavior/subtask from the approved plan. Follow the TDD skill for the actual methodology; keep rows concise and expand only for failures, blockers, or approved exceptions.

| Behavior/Subtask | RED command/result | GREEN command/result | Refactor | Notes/exception |
|---|---|---|---|---|
| ... | ... | ... | yes/no | ... |

### 3. Scope and Docs
- [ ] All planned TDD cycles are complete or documented as approved exceptions.
- [ ] Changes stayed within approved scope.
- [ ] No unrelated refactors.
- [ ] DB changes done, migration and rollback notes recorded, or not applicable.
- [ ] API contracts updated, or not applicable.
- [ ] UI follows `agents/docs/design.md` and relevant skill, or not applicable.
- [ ] Durable decisions documented, or not applicable.

### 4. Validation
- [ ] Targeted tests:
- [ ] Full test suite:
- [ ] Lint:
- [ ] Typecheck:
- [ ] Build:
- [ ] DoD checked:

### 5. Closeout
- [ ] Plan status updated to `validated`, or remaining validation gap documented.
- [ ] Final response includes changes, validation, and residual risk.
- [ ] Ask user before marking backlog task done.
- [ ] Move task files to `agents/task/archive/` after the user approves marking the task done.

## Resume Notes
...
