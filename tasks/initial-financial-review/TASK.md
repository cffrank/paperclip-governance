---
kind: task
slug: initial-financial-review
name: Initial Financial Review
description: >
  Run the first financial analysis and budget review. Establishes baseline
  cost data and validates that financial monitoring is working.
assignee: cfo
priority: high
status: todo
---

# Initial Financial Review

Use the `financial-analysis` skill to pull current cost data and establish baselines.

## What You Need

1. Governance context must exist (depends on setup-governance-context task)
2. Read governance context for budget thresholds
3. Pull cost summary, per-agent costs, per-project costs
4. Document initial findings as an issue document

## Done When

- First financial analysis document exists with current spend data
- Baseline metrics established for future comparison
- Any immediate anomalies flagged and communicated to Chief of Staff
