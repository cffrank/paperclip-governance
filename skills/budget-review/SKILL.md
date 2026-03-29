---
name: budget-review
description: >
  Monthly budget cycle for governance companies. Use when running the monthly
  budget review, recommending budget rebalancing between agents or projects,
  or when the CFO needs to produce the budget section of the board package.
  Distinct from financial-analysis (this is the approval workflow, not the analysis).
---

# Budget Review

The monthly budget cycle. Run on the cadence defined in governance context.

## Before Starting

Read company-governance-context for:
- Monthly budget total
- Per-agent and per-project allocations
- Authority thresholds for rebalancing
- Reporting cadence (when is the monthly review due?)

## Monthly Cycle

### 1. Run Financial Analysis

Invoke financial-analysis skill first. You need current spend data and trend analysis before reviewing budgets.

### 2. Compare Allocation vs. Need

For each agent:
- Is the current allocation sufficient for the remaining month?
- Is any agent consistently under-utilizing budget (waste)?
- Is any agent consistently hitting limits (underfunded)?

For each project:
- Is the project on track to complete within budget?
- Are there cost overruns that need addressing?

### 3. Recommend Rebalancing

If rebalancing is needed:
1. Use decision-protocol to record the recommendation with VFM score
2. Specify: move $X from [agent/project A] to [agent/project B]
3. Justify with evidence from financial-analysis findings

### 4. Check Authority

From governance context decision authority table:
- Rebalancing within your authority → recommend to Chief of Staff for approval
- Rebalancing above threshold → Chief of Staff escalates to human board

You never approve rebalancing yourself. Always recommend.

### 5. Produce Budget Section

Write the budget section for the monthly board report:
- Budget utilization summary
- Rebalancing recommendations (if any)
- Forecast for next month

Post as issue document or comment, per governance-reporting skill format.

For the full monthly close checklist, read `references/budget-cycle.md`.

## Related Skills

- financial-analysis provides the data for budget review
- decision-protocol records rebalancing recommendations
- escalation-protocol if rebalancing exceeds authority
- governance-reporting consumes budget review for board reports
- company-governance-context provides allocations and thresholds
