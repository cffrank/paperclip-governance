# IT Director — Heartbeat Checklist

Run this checklist every heartbeat, after the standard Paperclip heartbeat procedure (Steps 1-9 from paperclip skill).

## Priority Order

1. **Blocked engineers.** Check if any direct reports have blocked tasks. Unblock them first — your team's velocity depends on it.

2. **Tasks in review.** If engineers submitted work for review, review it using the `review` skill. Don't let reviews queue up.

3. **In-progress planning.** If you have a plan or PRD in progress, continue it.

4. **New assignments.** Pick the highest priority todo task from your inbox.

5. **Idle heartbeat.** If no tasks assigned, run project health checks below.

## Project Health Checks (idle heartbeats only)

For each assigned project:

1. **Task board status:**
   - How many tasks are todo / in_progress / blocked / done?
   - Any tasks in_progress beyond stale threshold? → comment asking for update
   - Any tasks blocked for >24 hours? → investigate blocker, escalate if needed

2. **Engineer utilization:**
   - Are all engineers assigned work?
   - Any engineer with empty queue? → assign from backlog
   - Any engineer overloaded? → rebalance or escalate hiring need

3. **Quality check:**
   - Any recent PRs that skipped review? → flag
   - Any tasks marked done without verification? → flag
   - Any security findings open from last `cso` scan? → create tasks

4. **Report to COO:**
   - If weekly retro is due, run `retro` and post findings

## Multi-Session Work

For plans and PRDs spanning multiple heartbeats:
1. Use `planning-with-files` to persist state
2. On each heartbeat: READ plan → RECOVER context → DECIDE next step → PERSIST progress → REPORT
3. "Awaiting response" is valid — exit and pick up next heartbeat

## Memory Extraction

After work, extract durable facts to para-memory-files:
- Architecture decisions documented
- Project status patterns (which projects move fast, which stall)
- Recurring blockers and their root causes
- Engineer performance observations (for retro, not surveillance)
