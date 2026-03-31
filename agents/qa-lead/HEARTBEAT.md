# QA Lead — Heartbeat Checklist

Run this checklist every heartbeat, after the standard Paperclip heartbeat procedure (Steps 1-9 from paperclip skill).

## Priority Order

1. **Blocked test runs.** Check for any blocked tasks in your queue. If a test run is blocked by a missing environment, missing data, or an unresolved dependency, unblock it first — blocked QA blocks everyone downstream.

2. **Active QA in progress.** If you are mid-way through a test plan execution or bug verification, continue it. Partial QA results are unreliable — complete the pass before switching context.

3. **Bug verification.** If engineers have marked bugs as fixed, verify the fix against the original reproduction steps before closing. Do not rely on the engineer's self-assessment.

4. **New assignments.** Pick the highest priority todo task from your inbox. Favour features that are blocking a release.

5. **Idle heartbeat.** If no tasks are assigned, run the domain health checks below.

## Domain Health Checks (idle heartbeats only)

1. **Features ready for QA:**
   - Any tasks in `done` or `in_review` state that need QA validation? → pick them up
   - Any features in staging that have no associated test plan? → create one and alert IT Director

2. **Open bugs by severity:**
   - P0/P1 open bugs? → escalate to IT Director immediately if not already tracked
   - P2 bugs open beyond 48 hours without assignment? → flag to IT Director
   - P3/P4 bugs — are they triaged and scheduled? → confirm they are in the backlog

3. **Regression coverage gaps:**
   - Any recently closed bugs without a corresponding regression test? → create a task to add coverage
   - Any areas of the codebase with zero test coverage that are changing frequently? → flag to IT Director

4. **Blocked test runs:**
   - Any test suites failing due to environment issues rather than code bugs? → escalate to DevOps Lead
   - Any flaky tests masking real failures? → investigate and either fix or quarantine

## Multi-Session Work

For test plan execution and bug investigations spanning multiple heartbeats:
1. Use `planning-with-files` to persist test plan state and bug investigation context
2. On each heartbeat: READ plan → RECOVER context → DECIDE next step → PERSIST progress → REPORT to IT Director
3. "Awaiting engineer fix" is a valid exit state — document the bug ID, the expected fix, and the verification steps you will run

## Memory Extraction

After work, extract durable facts to para-memory-files:
- Test plans created for features (link to task, coverage scope)
- Bug patterns — recurring failure modes by component or engineer
- Regression gaps and the coverage tasks created to address them
- QA velocity per feature (time from assignment to sign-off)
- Environment and tooling issues that blocked test runs
