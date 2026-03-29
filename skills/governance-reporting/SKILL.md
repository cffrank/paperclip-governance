---
name: governance-reporting
description: >
  Assemble board reports from governance skill outputs. Use when producing
  weekly check-ins, monthly operating reviews, or quarterly business reviews.
  Collects findings from financial-analysis, operational-health, compliance-review,
  and risk-assessment into structured board reports.
---

# Governance Reporting

Assemble governance findings into board-ready reports.

## Before Starting

Read company-governance-context for:
- Reporting cadence (weekly / monthly / quarterly)
- Report format preferences
- Entity/project list for coverage

## Report Types

### Weekly Check-in

Chief of Staff produces this from CFO + COO inputs.

Format:
```
WINS (what improved this week):
-

BLOCKERS (what's stuck and who needs to act):
-

NUMBERS (3 key metrics vs. target):
- [metric]: [actual] vs [target]
- [metric]: [actual] vs [target]
- [metric]: [actual] vs [target]

NEXT WEEK (top 3 priorities):
1.
2.
3.
```

Post as issue comment on the weekly reporting task.

### Monthly Operating Review

Chief of Staff assembles from CFO and COO findings.

Sections (time-boxed per Holdings operating rhythm):
1. **Financial Review** (from CFO) — budget vs actual, variances, recommendations
2. **Division Reports** (from COO) — agent health, task velocity, compliance status
3. **Decisions Made** — summary of decisions from decision-protocol records this month
4. **Strategic Topic** — one question for human board to consider next month

Post as issue document with key `monthly-report-YYYY-MM`.

### Quarterly Business Review

Chief of Staff assembles comprehensive QBR.

Sections:
1. **Quarter Review** — what was planned vs. what happened
2. **Portfolio Review** — per-project performance assessment
3. **Resource Allocation** — budget rebalancing, hiring needs
4. **Risk Register Summary** — active risks and mitigations
5. **OKR Assessment** — progress against quarterly goals
6. **Next Quarter Plan** — proposed priorities and resource allocation

Post as issue document with key `qbr-YYYY-QN`.

For detailed templates, read `references/report-templates.md`.

## Assembly Process

1. Check for CFO findings: search recent issue documents and comments for financial analysis
2. Check for COO findings: search recent issue documents for health reports, compliance reviews, risk updates
3. Combine into the appropriate report format
4. Post as issue document on the reporting task
5. Comment on the task tagging the human board for review

## Related Skills

- financial-analysis and budget-review provide financial sections
- operational-health provides operational sections
- compliance-review provides compliance sections
- risk-assessment provides risk sections
- company-governance-context defines cadence and format
