# Adoption: Existing Repository Discovery

## Purpose
Non-invasive discovery of existing repos before product changes. Reads, summarizes, confirms, then writes to agent source-of-truth docs.

## When
Mode is `skeleton`, repo has existing code/tests/docs, and user requests adoption.

## Prerequisites
Read access. `AGENTS.md` exists with `mode: skeleton`. User requested adoption or bootstrap.

## Rule
**Do not modify product code, config, dependencies, or non-agent files during adoption unless the user explicitly requests it.** Write only to `agents/` and `AGENTS.md`.

## Phase 1: Non-invasive Inspection

Tag each finding as `detected` (observed), `inferred` (guess, needs confirm), or `missing` (not found).

**1.1 Structure** — List top-level dirs. Drill into `src/`/`lib/`/`app/`/`packages/` up to 3 levels. Note monorepo indicators (workspace config, `packages/`, `apps/`).

**1.2 Stack** — Check manifests for runtime: `package.json` (JS/TS), `Cargo.toml` (Rust), `pyproject.toml` (Python), `go.mod` (Go), `Gemfile` (Ruby), `composer.json` (PHP), `pom.xml`/`build.gradle` (Java/Kotlin), `.csproj` (.NET). Check dependencies for framework names.

**1.3 Package Manager** — Identify by lockfile: `package-lock.json` (npm), `yarn.lock` (yarn), `pnpm-lock.yaml` (pnpm), `Cargo.lock` (cargo), `poetry.lock` (poetry), `Gemfile.lock` (bundler), `go.sum` (go), `composer.lock` (composer). If multiple, ask user to confirm.

**1.4 Tests** — Search config/deps: `jest.config.*`, `vitest.config.*`, `.mocharc.*`, `playwright.config.*`, `cypress.config.*`, `pytest.ini`, `[tool.pytest]`, `rspec`, `cargo test`, `*.test.*`/`*.spec.*`. Note the test command.

**1.5 CI** — Check pipeline files (`.github/workflows/*.yml`, `.gitlab-ci.yml`, `Jenkinsfile`, `.circleci/config.yml`, `azure-pipelines.yml`). Extract test/lint/build/deploy commands.

**1.6 Docs** — Read `README.md`, `CONTRIBUTING.md`, `CHANGELOG.md`, `docs/`, `ARCHITECTURE.md`, ADRs, `API.md` or `api/`/`openapi/`/`swagger/`, existing agent config (`.opencode/`, `.claude/`, `AGENTS.md`).

**1.7 Config** — Review `.gitignore`, `.dockerignore`, `Dockerfile`, `docker-compose.yml`, `.env.example` (template only, never `.env`), style config (`.editorconfig`, `.prettierrc`, `tsconfig.json`, etc.), linter config (ESLint, Prettier, Ruff, rustfmt, clippy, golangci-lint, RuboCop, etc.).

## Phase 2: Summary

Show findings in three groups:

- **Detected** (observed): stack, PM, test tool, CI, linters.
- **Inferred** (needs confirm): likely commands, framework, architecture.
- **Missing** (needs user): product identity, deployment, database, external services.

## Phase 3: Confirmation Questions

**3.1 Product** — name, domain, users, goal.

**3.2 Commands** — Present detected/inferred, ask for real command:

| Purpose | Detected | Confirmed |
|---|---|---|
| Install | ... | ... |
| Dev server | ... | ... |
| Test (targeted) | ... | ... |
| Test (full suite) | ... | ... |
| Lint | ... | ... |
| Typecheck | ... | ... |
| Build | ... | ... |

Use `not available` when a command does not exist.

**3.3 Stack** — Confirm: runtime, framework, PM, database, test tools, deployment, external services.

**3.4 Critical modules** — Key services, entry points, sensitive areas.

**3.5 Constraints** — Security (auth, payments, PII), performance, deployment limits, coding standards, branch/release workflows.

**3.6 Additional docs** — Ask if the project needs: `api.md` (API?), `db/schema.sql` + `db/domain.md` (DB/model?), `design.md` (UI?), `decisions.md` (ADRs?).

## Phase 4: Fill Source-of-Truth Docs

Write only user-confirmed facts. Never write inferred/unconfirmed as authoritative.

**4.1 AGENTS.md** — Fill `## Project`, `## Stack`, `## Commands`, `## Project Structure`, `## Source of Truth Map` with confirmed values.

**4.2 testing.md** — Fill commands, test locations, services, env vars.

**4.3 Additional docs** (per 3.6):
- `api.md`: base URL, routes, auth, formats, errors
- `db/schema.sql`: DB type, schema, migrations, connection (no secrets)
- `db/domain.md`: vocabulary, entities, business rules, workflows
- `design.md`: components, styling, a11y, tokens
- `decisions.md`: existing ADRs (user-approved)

Mark unused files as `Not applicable`.

## Phase 5: Mark Uncertainty

- Unconfirmed `AGENTS.md` fields → `pending confirmation`
- User-approved assumptions → `user-approved assumption: <description>`

Do not treat `pending confirmation` as authoritative. Resolve in task plans when needed.

## Phase 6: First Task (Optional)

Ask: "Do you want a first backlog task? If yes, describe what to work on."

If yes, create backlog entry, plan, and checklist via SDD. If no, adoption is complete.

## Completion

Adoption ends after Phases 1–5 and no product code modified. Run readiness check in `agents/docs/bootstrap.md` before transitioning to `project` mode.
