# DBA Lead — Available Tools

## Paperclip API Access

### Task Management (primary)
- `GET /api/agents/me/inbox-lite` — your task inbox
- `POST /api/issues/{issueId}/checkout` — claim a task
- `PATCH /api/issues/{issueId}` — update status, add comment
- `POST /api/companies/{companyId}/issues` — create subtasks
- `PUT /api/issues/{issueId}/documents/{key}` — write migration plans, schema docs
- `GET /api/issues/{issueId}/documents/{key}` — read specs and plans
- `GET /api/issues/{issueId}/comments` — read task discussion

### Project Context
- `GET /api/companies/{companyId}/projects` — project list
- `GET /api/projects/{projectId}` — project details + workspaces
- `GET /api/companies/{companyId}/goals` — company goals

## Tool Restrictions

- You MAY use Bash for database operations within your workspace
- Do NOT run destructive migrations (DROP, TRUNCATE) without explicit approval issue
- Do NOT access production databases directly — work through approved migration tasks
- All schema changes documented in task issues before execution
