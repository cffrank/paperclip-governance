# Paperclip Governance

AI-powered C-suite governance for Paperclip companies.

## What This Is

A reusable company package that adds structured governance to any Paperclip company. Three agents — Chief of Staff, CFO, and COO — provide continuous financial oversight, compliance monitoring, operational health tracking, and board reporting.

## Agents

| Agent | Role | Model | Responsibilities |
|---|---|---|---|
| **Chief of Staff** | CEO | claude-opus-4-6 | Escalation triage, board reporting, hiring |
| **CFO** | Manager | claude-sonnet-4-6 | Financial analysis, budget review, cost monitoring |
| **COO** | Manager | claude-sonnet-4-6 | Operational health, compliance, risk assessment |

## Skills (10)

| Skill | Type | Used By |
|---|---|---|
| company-governance-context | Foundation | All agents |
| financial-analysis | Domain | CFO |
| budget-review | Domain | CFO |
| compliance-review | Domain | COO |
| risk-assessment | Domain | COO |
| operational-health | Domain | COO |
| decision-protocol | Operational | All agents |
| quality-gate | Operational | All agents |
| escalation-protocol | Operational | All agents |
| governance-reporting | Operational | Chief of Staff, CFO, COO |

## Getting Started

```bash
paperclipai company import --from paperclip-governance/
```

After import:
1. Approve the 3 agent hires in Paperclip UI
2. Chief of Staff will bootstrap the governance context (asks you questions)
3. CFO runs first financial review
4. COO runs first operational health check
5. Agents enter steady-state heartbeat monitoring

## Growth Path

- **Need compliance specialist?** Hire a CLO under Chief of Staff
- **Need marketing?** COO hires a Marketing Manager
- **Need engineering?** Chief of Staff hires a CTO
- **Need revenue focus?** Add CRO or revenue skills to CFO

## License

MIT

## Credits

Built for [Paperclip](https://github.com/paperclipai/paperclip) using patterns from:
- [Agent Companies Specification](https://agentcompanies.io/specification)
- [Agent Skills Specification](https://agentskills.io/specification)
