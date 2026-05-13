---
description: Adopt the agent into an existing project, configure source-of-truth docs, and transition to project mode
---

Adopta este agente skeleton para un proyecto existente siguiendo `agents/docs/bootstrap.md`.

Contexto opcional: `$ARGUMENTS`

Si se provee `$ARGUMENTS`, úsalo como semilla para pre-llenar respuestas y reducir la cantidad de preguntas al usuario.

## Reglas generales

- No modifiques código fuente del producto, configuraciones ni dependencias durante la adopción.
- Escribe solo a `AGENTS.md`, `agents/` y archivos del agente.
- Clasifica cada hallazgo como `detected` (observado), `inferred` (inferido, necesita confirmación), o `missing` (no encontrado).
- Los campos no confirmados se marcan como `pending confirmation`.
- Las asunciones aprobadas por el usuario se marcan como `user-approved assumption: <descripción>`.
- Si el repositorio está vacío o no tiene código de producto, informa que este comando es para adopción de proyectos existentes y sugiere usar el flujo de new project initialization.

## Flujo

### 1. Auto-detección inicial

Inspecciona el repositorio para determinar si tiene código de producto existente. Busca:
- Manifiestos (`package.json`, `Cargo.toml`, `pyproject.toml`, `go.mod`, etc.)
- Directorios de código fuente (`src/`, `lib/`, `app/`, `packages/`)
- Archivos de configuración del proyecto

Si no hay código de producto, detente e informa al usuario.

### 2. Adoption Phase 1 — Non-invasive Inspection

**2.1 Structure** — Lista directorios raíz. Inspecciona `src/`/`lib/`/`app/`/`packages/` hasta 3 niveles. Detecta indicios de monorepo (workspace config, `packages/`, `apps/`).

**2.2 Stack** — Revisa manifiestos para detectar runtime: `package.json` (JS/TS), `Cargo.toml` (Rust), `pyproject.toml` (Python), `go.mod` (Go), `Gemfile` (Ruby), `composer.json` (PHP), `pom.xml`/`build.gradle` (Java/Kotlin), `.csproj` (.NET). Revisa dependencias en busca de frameworks.

**2.3 Package Manager** — Identifica por lockfile: `package-lock.json` (npm), `yarn.lock` (yarn), `pnpm-lock.yaml` (pnpm), `Cargo.lock` (cargo), `poetry.lock` (poetry), `Gemfile.lock` (bundler), `go.sum` (go), `composer.lock` (composer). Si hay múltiples, pregúntale al usuario.

**2.4 Tests** — Busca config/deps: `jest.config.*`, `vitest.config.*`, `.mocharc.*`, `playwright.config.*`, `cypress.config.*`, `pytest.ini`, `[tool.pytest]`, `rspec`, `cargo test`, `*.test.*`/`*.spec.*`. Identifica el comando de tests existente.

**2.5 CI** — Revisa pipelines (`.github/workflows/*.yml`, `.gitlab-ci.yml`, `Jenkinsfile`, `.circleci/config.yml`, `azure-pipelines.yml`). Extrae comandos de test/lint/build/deploy.

**2.6 Docs** — Lee `README.md`, `CONTRIBUTING.md`, `CHANGELOG.md`, `docs/`, `ARCHITECTURE.md`, ADRs, `API.md` o `api/`/`openapi/`/`swagger/`, configs de agente existentes (`.opencode/`, `.claude/`, `AGENTS.md`).

**2.7 Config** — Revisa `.gitignore`, `.dockerignore`, `Dockerfile`, `docker-compose.yml`, `.env.example` (solo template, nunca `.env`), style config (`.editorconfig`, `.prettierrc`, `tsconfig.json`, etc.), linter config (ESLint, Prettier, Ruff, rustfmt, clippy, golangci-lint, RuboCop, etc.).

### 3. Adoption Phase 2 — Summary

Presenta los hallazgos en tres grupos:

| Categoría | Hallazgos |
|---|---|
| **Detected** (observado) | Stack, PM, test tool, CI, linters |
| **Inferred** (necesita confirmación) | Comandos probables, framework, arquitectura |
| **Missing** (necesita usuario) | Identidad del producto, despliegue, DB, servicios externos |

### 4. Adoption Phase 3 — Confirmation Questions

Haz las siguientes preguntas al usuario, una por una. Usa `$ARGUMENTS` como semilla cuando sea relevante.

**4.1 Producto:**
- Nombre del producto
- Dominio/industria
- Usuarios target
- Objetivo principal

**4.2 Comandos:**
Presenta los detectados/inferidos. Pregunta el comando real para cada propósito. Usa `not available` cuando no exista.

| Propósito | Detectado | Confirmado |
|---|---|---|
| Install | ... | ... |
| Dev server | ... | ... |
| Test (targeted) | ... | ... |
| Test (full suite) | ... | ... |
| Lint | ... | ... |
| Typecheck | ... | ... |
| Build | ... | ... |

**4.3 Stack:**
Confirma: runtime, framework, PM, database, test tools, deployment, external services.

**4.4 Módulos críticos:**
Servicios clave, entry points, áreas sensibles.

**4.5 Restricciones:**
Seguridad (auth, pagos, PII), performance, límites de deploy, estándares de código, flujos de branch/release.

