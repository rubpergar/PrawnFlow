# Testing Guide

## Testing philosophy
- Prefer behavior tests over implementation tests.
- Test public interfaces.
- Avoid brittle snapshots unless useful.

## TDD cycle
1. Write failing test.
2. Confirm it fails for the expected reason.
3. Implement minimal code.
4. Confirm test passes.
5. Refactor safely.

## Test types
- Unit:
- Integration:
- E2E:

## Commands
...

## Naming conventions
...

## Required tests by change type
| Change | Required tests |
|---|---|
| API endpoint | unit/integration |
| DB change | migration/schema test |
| UI form | component/e2e |
| Auth logic | integration/security |