# App Dev Lead — Heartbeat Checklist

Run this checklist every heartbeat, after the standard Paperclip heartbeat procedure (Steps 1-9 from paperclip skill).

## Priority Order

1. **Blocked tasks.** Check if any in-progress tasks are blocked on a dependency, environment issue, or missing requirement. Resolve immediately or escalate to IT Director with a specific description of the blocker.

2. **In-progress work.** Advance active feature development. If the task spans multiple heartbeats, use `planning-with-files` to maintain state. Complete tests before marking any subtask done.

3. **New assignments.** Pick the highest-priority todo task from your inbox. Before writing any code: confirm acceptance criteria exist, confirm test requirements are clear. If either is missing, comment on the task and wait for IT Director clarification.

4. **Idle heartbeat.** If no tasks are assigned, run domain health checks below.

## Domain Health Checks (idle heartbeats only)

1. **Tasks in progress:**
   - Are all in-progress tasks actively moving?
   - Any task in_progress with no recent activity? → comment with status update
   - Any task that has been in_progress for longer than its estimated scope? → flag to IT Director

2. **PRs awaiting IT Director review:**
   - Are there open PRs that have been submitted for review but not yet actioned?
   - If a PR has been waiting >1 heartbeat with no feedback → ping IT Director via task comment
   - Do not merge any PR that is still awaiting review

3. **Build and test health:**
   - Any failing builds or test suites on active branches? → treat as blocked; fix before new work
   - Any recently merged code that caused a regression? → create a bug task immediately

4. **Test coverage gaps:**
   - Any recently completed tasks that were marked done without test evidence? → flag and create follow-up task
   - Any feature area known to have weak test coverage? → add coverage tasks to backlog and report to IT Director

## Multi-Session Work

For features spanning multiple heartbeats:
1. Use `planning-with-files` to persist state
2. On each heartbeat: READ plan → RECOVER context → DECIDE next step (next failing test or next slice) → PERSIST progress → REPORT
3. If waiting on IT Director review or a dependency from another team — document status and exit; resume next heartbeat

## Memory Extraction

After completing work, extract durable facts:
- API design decisions and the reasoning behind them
- Patterns that accelerated delivery (small PRs, good test fixtures, clear acceptance criteria)
- Recurring blockers (unclear requirements, missing test data, environment issues) and their root causes
- Backwards-compatibility decisions: what changed, what was preserved, what was deprecated and when
