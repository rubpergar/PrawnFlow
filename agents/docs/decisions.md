# Decisions

Record lasting project or agent-workflow decisions that future tasks should reuse.

## Format

```md
## DEC-000: Short imperative title
Date: YYYY-MM-DD
Status: proposed | accepted | superseded

### Context
What recurring uncertainty or constraint forced the decision?

### Decision
What rule should future work follow?

### Consequences
What tradeoffs or follow-up work does this create?
```

## DEC-001: Use task-specific plan and checklist files
Date: 2026-04-29
Status: accepted

### Context
Backlog entries are intentionally short, but implementation needs stable task artifacts that survive context limits and session handoffs.

### Decision
Use `agents/task/backlog.md` to identify the single current task. For each task, create `agents/task/TASK-XXX-plan.md` from `agents/task/plan.md`, then `agents/task/TASK-XXX-checklist.md` from `agents/task/checklist.md`. Implement from task-specific files, not templates.

### Consequences
The checklist must stay updated during implementation. Backlog completion and archive moves require user approval.


## DEC-002: Ignore terminal-only mojibake in Markdown output
Date: 2026-04-29
Status: accepted

### Context
Some Markdown text appears to Codex through PowerShell output as mojibake, for example `descripciÃ³n`, while the user sees the text correctly in the editor. This appears to be a terminal/output encoding artifact rather than a repository content issue.

### Decision
Do not modify files solely to fix mojibake that only appears in Codex terminal output. Only change encoding or text when the user also sees the problem in the editor, or when a validation tool confirms the file is incorrectly encoded.

### Consequences
Codex should mention terminal-only mojibake as a possible display artifact, then proceed without churn. Encoding fixes require explicit evidence that the repository file itself is wrong.

## DEC-003: Use task-specific plan and checklist files for SDD
Date: 2026-04-29
Status: accepted

### Context
The project workflow is based on spec-driven development. Backlog entries begin as short task references, but implementation should only start after the active task has a detailed plan and a concrete checklist. Sessions may stop midway, so future Codex sessions need stable task artifacts that can be resumed without redefining the task.

### Decision
Use `agents/task/backlog.md` to identify the single active task under `## Current`. For each active task, create `agents/task/TASK-XXX-plan.md` from `agents/task/plan.md`, then create `agents/task/TASK-XXX-checklist.md` from `agents/task/checklist.md`. Implement from the task-specific files, not from the templates. After user-approved completion, move the task-specific files to `agents/task/archive/`.

### Consequences
`agents/task/plan.md` and `agents/task/checklist.md` are templates, not active work files. The agent must keep the task-specific checklist updated during implementation so work can resume from a new session. Backlog closeout and archive moves require user approval.