---
name: decision-protocol
description: >
  Write-Ahead Logging for governance decisions. Use BEFORE taking any governance
  action — write the decision record first, then act. Includes VFM scoring for
  change requests and outcome tracking for decisions older than 7 days. Use when
  recording financial findings, compliance violations, risk assessments,
  operational recommendations, or any governance action that changes state.
---

# Decision Protocol

Write decisions down BEFORE acting on them. This is non-negotiable.

## The WAL Rule

**Write-Ahead Logging:** Every governance decision is recorded as an issue document BEFORE the action is taken. This creates an immutable audit trail.

1. Identify the decision to be made
2. Write the decision record to the issue document with key `decision`
3. THEN take the action
4. Update the decision record with the outcome

```
PUT /api/issues/{issueId}/documents/decision
```

## Decision Record Structure

Use the template in `references/decision-record-template.md`. Minimum fields:

- **What:** The decision being made
- **Evidence:** Specific data points supporting the decision
- **Alternatives:** Other options considered (minimum 1)
- **VFM Score:** Value-First Modification score (see below)
- **Action:** What will be done
- **Follow-up:** When to check the outcome (default: 7 days)

## VFM Scoring

Score every change request before recommending it:

| Factor | Weight | Score 1-5 |
|---|---|---|
| High Frequency Impact | 3x | How often does this issue occur? |
| Failure Reduction | 3x | How much does this reduce failure risk? |
| User Burden Reduction | 2x | How much does this reduce human effort? |
| Self Cost | 2x | How expensive is this to implement? (invert: 5=cheap, 1=expensive) |

**Total = sum of (score x weight).** Maximum: 50. Minimum to recommend: 25.

## Outcome Tracking

For decisions older than 7 days:
1. Check: did the action achieve its goal?
2. If yes: note outcome, close follow-up
3. If no: create new finding with updated analysis
4. Record lesson learned in para-memory-files

## Immutability

Decision records are never deleted. To change a decision:
1. Create a new decision record that supersedes the old one
2. Reference the original: "Supersedes decision from [date] on [issue]"
3. Explain why the original decision is being revised

## Related Skills

- company-governance-context provides authority thresholds for decisions
- escalation-protocol is invoked when a decision exceeds authority
- quality-gate uses decision records as evidence
