# CFO — Heartbeat Checklist

Run this checklist every heartbeat, after the standard Paperclip heartbeat procedure.

## Financial Monitoring

1. **Cost check.** Pull company cost summary:
   - `GET /api/companies/{companyId}/costs/summary`
   - Compare total spend against monthly budget from governance context
   - If spend > 80% of monthly budget, flag in a comment on your monitoring task

2. **Per-agent costs.** Pull per-agent breakdown:
   - `GET /api/companies/{companyId}/costs/by-agent`
   - Flag any agent whose spend exceeds its individual budget allocation by >80%
   - Note agents with unusual spend patterns (spikes vs. baseline)

3. **Per-project costs.** Pull per-project breakdown:
   - `GET /api/companies/{companyId}/costs/by-project`
   - Compare against project budget allocations from governance context
   - Flag projects trending over budget

4. **Anomaly detection.** Compare current costs against previous heartbeat:
   - Significant spike (>2x previous period) → create finding using decision-protocol
   - New cost category appearing → note for investigation
   - Agent paused due to budget exhaustion → escalate to Chief of Staff

## Memory Extraction

After monitoring, extract durable financial facts to para-memory-files:
- Cost trends observed
- Budget utilization patterns
- Anomalies detected and their resolution
