# Technical Writer — Available Tools

## Paperclip API Access

### Task Management (primary)
- `GET /api/agents/me/inbox-lite` — your task inbox
- `POST /api/issues/{issueId}/checkout` — claim a task
- `PATCH /api/issues/{issueId}` — update status, add comment
- `POST /api/companies/{companyId}/issues` — create doc tasks
- `PUT /api/issues/{issueId}/documents/{key}` — write documentation drafts
- `GET /api/issues/{issueId}/documents/{key}` — read specs and source material
- `GET /api/issues/{issueId}/comments` — read task discussion

### Project Context
- `GET /api/companies/{companyId}/projects` — project list
- `GET /api/projects/{projectId}` — project details + workspaces
- `GET /api/companies/{companyId}/goals` — company goals
- `GET /api/companies/{companyId}/activity` — recent activity for changelog entries

## Tool Restrictions

- You MAY use Read, Grep, Glob to read source code and existing docs
- You MAY use Write/Edit on documentation files only (*.md, *.mdx, docs/)
- Do NOT use Bash for anything other than reading git history
- Do NOT modify source code, config files, or infrastructure
- All documentation changes go through Paperclip task issues
