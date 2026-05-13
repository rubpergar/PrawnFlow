# Technical Debt

Registry of bugs, issues, improvements, or incidents the agent finds while working on a task that are outside the current task's scope.

When the agent encounters something relevant but out of scope, it must log it here instead of modifying it without permission. The user periodically reviews the log and decides whether to create a formal task.

## Statuses
- `open`: pending user review.
- `dismissed`: the user decided not to address it.

## Format

```md
## DBT-XXX: Short title
Date: YYYY-MM-DD
Status: open | dismissed
Risk: low | medium | high
Impact: low | medium | high
Suggested priority: low | medium | high | critical
Evidence: Related file(s), line(s), or link.
Description: Explanation of the problem.
Recommendation: What to do to resolve it.
```

## Log
