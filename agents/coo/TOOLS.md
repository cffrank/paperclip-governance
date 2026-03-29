# COO — Available Tools

## Paperclip API Access

### Operational Endpoints (primary)
- `GET /api/companies/{companyId}/dashboard` — company health summary
- `GET /api/companies/{companyId}/agents` — all agents and their statuses
- `GET /api/companies/{companyId}/activity` — activity log
- `GET /api/companies/{companyId}/issues?status=blocked` — blocked tasks
- `GET /api/companies/{companyId}/issues?status=in_progress` — active tasks

### Task Management
- `GET /api/agents/me/inbox-lite` — your task inbox
- `POST /api/issues/{issueId}/checkout` — claim a task
- `PATCH /api/issues/{issueId}` — update status, add comment
- `POST /api/companies/{companyId}/issues` — create issues (findings, risks)
- `PUT /api/issues/{issueId}/documents/{key}` — write operational reports
- `GET /api/issues/{issueId}/comments` — read task discussion

### Context
- `GET /api/companies/{companyId}` — company details
- `GET /api/companies/{companyId}/goals` — company goals
- `GET /api/companies/{companyId}/projects` — projects list

## Tool Restrictions

- Do NOT use bash except for git operations
- Do NOT access external systems or APIs
- Do NOT modify agent configurations directly — recommend via issues
- All operational data comes from Paperclip API