**4.6 Documentos adicionales:**
Pregunta si el proyecto necesita:
- `agents/docs/api.md` (API?)
- `agents/db/schema.sql` + `agents/db/domain.md` (DB/modelo?)
- `agents/docs/design.md` (UI?)
- `agents/docs/decisions.md` (ADR?)

### 5. Adoption Phase 4 — Fill Source-of-Truth Docs

Escribe solo hechos confirmados por el usuario. Nunca escribas inferencias no confirmadas como autoritativas.

**5.1 `AGENTS.md`:**
- Rellena `## Project` (Product, Domain, Users, Goal)
- Rellena `## Stack` (Runtime/framework, Package manager, Database, Test tools, Deployment, External services)
- Rellena `## Commands` con los comandos confirmados
- Rellena `## Project Structure` con rutas principales y su propósito

**5.2 `agents/docs/testing.md`:**
- Comandos de test, ubicaciones, servicios, env vars

**5.3 Documentos adicionales (según 4.6):**
- `agents/docs/api.md`: base URL, rutas, auth, formatos, errores
- `agents/db/schema.sql`: tipo DB, esquema, migraciones, conexión
- `agents/db/domain.md`: vocabulario, entidades, reglas de negocio
- `agents/docs/design.md`: componentes, estilos, a11y, tokens
- `agents/docs/decisions.md`: ADRs existentes

Marca los archivos no usados como `Not applicable`.

### 6. Adoption Phase 5 — Mark Uncertainty

Antes de marcar, distingue entre:

- **confirmed**: el usuario respondió explícitamente (incluye respuestas "not available").
- **assumed**: el usuario aceptó una inferencia tuya ("user-approved assumption: <descripción>").
- **pending**: el usuario no respondió, dijo "no sé", o no pudiste detectarlo y no lo confirmó ("pending confirmation").

Campos confirmed → se escriben tal cual.
Campos assumed → se escriben con nota `user-approved assumption: <descripción>`.
Campos pending → no se escriben como autoritativos. Se marcan con `pending confirmation` en el campo correspondiente.

### 7. Readiness Check

Clasifica los campos en dos categorías:

**Campos críticos** (necesarios para project mode):
- Producto: nombre, dominio, usuarios, goal
- Runtime/framework
- Package manager
- Comando install
- Al menos un comando de test

**Campos diferibles** (importantes pero no bloquean la transición):
- Database, deployment, external services
- Lint, typecheck, build
- Documentos adicionales (api.md, design.md, decisions.md, schema.sql)
- Project structure

Un campo cuenta como "resuelto" si está en estado `confirmed` o `assumed` (incluye `not available`). Un campo en `pending` cuenta como "pendiente".

Evalúa el nivel de completitud entre los campos críticos:

| % Críticos resueltos | Escenario | Acción |
|---|---|---|
| 100% | Todo completo | Readiness pasa limpio. Ofrece transición. |
| ≥50% y <100% | Parcialmente completo | Readiness pasa con observaciones. Ofrece transición, listando qué críticos quedan pendientes y por qué no bloquean (ej. "test command pending — se puede rellenar después"). El usuario decide. |
| <50% | Mayormente incompleto | Readiness NO pasa. Explica por qué los críticos faltantes bloquean project mode. No ofrecer transición. |
| 0% y sin contexto | Nada completado | Solo ocurre si el repo está vacío. La auto-detección inicial ya frenó. Si llegas aquí, informa y sugiere new project flow. |

Para escenarios parcial o mayormente incompleto: Pregunta al usuario si quiere responder ahora los campos pendientes o dejarlos para después.

Presenta un resumen tabular de todo lo configurado, lo que quedó pendiente y el veredicto.

### 8. Transición a Project Mode

Sigue la tabla de readiness:

**Si readiness pasa (completo o parcial):**
Pregunta al usuario: "¿Quieres transicionar a project mode?"

- Si accepta (en completo):
  - En `AGENTS.md`: cambiar `Current mode: \`skeleton\`` a `Current mode: \`project\``
  - En `AGENTS.md`: reemplazar el mensaje de skeleton-mode con el mensaje de project-mode:
    ```md
    Current mode: `project`.

    This repository is an active project. Use the SDD/TDD workflow and the source-of-truth documents under `agents/**`.

    Bootstrap is complete. Archived bootstrap documents are historical references only and must not be followed unless the user explicitly requests bootstrap maintenance or review.
    ```
  - Mover `agents/docs/bootstrap.md` a `agents/task/archive/bootstrap-YYYY-MM-DD.md`
  - Confirmar que el archivo archivado es referencia histórica
  - Confirmar todos los cambios realizados

- Si accepta (en parcial):
  - Misma transición pero añadiendo al mensaje de project-mode una nota: "Pending fields: <lista de campos pendientes>. Resuélvelos en un task plan antes de trabajar en esas áreas."
  - No archivar `bootstrap.md` (el skeleton aún no está 100% cerrado). Dejarlo como referencia para resolver pendientes.

- Si no accepta:
  - Informa que la configuración parcial quedó escrita y que el repo sigue en skeleton mode.
  - El usuario puede retomar la transición más tarde.

**Si readiness NO pasa (mayormente incompleto):**
- No ofrecer transición.
- Explica claramente: "No es posible transicionar a project mode hasta que se resuelvan estos campos críticos: <lista>."
- Sugiere: "Vuelve a ejecutar /bootstrap cuando tengas esa información, o usa /bootstrap <contexto> para pre-llenar respuestas."
