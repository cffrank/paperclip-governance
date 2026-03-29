# Risk Assessment Matrix

## Likelihood Scale

| Score | Likelihood | Description |
|---|---|---|
| 1 | Rare | Could happen but very unlikely (<10% chance this quarter) |
| 2 | Unlikely | Possible but not expected (10-25% chance) |
| 3 | Possible | Could reasonably occur (25-50% chance) |
| 4 | Likely | More likely than not (50-75% chance) |
| 5 | Almost Certain | Expected to occur (>75% chance) |

## Impact Scale

| Score | Impact | Description |
|---|---|---|
| 1 | Negligible | Minor inconvenience, no financial or operational effect |
| 2 | Minor | Small financial loss (<5% of budget) or brief disruption |
| 3 | Moderate | Meaningful financial loss (5-15%) or multi-day disruption |
| 4 | Major | Significant financial loss (15-30%) or week+ disruption |
| 5 | Severe | Critical financial loss (>30%) or extended outage |

## Risk Heat Map

```
Impact →    1    2    3    4    5
Likelihood
    5        5   10   15   20   25
    4        4    8   12   16   20
    3        3    6    9   12   15
    2        2    4    6    8   10
    1        1    2    3    4    5
```

Green (1-9) | Yellow (10-14) | Orange (15-19) | Red (20-25)

## Common Risk Categories

| Category | Examples |
|---|---|
| Budget | Agent budget exhaustion, project cost overrun, unexpected spend |
| Operational | Agent errors, stale tasks, capacity constraints |
| Compliance | Policy violations, missed approvals, audit findings |
| Strategic | Goal misalignment, market changes, priority conflicts |
| Technical | Adapter failures, API errors, data integrity issues |
| People | Key agent dependency, knowledge silos, human board unavailability |

## Mitigation Template

```markdown
### Mitigation Plan: [Risk Title]

**Strategy:** [avoid / reduce / transfer / accept]

**Actions:**
1. [Specific action] — Owner: [agent] — Due: [date]
2. [Specific action] — Owner: [agent] — Due: [date]

**Residual Risk:** After mitigation, expected score: [L] x [I] = [score]

**Contingency:** If mitigation fails: [backup plan]

**Review:** Reassess on [date]
```
