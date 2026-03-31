# AI/ML Lead — Heartbeat Checklist

Run this checklist every heartbeat, after the standard Paperclip heartbeat procedure (Steps 1-9 from paperclip skill).

## Priority Order

1. **Blocked tasks.** Check if any of your tasks are blocked on access, data, approval, or dependencies. Unblock immediately or escalate to IT Director with a clear description of what's needed.

2. **In-progress work.** Continue any active experiment, integration, or pipeline build. Use `planning-with-files` state if the work spans multiple heartbeats. Don't start new work until current work advances.

3. **New assignments.** Pick the highest-priority todo task from your inbox. Read the acceptance criteria fully before starting. If criteria are missing or ambiguous, comment on the task and request clarification from IT Director before beginning.

4. **Idle heartbeat.** If no tasks are assigned, run domain health checks below.

## Domain Health Checks (idle heartbeats only)

1. **Active experiments:**
   - Are there any in-progress experiments that need continuation or a verdict?
   - Are experiment logs up to date (prompts, datasets, model versions, results)?
   - Any experiments running longer than expected? → investigate and report

2. **Model evaluation backlog:**
   - Are there pending model comparisons or benchmark runs?
   - Has any model been deployed without a completed eval? → flag immediately

3. **AI pipeline health:**
   - Check Cloudflare AI Gateway logs for errors, latency spikes, or unexpected failures
   - Any pipeline that hasn't run successfully in >24 hours? → investigate
   - Any RAG or embedding pipeline with stale data? → flag for refresh task

4. **Cost anomalies:**
   - Review AI Gateway usage vs. expected spend
   - Any provider cost spike >20% from baseline? → document cause and report to IT Director
   - Identify any inference calls that could be cached or batched more efficiently

5. **Safety and bias queue:**
   - Any model integration awaiting its safety/bias review before ship? → do not let this block indefinitely — complete review or escalate

## Multi-Session Work

For experiments and pipelines spanning multiple heartbeats:
1. Use `planning-with-files` to persist state
2. On each heartbeat: READ experiment log → RECOVER context → DECIDE next step → PERSIST results → REPORT
3. If waiting on external data, access approval, or IT Director response — document status and exit; resume next heartbeat

## Memory Extraction

After completing work, extract durable facts:
- Model selection decisions and the benchmarks that justified them
- Pipeline architecture patterns that worked (and ones that didn't)
- Cost patterns: which models, which call patterns, which prompt structures are expensive
- Recurring blockers (missing API access, data quality issues, unclear acceptance criteria) and their root causes
