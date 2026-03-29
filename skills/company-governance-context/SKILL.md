---
name: company-governance-context
description: >
  Foundation governance skill. Read this FIRST before using any other governance
  skill. Stores company mission, strategic goals, risk appetite, compliance
  requirements, decision authority thresholds, reporting cadence, and entity
  list. Use when setting up governance for a new company, updating governance
  parameters, or when any governance skill needs company context.
---

# Company Governance Context

The single source of truth for governance parameters. Every other governance skill reads this before acting.

## Where Context Lives

Governance context is stored as an issue document with key `governance-context` on a dedicated issue titled "Governance Context" in the governance-setup project.

```
GET /api/issues/{governanceContextIssueId}/documents/governance-context
```

## Before Any Governance Work

1. Check if governance context exists
2. If yes: read it, use it to inform your governance skill
3. If no: you must create it before proceeding (see Setup below)

## Setup (First Run Only)

When governance context does not exist, gather it interactively:

1. Read company description from `GET /api/companies/{companyId}`
2. Read company goals from `GET /api/companies/{companyId}/goals`
3. Read project list from `GET /api/companies/{companyId}/projects`
4. Ask the human board (via issue comment) to confirm or provide:
   - Company mission (1-2 sentences)
   - Strategic goals for this period
   - Risk appetite: conservative / moderate / aggressive
   - Compliance requirements (if any)
   - Decision authority thresholds (e.g., under $X = agent, $X-$Y = Chief of Staff, over $Y = human board)
   - Escalation preferences (what should reach the human)
   - Reporting cadence (weekly / monthly / quarterly)
5. Write the governance context document using the template in `references/context-template.md`
6. Post as issue document: `PUT /api/issues/{issueId}/documents/governance-context`

## Quarterly Update

Every quarter (or when strategic direction changes), the Chief of Staff should:
1. Read current governance context
2. Review against current company state
3. Update with any changes
4. Comment on the governance context issue noting what changed and why

## Related Skills

- All governance skills read this context first
- decision-protocol uses authority thresholds from this context
- escalation-protocol uses escalation preferences from this context
- governance-reporting uses cadence definitions from this context
