# Financial Analysis Frameworks

Detailed frameworks loaded on demand when deeper analysis is needed.

## Spend Ratio Analysis

### Budget Utilization Ratio
```
utilization = (current_spend / monthly_allocation) x 100
```
- Green: <60%
- Yellow: 60-80%
- Orange: 80-95%
- Red: >95%

### Burn Rate
```
daily_burn = current_spend / days_elapsed_this_month
projected_monthly = daily_burn x days_in_month
```
Flag if projected_monthly > monthly_allocation.

### Per-Agent Efficiency
```
cost_per_task = agent_spend / tasks_completed
```
Compare across agents doing similar work. Outliers (>2 standard deviations) warrant investigation.

## Trend Detection

### Week-over-Week Change
```
wow_change = (current_week_spend - prior_week_spend) / prior_week_spend x 100
```
Flag if wow_change > 50% (rapid acceleration).

### Moving Average
Track 4-week moving average per agent. Current spend >1.5x the moving average is an anomaly.

## Anomaly Scoring

Score each anomaly:

| Factor | Weight | Score 1-5 |
|---|---|---|
| Magnitude (how far from baseline) | 3x | 1=slight, 5=extreme |
| Duration (how long has it persisted) | 2x | 1=new, 5=ongoing |
| Impact (effect on company budget) | 3x | 1=negligible, 5=material |

**Total = sum of (score x weight).** Maximum: 40.
- Score <15: info (note but no action)
- Score 15-25: warning (monitor closely)
- Score >25: critical (escalate)

## Monthly Financial Report Template

```markdown
## Financial Report — [Month YYYY]

### Executive Summary
- Total spend: $[X] of $[Y] budget ([Z]% utilization)
- Trend: [increasing / stable / decreasing] vs prior month
- Anomalies: [count] ([critical / warning / info])

### Per-Agent Breakdown
| Agent | Spend | Budget | Utilization | Trend | Status |
|---|---|---|---|---|---|

### Per-Project Breakdown
| Project | Spend | Budget | Utilization | Trend | Status |
|---|---|---|---|---|---|

### Findings
1. [Finding with metrics and recommendation]

### Recommendations
1. [Action with VFM score from decision-protocol]
```
