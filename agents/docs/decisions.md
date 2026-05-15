# Architecture Decision Records

ADR log for durable decisions that should guide future work.

Before planning product work, read relevant accepted ADRs and do not contradict them silently.

Record only decisions with future impact. Keep one-off choices, temporary workarounds, task-local assumptions, and obvious coding details in the task plan/checklist.

Before adding or changing an ADR, ask the user for approval and summarize the title, context, decision, consequences, and future value.

If new work conflicts with an accepted ADR, explain the conflict and ask whether to keep, rewrite, or update it.

## Statuses
- `accepted`: approved by the user and active for future work.
- `rejected`: considered and explicitly declined; keep only when remembering the rejection prevents repeated debate.

## Format

```md
## ADR-000: Short title
Date: YYYY-MM-DD
Status: accepted | rejected
Context: What recurring uncertainty, constraint, or tradeoff forced the decision? What options mattered?
Decision: What rule should future work follow? Be specific enough that another agent can apply it.
Consequences: What benefits, costs, constraints, or follow-up work does this create?
```

## Log
