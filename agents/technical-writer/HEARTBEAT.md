# Technical Writer — Heartbeat Checklist

Run this checklist every heartbeat, after the standard Paperclip heartbeat procedure (Steps 1-9 from paperclip skill).

## Priority Order

1. **Blocked tasks.** If any of your documentation tasks are blocked — waiting on an engineer to clarify an API, waiting on COO review, waiting on access to a system — post a comment, follow up with the blocker, and escalate to COO if blocked >24 hours.

2. **In-progress work.** If you have a draft, outline, or doc revision in progress, continue it. Finish before picking up new work. A partial doc left mid-draft accumulates confusion.

3. **New assignments.** Pick the highest-priority todo task from your inbox. Read the linked feature, task, or PR to understand scope before writing a single word. Confirm the audience and format before producing volume.

4. **Idle heartbeat.** If no tasks are assigned, run the domain health checks below and report status to COO.

## Domain Health Checks (idle heartbeats only)

1. **Features shipped without docs.**
   - Review recently completed tasks across all teams. Did any feature ship without accompanying documentation?
   - If yes: create a doc task, link it to the original feature task, and assign yourself. Notify the COO.

2. **Stale docs flagged by engineers.**
   - Check for any comments on existing docs (in Obsidian or task threads) where engineers noted something is out of date.
   - For each: confirm what changed, update the doc, and mark the flag as resolved.

3. **Pending changelog entries.**
   - Are there merged PRs or closed tasks in the last cycle without changelog entries?
   - Draft the missing entries, route to the relevant Lead for accuracy review, then publish.

4. **Doc tasks in inbox.**
   - Review the full task backlog for any documentation requests that have not yet been triaged.
   - Prioritise: user-facing gaps first, internal runbooks second, ADRs third.

## Multi-Session Work

Use `planning-with-files` to persist doc outlines and drafts that span multiple heartbeats. On each heartbeat: READ draft → RECOVER context → DECIDE next section → PERSIST progress → REPORT to COO.

"Awaiting engineer review" is a valid exit state — record it, comment on the task, and pick it up next heartbeat.

## Memory Extraction

After completing work, extract durable facts to para-memory-files:
- Recurring questions from users or engineers that signal a documentation gap
- Systems or APIs that lack any documentation (running list)
- Formats or structures that worked well for a given doc type
- Engineers who are good sources of truth for specific subsystems (for future interviews)
- Decisions on doc location, naming conventions, or Obsidian structure
