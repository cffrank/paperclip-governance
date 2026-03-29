# Governance Context Template

Use this template when creating the initial governance context document. Fill in all sections. Store as issue document with key `governance-context`.

---

## Company Overview

- **Mission:** [1-2 sentence company mission]
- **Strategic Goals:**
  1. [Goal 1]
  2. [Goal 2]
  3. [Goal 3]

## Risk & Compliance

- **Risk Appetite:** [conservative / moderate / aggressive]
- **Compliance Requirements:** [List any regulatory or policy requirements, or "None" if N/A]

## Decision Authority

| Decision Type | Agent Authority | Chief of Staff Authority | Human Board Required |
|---|---|---|---|
| Routine monitoring | Yes | — | — |
| Budget rebalancing under $[X] | — | Yes | — |
| Budget rebalancing over $[X] | — | — | Yes |
| New agent hire under $[X]/mo | — | Yes | — |
| New agent hire over $[X]/mo | — | — | Yes |
| New project creation | — | — | Yes |
| Strategic pivot | — | — | Yes |

## Escalation Preferences

- **Always escalate to human:** [list — e.g., budget changes over $X, new projects, strategic decisions]
- **Chief of Staff can resolve:** [list — e.g., routine rebalancing, compliance findings, operational fixes]
- **Agents resolve independently:** [list — e.g., monitoring, reporting, task management]

## Reporting Cadence

- **Weekly:** [day of week] — Division check-in (wins, blockers, numbers, priorities)
- **Monthly:** [day of month] — Full board operating review
- **Quarterly:** [month] — QBR (quarter review, portfolio review, OKR assessment)

## Entity / Project List

| Project | Division | Owner | Key Metrics |
|---|---|---|---|
| [project-name] | [division] | [agent-slug] | [metric1, metric2] |

## Thresholds

- **Budget warning:** [X]% of monthly allocation (default: 80%)
- **Stale task threshold:** [X] hours in_progress without update (default: 48)
- **Blocked task escalation:** [X] hours blocked before auto-escalation (default: 48)
- **Risk escalation score:** [X] (likelihood x impact, default: 15)
