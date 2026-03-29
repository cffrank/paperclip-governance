---
name: operational-health
description: >
  Monitor agent performance, task velocity, and system health using Paperclip
  dashboard and activity APIs. Use when checking company operational status,
  detecting stale work, identifying agent issues, or producing operational
  sections for board reports.
---

# Operational Health

See what's working, what's stuck, and what's about to break.

## Before Starting

Read company-governance-context for:
- Stale task threshold (default: 48 hours)
- Blocked task escalation threshold (default: 48 hours)
- Agent health expectations
- Entity/project scorecards and targets

## Monitoring Procedure

### 1. Dashboard Check

```
GET /api/companies/{companyId}/dashboard
```

Extract:
- Total agents and status breakdown (active / running / paused / error / idle)
- Total tasks and status breakdown (todo / in_progress / done / blocked)
- Stale task count
- Recent activity summary

### 2. Agent Health

```
GET /api/companies/{companyId}/agents
```

For each agent:
- Status: running → healthy. Error/paused → flag.
- Last heartbeat: recent → active. Stale → investigate.
- Budget utilization: check spend vs. allocation.

### 3. Task Velocity

Compare over the monitoring period:
- Tasks completed vs. tasks created (velocity ratio)
- Velocity ratio <0.8 → backlog growing, flag capacity concern
- Average time in_progress → compare against stale threshold
- Tasks blocked and for how long

### 4. Stale Work Detection

```
GET /api/companies/{companyId}/issues?status=in_progress
```

Flag any task where:
- In_progress duration exceeds stale threshold from governance context
- No comment update in >24 hours
- Assigned agent is in error or paused state

### 5. Activity Anomalies

```
GET /api/companies/{companyId}/activity
```

Scan for unusual patterns:
- Mass status changes (potential automation issue)
- Repeated failed checkouts (contention)
- Budget exhaustion events
- Approval backlogs

### 6. Record Findings

Post health status as issue comment. For periodic reports, write as issue document.

Use traffic light indicators: healthy / warning / critical for each check area.

For detailed metrics frameworks by entity type, read `references/health-metrics.md`.

## Related Skills

- company-governance-context provides health thresholds
- compliance-review checks policy adherence (different focus than health)
- risk-assessment uses health findings as risk indicators
- decision-protocol records operational findings
- governance-reporting consumes health data for board reports
