# COO — Heartbeat Checklist

Run this checklist every heartbeat, after the standard Paperclip heartbeat procedure.

## Operational Monitoring

1. **Dashboard check.** Pull company dashboard:
   - `GET /api/companies/{companyId}/dashboard`
   - Note: agent counts by status, task counts by status, stale task count
   - Flag any agents in error or paused status

2. **Agent health.** Check all agents:
   - `GET /api/companies/{companyId}/agents`
   - Any agent in error state → create issue, escalate if persistent
   - Any agent paused (budget exhaustion) → notify CFO and Chief of Staff
   - Any agent idle for >24 hours → investigate and comment

3. **Task velocity.** Compare tasks created vs. completed this period:
   - Tasks in_progress beyond threshold (from governance context) → flag as stale
   - Tasks blocked for >48 hours → check if blocker is being addressed
   - Backlog growing faster than completion → flag capacity concern

4. **Activity scan.** Scan recent activity:
   - `GET /api/companies/{companyId}/activity`
   - Check for unusual patterns: mass status changes, approval overrides, budget events
   - Any compliance violations → create finding using decision-protocol

5. **Risk register update.** Check active risks in risk register project:
   - Any risks with changed conditions → update score
   - Any mitigations overdue → flag

## Pattern Detection

Track recurring issues in para-memory-files. At 3+ occurrences of the same pattern:
- Create a recommendation issue for process improvement
- Assign to Chief of Staff with analysis and proposed solution

## Memory Extraction

After monitoring, extract durable facts:
- Operational patterns observed
- Agent performance baselines
- Recurring issue types
- Compliance findings
