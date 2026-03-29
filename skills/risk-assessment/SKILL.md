---
name: risk-assessment
description: >
  Identify, score, and track organizational risks. Use when scanning for new
  risks, updating the risk register, scoring risk severity, or producing risk
  sections for board reports. Maintains a risk register as a Paperclip project
  with individual risks as issues.
---

# Risk Assessment

Find risks before they find you. Maintain a living risk register.

## Before Starting

Read company-governance-context for:
- Risk appetite (conservative / moderate / aggressive)
- Risk escalation threshold (default: score >=15)
- Entity/project list (risk sources)

## Risk Register

Risks are tracked as issues in a dedicated "Risk Register" project:
- Each risk = one issue
- Title: concise risk description
- Description: full risk record (see template below)
- Status: `todo` (identified) / `in_progress` (being mitigated) / `done` (mitigated or accepted) / `blocked` (mitigation stuck)
- Priority maps to risk score: critical (>=20), high (15-19), medium (10-14), low (<10)

## Risk Identification

Scan these sources for risk indicators:

1. **Budget risks:** Agents approaching limits, projects trending over budget (from financial-analysis)
2. **Operational risks:** Agents in error state, stale blocked tasks, declining task velocity (from operational-health)
3. **Compliance risks:** Policy violations found in compliance reviews
4. **Capacity risks:** Teams at capacity, no slack for unexpected work
5. **Dependency risks:** Critical work blocked on single agent or approval

## Risk Scoring

Score each risk: **Likelihood (1-5) x Impact (1-5)**

| Score | Severity | Action |
|---|---|---|
| 1-9 | Low | Monitor. Review quarterly. |
| 10-14 | Medium | Mitigation plan required. Review monthly. |
| 15-19 | High | Active mitigation. Escalate via escalation-protocol. |
| 20-25 | Critical | Immediate escalation. Stop related work if necessary. |

## Risk Record

For each risk, the issue description includes:
- **Risk:** What could go wrong
- **Likelihood:** 1-5 with justification
- **Impact:** 1-5 with justification
- **Score:** L x I
- **Mitigation:** What we're doing about it
- **Owner:** Who is responsible for the mitigation
- **Review date:** When to reassess

For the full scoring framework, read `references/risk-matrix.md`.

## Related Skills

- company-governance-context defines risk appetite and thresholds
- decision-protocol records risk decisions
- escalation-protocol invoked for high/critical risks
- operational-health and financial-analysis surface risk indicators
- governance-reporting consumes risk assessment for board reports
