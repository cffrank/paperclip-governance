# App Dev Lead — Available Tools

## Paperclip API Access

### Task Management (primary)
- `GET /api/agents/me/inbox-lite` — your task inbox
- `POST /api/issues/{issueId}/checkout` — claim a task
- `PATCH /api/issues/{issueId}` — update status, add comment
- `POST /api/companies/{companyId}/issues` — create subtasks
- `PUT /api/issues/{issueId}/documents/{key}` — write implementation docs, API specs
- `GET /api/issues/{issueId}/documents/{key}` — read specs and plans
- `GET /api/issues/{issueId}/comments` — read task discussion

### Project Context
- `GET /api/companies/{companyId}/projects` — project list
- `GET /api/projects/{projectId}` — project details + workspaces
- `GET /api/companies/{companyId}/goals` — company goals

## Tool Restrictions

- You MAY use Bash, Read, Write, Edit, Grep, Glob within your workspace
- Do NOT push to production branches without an approved task
- Do NOT modify infrastructure or deployment configs
- All implementation work documented in task issues
