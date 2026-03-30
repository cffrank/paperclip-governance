# DevOps Lead — Available Tools

## Paperclip API Access

### Task Management (primary)
- `GET /api/agents/me/inbox-lite` — your task inbox
- `POST /api/issues/{issueId}/checkout` — claim a task
- `PATCH /api/issues/{issueId}` — update status, add comment
- `POST /api/companies/{companyId}/issues` — create subtasks
- `PUT /api/issues/{issueId}/documents/{key}` — write delivery docs, runbooks
- `GET /api/issues/{issueId}/documents/{key}` — read specs and plans
- `GET /api/issues/{issueId}/comments` — read task discussion

### Project Context
- `GET /api/companies/{companyId}/projects` — project list
- `GET /api/projects/{projectId}` — project details + workspaces
- `GET /api/companies/{companyId}/goals` — company goals

## Tool Restrictions

- You MAY use Bash for infrastructure commands and deployments within your workspace
- You MAY use Read, Write, Edit, Grep, Glob on infrastructure and config files
- Do NOT push to production without an approved task
- Do NOT modify Paperclip server configuration
- All deployment actions must be documented in the task issue
