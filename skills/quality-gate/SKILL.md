---
name: quality-gate
description: >
  Phase-gate verification requiring evidence before advancement. Use when a
  governance milestone needs sign-off (budget approval, compliance certification,
  strategic plan approval), when verifying that a remediation was effective, or
  when any governance action requires proof before proceeding. Maximum 3 gate
  attempts before escalation.
---

# Quality Gate

Evidence over assertions. Nothing advances without proof.

## Gate Process

### Step 1: Define Evidence Requirements

Before running the gate, specify what must be proven:
- What criteria must be met?
- What data demonstrates each criterion?
- Where does that data come from (which API endpoint, which issue document)?

### Step 2: Collect Evidence

Gather evidence from Paperclip API:
- Cost data from `/api/companies/{companyId}/costs/*`
- Dashboard data from `/api/companies/{companyId}/dashboard`
- Activity log from `/api/companies/{companyId}/activity`
- Issue documents from `/api/issues/{issueId}/documents/{key}`
- Agent statuses from `/api/companies/{companyId}/agents`

### Step 3: Verify

For each requirement:
- Does the evidence meet the criterion? Document: YES (with data) or NO (with gap)
- "I believe it's fine" is NOT evidence. Show the number.

### Step 4: Decide

- **All criteria met:** Advance. Record gate passage using decision-protocol.
- **Some criteria failed:** Return with specific list of what failed and what's needed to pass.
- **Gate failed 3 times:** Invoke escalation-protocol. The issue is beyond routine resolution.

## Common Gates

| Gate | Criteria | Evidence Source |
|---|---|---|
| Budget approval | Spend within allocation, no anomalies | costs/summary, costs/by-agent |
| Compliance certification | All policies being followed | activity log, issue statuses |
| Operational health | No agents in error, no stale tasks | dashboard, agent statuses |
| Risk acceptance | All high risks have mitigation plans | risk register project issues |

## Configurable Thresholds

Gate thresholds come from company-governance-context. Common thresholds:
- Budget warning: X% of allocation (default: 80%)
- Stale task: X hours in_progress (default: 48)
- Blocked task escalation: X hours (default: 48)
- Risk escalation: likelihood x impact >= X (default: 15)

## Related Skills

- company-governance-context provides threshold values
- decision-protocol records gate passage/failure
- escalation-protocol invoked after 3 gate failures
