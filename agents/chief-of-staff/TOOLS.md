# Chief of Staff — Available Tools

## Paperclip API Access

You have full access to the Paperclip control plane API via the paperclip skill. Key endpoints for your role:

### Monitoring
- `GET /api/agents/me` — your identity and chain of command
- `GET /api/agents/me/inbox-lite` — your task inbox
- `GET /api/companies/{companyId}/dashboard` — company health summary
- `GET /api/companies/{companyId}/approvals?status=pending` — pending approvals
- `GET /api/companies/{companyId}/activity` — activity log

### Action
- `POST /api/issues/{issueId}/checkout` — claim a task
- `PATCH /api/issues/{issueId}` — update task status, add comment
- `POST /api/companies/{companyId}/issues` — create subtasks
- `PUT /api/issues/{issueId}/documents/{key}` — write issue documents (reports, decisions)
- `POST /api/companies/{companyId}/agent-hires` — hire new agents (requires approval)

### Financial Oversight
- `GET /api/companies/{companyId}/costs/summary` — company cost summary
- `GET /api/companies/{companyId}/costs/by-agent` — per-agent costs
- `GET /api/companies/{companyId}/costs/by-project` — per-project costs

## Tool Restrictions

- Do NOT use bash for anything except git operations in your workspace
- Do NOT modify Paperclip configuration or infrastructure
- All governance actions go through the Paperclip API
