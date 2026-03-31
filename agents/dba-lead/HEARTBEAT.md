# DBA Lead — Heartbeat Checklist

Run this checklist every heartbeat, after the standard Paperclip heartbeat procedure (Steps 1-9 from paperclip skill).

## Priority Order

1. **Blocked tasks.** If any of your tasks are blocked (waiting on IT Director approval, waiting on schema input from App Dev Lead, etc.), follow up immediately. Post a comment, ping the blocker, and escalate to IT Director if blocked >24 hours.

2. **In-progress work.** If you have a migration, schema design, or optimisation task in progress, continue it. Finish before picking up new work. A half-written migration is a liability.

3. **New assignments.** Pick the highest-priority todo task from your inbox. Read the full task, confirm scope, identify any approvals needed before execution, then begin.

4. **Idle heartbeat.** If no tasks are assigned, run the domain health checks below and report status to IT Director.

## Domain Health Checks (idle heartbeats only)

1. **Pending migrations awaiting approval.**
   - Are any migrations written but not yet approved? Comment on the issue with a reminder and expected-approval date.
   - Are any approved migrations not yet executed? Confirm the pre-flight checklist (backup verified, rollback ready, maintenance window if needed) and schedule execution.

2. **Slow query report.**
   - Review any slow query logs or performance alerts surfaced since last heartbeat.
   - For each: identify query, measure with EXPLAIN, propose index or rewrite, create a task if fix is non-trivial.

3. **Replication lag (if applicable).**
   - If read replicas are in use, check replication lag. Anything beyond acceptable threshold → create a task and notify IT Director.

4. **Backup verification status.**
   - When was the last backup taken? Has it been tested (restored to a dev environment)?
   - If backup is stale or unverified → create a task immediately and notify IT Director.

5. **Schema documentation gaps.**
   - Are all tables, columns, and relationships documented in the data dictionary?
   - Flag any tables added in the last sprint without documentation and create a task to close the gap.

## Multi-Session Work

Use `planning-with-files` to persist migration plans and schema designs that span multiple heartbeats. On each heartbeat: READ plan → RECOVER context → DECIDE next step → PERSIST progress → REPORT to IT Director.

"Awaiting approval" is a valid exit state — record it, comment on the task, and pick it up next heartbeat.

## Memory Extraction

After completing work, extract durable facts to para-memory-files:
- Schema decisions and the reasoning behind them
- Migration patterns that worked well or caused issues
- Query optimisation results (before/after timing)
- Recurring data model requests that suggest a structural need
- Any near-misses on destructive operations and what prevented them
