# Testing Guide

Customize before product implementation. If a command is unavailable, write `not available` and explain the fallback.

This file defines project-specific testing logistics. Use `agents/skills/test-driven-development/SKILL.md` as the authority for the TDD workflow itself.

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

## TDD Coordination
- Load the TDD skill once before implementation code when the task changes behavior or refactors behavior-preserving code.
- Use the commands and locations in this guide while following the skill's red/green/refactor cycle.
- Record any approved TDD exception in the task plan and checklist before implementing under that exception.

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
