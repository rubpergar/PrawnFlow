# Testing Guide

Customize before product implementation. If a command is unavailable, write `not available` and explain the fallback.

## Commands
| Purpose | Command |
|---|---|
| Targeted unit | |
| Full unit | |
| Integration | |
| E2E | |
| Lint | |
| Typecheck | |
| Build | |
| Full validation | |

## Environment
- Required services:
- Required environment variables:
- Test database/fixtures:
- Reset/cleanup:

## Test Locations
- Unit:
- Integration:
- E2E:
- Fixtures/utilities:

## TDD Rules
- Write the smallest failing test before production code when feasible.
- Confirm the failure is for the expected missing behavior.
- Implement the smallest passing change.
- Refactor only while tests stay green.
- Document approved exceptions in the task plan and checklist.

## Test Quality
- Prefer deterministic fixtures.
- Avoid shared mutable state and order-dependent tests.
- Keep sensitive or production-like data out of fixtures.
- Mock external services at boundaries; prefer real code for domain logic.
- Do not assert only on mock calls when user-visible behavior can be asserted.

## Failure Handling
- Fix unexpected targeted-test failures before continuing.
- Report unrelated failures before broadening scope.
- Record skipped commands, reasons, and residual risk.
