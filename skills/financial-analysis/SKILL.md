---
name: financial-analysis
description: >
  Analyze company financials using Paperclip cost API. Use when monitoring spend
  trends, detecting cost anomalies, comparing budget vs actual, or producing
  financial findings for board reports. Covers per-agent costs, per-project
  costs, trend analysis, and anomaly detection.
---

# Financial Analysis

Structured procedure for analyzing company financials through Paperclip's cost API.

## Before Starting

Read company-governance-context for:
- Budget thresholds and limits
- Reporting cadence
- Entity/project list with budget allocations
- Risk appetite (affects anomaly sensitivity)

## Analysis Procedure

### 1. Pull Current Data

```
GET /api/companies/{companyId}/costs/summary
GET /api/companies/{companyId}/costs/by-agent
GET /api/companies/{companyId}/costs/by-project
```

### 2. Budget Comparison

For each agent and project:
- Current spend vs. monthly allocation
- Utilization percentage: (spend / allocation) x 100
- Flag if utilization > warning threshold from governance context (default: 80%)

### 3. Trend Analysis

Compare current period against previous:
- Week-over-week change in total spend
- Month-over-month change per agent
- Identify acceleration (spend increasing faster than linear)

### 4. Anomaly Detection

Flag if any of these occur:
- Agent spend >2x its previous period baseline
- New cost category appearing (agent not previously active)
- Agent paused due to budget exhaustion
- Total company spend on pace to exceed monthly budget before month end

### 5. Record Findings

For each finding, use decision-protocol to write a decision record:
- What was found (specific metrics)
- Severity: info / warning / critical
- Recommendation: no action / monitor / rebalance / escalate

### 6. Escalation

If any finding is critical or exceeds your authority, invoke escalation-protocol.

## Output

Post findings as issue comment with summary table. For monthly reports, write full analysis as issue document with key `financial-analysis`.

For detailed frameworks (ratio analysis, trend formulas, anomaly scoring), read `references/analysis-frameworks.md`.

## Related Skills

- company-governance-context provides thresholds
- budget-review is the monthly approval cycle (this skill is the analysis)
- decision-protocol records financial findings
- governance-reporting consumes financial analysis for board reports
