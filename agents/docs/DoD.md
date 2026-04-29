# Definition of Done

A task is done when all applicable items are true.

## Spec
- Task plan matches the implemented behavior.
- Checklist is complete or explains non-applicable items.
- Assumptions, edge cases, scope changes, and TDD exceptions are recorded.

## Tests and Validation
- Relevant tests were added or updated.
- The first relevant failing test was observed when feasible.
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
- `agents/docs/decisions.md` for lasting decisions.

## Closeout
- User approved backlog completion.
- User approved archiving task plan/checklist.
