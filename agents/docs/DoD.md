# Definition of Done

A task passes through three states. Each state has its own criteria. A task can be `validated` without being `closed`, but cannot be `closed` without being `validated`.

## Implemented

The change is technically ready. Relevant tests exist.

- [ ] Task plan matches the implemented behavior.
- [ ] Checklist is complete or explains non-applicable items.
- [ ] Assumptions, edge cases, scope changes, and TDD exceptions are recorded.
- [ ] Changes are scoped to the approved plan.
- [ ] Existing public interfaces stay compatible unless the plan says otherwise.
- [ ] No unrelated refactors.
- [ ] No unnecessary dependencies.
- [ ] Security-sensitive behavior changed only with explicit plan coverage.

## Validated

Validations passed, or gaps are documented with residual risk.

- [ ] Relevant tests were added or updated.
- [ ] TDD evidence or approved exception is recorded for behavior changes.
- [ ] Affected tests pass.
- [ ] Lint/typecheck/build pass when available and relevant.
- [ ] Any command that could not run is recorded with reason and residual risk.
- [ ] Affected source-of-truth docs updated (see documentation rules below).
- [ ] Temporary files, debug logs, scratch scripts, and test artifacts cleaned or promoted.
- [ ] `git status` contains only intentional changes.

### Documentation rules

Update only when the durable contract changes:
- `agents/docs/api.md` for public API behavior.
- `agents/db/schema.sql` and migration/rollback notes for DB schema.
- `agents/db/domain.md` for domain rules.
- `agents/docs/design.md` for reusable UI rules.
- `agents/docs/testing.md` for validation rules or commands.
- `agents/docs/decisions.md` for user-approved lasting ADRs only.
- Durable decisions identified during the task were either approved and recorded as ADRs, or deliberately left in the task plan/checklist because the user declined or they were task-local.

## Closed

Administratively closed. User approved, task files archived.

- [ ] User approved backlog completion.
- [ ] Task plan/checklist were moved to `agents/task/archive/` in the same closeout step.
