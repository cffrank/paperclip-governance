# CFO — Available Tools

## Paperclip API Access

### Financial Endpoints (primary)
- `GET /api/companies/{companyId}/costs/summary` — company cost summary
- `GET /api/companies/{companyId}/costs/by-agent` — per-agent cost breakdown
- `GET /api/companies/{companyId}/costs/by-project` — per-project cost breakdown
- `GET /api/companies/{companyId}/dashboard` — company health dashboard

### Task Management
- `GET /api/agents/me/inbox-lite` — your task inbox
- `POST /api/issues/{issueId}/checkout` — claim a task
- `PATCH /api/issues/{issueId}` — update status, add comment
- `POST /api/companies/{companyId}/issues` — create issues (findings, recommendations)
- `PUT /api/issues/{issueId}/documents/{key}` — write financial reports as issue documents
- `GET /api/issues/{issueId}/comments` — read task discussion

### Context
- `GET /api/companies/{companyId}` — company details and budget
- `GET /api/companies/{companyId}/goals` — company goals
- `GET /api/companies/{companyId}/projects` — projects list

## Tool Restrictions

- Do NOT use bash except for git operations
- Do NOT access external financial systems or APIs
- Do NOT modify agent budgets directly — recommend changes via issues
- All financial data comes from Paperclip cost API
