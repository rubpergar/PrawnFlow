# Definition of Done

A task is done when all applicable items are true.

## Spec
- Task plan matches the implemented behavior.
- Checklist is complete or explains non-applicable items.
- Assumptions, edge cases, scope changes, and TDD exceptions are recorded.

## Tests and Validation
- Relevant tests were added or updated.
- TDD evidence or approved exception is recorded for behavior changes.
- Affected tests pass.
- Lint/typecheck/build pass when available and relevant.
- Any command that could not run is recorded with reason and residual risk.

## Code Quality
- Changes are scoped to the approved plan.
- Existing public interfaces stay compatible unless the plan says otherwise.
- No unrelated refactors.
- No unnecessary dependencies.
- Security-sensitive behavior changed only with explicit plan coverage.

## Documentation
Update only when the durable contract changes:
- `agents/docs/api.md` for public API behavior.
- `agents/db/schema.sql` and migration/rollback notes for DB schema.
- `agents/db/domain.md` for domain rules.
- `agents/docs/design.md` for reusable UI rules.
- `agents/docs/testing.md` for validation rules or commands.
- `agents/docs/decisions.md` for user-approved lasting ADRs only.
- Durable decisions identified during the task were either approved and recorded as ADRs, or deliberately left in the task plan/checklist because the user declined or they were task-local.

## Context Hygiene
- Remove temporary files, debug logs, scratch scripts, generated outputs, and local test artifacts created during the task unless they are intentionally promoted to project files.
- Do not delete files created or modified by the user.
- If an artifact may be useful later, ask whether to keep, document, or remove it.
- Before closeout or commit, ensure `git status` contains only intentional changes.

## Closeout
- User approved backlog completion.
- Task plan/checklist were moved to `agents/task/archive/` in the same closeout step.
