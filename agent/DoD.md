# Definition of Done

A task is done only when:

## Specification
- `plan.md` reflects the implemented behavior.
- Assumptions are documented.
- Edge cases are covered or explicitly excluded.

## Tests
- Relevant tests are added or updated.
- Failing test was observed before implementation when feasible.
- All affected tests pass.

## Code quality
- No unrelated refactors.
- No duplicated logic without reason.
- Existing public interfaces remain compatible unless specified.

## Documentation
- `schema.sql` updated if schema changed.
- `design.md` updated if UI rules changed.
- `backlog.md` updated after completion.

## Validation
- Lint passes.
- Typecheck passes.
- Build passes when relevant.