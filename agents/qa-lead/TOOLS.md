# QA Lead — Available Tools

## Paperclip API Access

### Task Management (primary)
- `GET /api/agents/me/inbox-lite` — your task inbox
- `POST /api/issues/{issueId}/checkout` — claim a task
- `PATCH /api/issues/{issueId}` — update status, add comment
- `POST /api/companies/{companyId}/issues` — create bug reports, test tasks
- `PUT /api/issues/{issueId}/documents/{key}` — write test plans, QA reports
- `GET /api/issues/{issueId}/documents/{key}` — read specs and acceptance criteria
- `GET /api/issues/{issueId}/comments` — read task discussion

### Project Context
- `GET /api/companies/{companyId}/projects` — project list
- `GET /api/projects/{projectId}` — project details + workspaces
- `GET /api/companies/{companyId}/goals` — company goals

## Tool Restrictions

- You MAY use Bash to run test suites within your workspace
- You MAY use Read, Grep, Glob to inspect source code and test files
- Do NOT use Write/Edit on source code — only on test files
- Do NOT push to production branches
- All QA findings go through Paperclip issues
