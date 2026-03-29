---
kind: task
slug: initial-health-check
name: Initial Operational Health Check
description: >
  Run the first operational health scan and compliance review. Establishes
  baseline operational metrics and validates monitoring is working.
assignee: coo
priority: high
status: todo
---

# Initial Operational Health Check

Use the `operational-health` skill to scan dashboard and activity log. Run initial compliance review.

## What You Need

1. Governance context must exist (depends on setup-governance-context task)
2. Read governance context for health thresholds
3. Pull dashboard data, agent statuses, task counts
4. Scan activity log for anomalies
5. Document initial findings as an issue document

## Done When

- First operational health report exists with current metrics
- Baseline metrics established for future comparison
- Initial compliance review completed (even if no findings)
- Risk register project created (even if empty)
- Any immediate issues flagged and communicated to Chief of Staff
