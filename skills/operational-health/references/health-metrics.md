# Operational Health Metrics

Detailed metrics frameworks by entity type, aligned with Holdings operating rhythm scorecards.

## Universal Metrics (all entities)

| Metric | Healthy | Warning | Critical |
|---|---|---|---|
| Agent error rate | 0% | <5% agents in error | >5% agents in error |
| Task stale rate | 0 stale | <10% tasks stale | >10% tasks stale |
| Velocity ratio | >1.0 | 0.8-1.0 | <0.8 |
| Blocked task age | <24h | 24-48h | >48h |
| Approval backlog | 0 pending >24h | 1-2 pending >24h | 3+ pending >24h |

## SaaS Entity Metrics

For AI product entities (AI Recruiter, SafePracticeIT, GetHiredAI):

| Metric | Description | Source |
|---|---|---|
| Task throughput | Features/bugs completed per week | Issue completion count |
| Bug fix time | Average time from creation to done for bugs | Issue timestamps |
| Deploy frequency | How often code ships | Activity log |
| Cost per feature | Average spend per completed feature task | Costs / completed issues |

## Field Services Entity Metrics

For operational entities (Good Dirt, Curbside FSM):

| Metric | Description | Source |
|---|---|---|
| Task completion rate | % of tasks completed vs created | Issue status counts |
| Agent utilization | % of heartbeats with productive work | Activity log analysis |
| Escalation rate | % of tasks escalated to manager | Issue reassignment events |
| Response time | Time from task creation to first agent action | Issue timestamps |

## Agency Entity Metrics

For agency entities (Curbside Marketing):

| Metric | Description | Source |
|---|---|---|
| Client task throughput | Tasks completed per client project | Per-project issue counts |
| Quality gate pass rate | % of deliverables passing on first review | Quality gate records |
| Client responsiveness | Time to respond to client-facing tasks | Issue timestamps |
| Content velocity | Content pieces produced per period | Issue completion by label |

## Health Report Template

```markdown
## Operational Health Report — [Period]

### Overall Status: [HEALTHY / WARNING / CRITICAL]

### Agent Health
| Agent | Status | Budget | Last Active | Issues |
|---|---|---|---|---|

### Task Velocity
- Created: [X] | Completed: [Y] | Ratio: [Y/X]
- Stale: [count] | Blocked: [count]

### Findings
1. [Finding with metrics]

### Recommendations
1. [Action item]
```
