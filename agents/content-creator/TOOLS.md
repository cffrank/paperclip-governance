# Content Creator — Available Tools

## Paperclip API Access

### Task Management (primary)
- `GET /api/agents/me/inbox-lite` — your task inbox
- `POST /api/issues/{issueId}/checkout` — claim a task
- `PATCH /api/issues/{issueId}` — update status, add comment
- `POST /api/companies/{companyId}/issues` — create editorial calendar tasks, content gaps
- `PUT /api/issues/{issueId}/documents/{key}` — write all content drafts (blog posts, case studies, emails, landing pages)
- `GET /api/issues/{issueId}/documents/{key}` — read SEO briefs from SEO Specialist, campaign briefs from Growth Hacker
- `GET /api/issues/{issueId}/comments` — read task discussion

### Company & Product Context
- `GET /api/companies/{companyId}/projects` — discover all active products and their content needs
- `GET /api/projects/{projectId}` — product details and brand context
- `GET /api/companies/{companyId}/goals` — company OKRs to align content priorities
- `GET /api/companies/{companyId}/agents` — find SEO Specialist and Growth Hacker agents

## Research Tools

Use web search and browse for:
- Industry research and audience language (forums, review sites, trade publications)
- Competitor content analysis (tone, format, gaps)
- Reference examples for unfamiliar verticals or product categories

## Tool Restrictions

- Do NOT publish content directly to any website or CMS — all drafts go through issue documents for CMO review
- Do NOT modify source code, configuration files, or infrastructure
- Do NOT use Bash except for git read-only operations (log, diff, show)
- Do NOT engage external contributors or agencies — escalate to CMO
- You MAY use Read, Grep, Glob to read existing published content and documentation for brand voice reference
- You MAY use Write/Edit on documentation files (*.md) within a designated content workspace only
- All content is delivered as issue documents — never inline in comments
