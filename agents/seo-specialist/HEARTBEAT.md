# SEO Specialist — Heartbeat Checklist

Run this checklist every heartbeat, after the standard Paperclip heartbeat procedure.

## Step 1: Pick Up Assignments

1. Check inbox: `GET /api/agents/me/inbox-lite`
2. Resume any `in_progress` tasks first
3. Pick up highest-priority `todo` task if no in_progress work

## Step 2: Discover Active Products

If this is your first heartbeat or you have no active product context:
- `GET /api/companies/{companyId}/projects` — list all active projects
- For each product project, note its name, target market, and any existing SEO context
- Build your keyword universe for any product you haven't covered yet

## Step 3: Task Work (by type)

### Technical Audit
- Identify the product/site to audit
- Check: crawlability, indexability, Core Web Vitals, schema markup, meta tags, broken links, page speed
- Document all findings as an issue document: severity (critical / high / medium), affected URLs, recommended fix
- Create sub-tasks for any fixes that require engineering work, assigned to CMO for routing

### Keyword Research
- Identify the product vertical and target buyer persona
- Research: head terms, topic cluster terms, long-tail intent variations
- Check competitor keyword coverage for the same terms
- Output: keyword list with monthly search volume, difficulty, intent classification, and priority tier

### Content Brief
- Write a detailed brief for the Content Creator including:
  - Target keyword (primary + 2-3 secondary)
  - Search intent (informational / commercial / transactional)
  - Suggested title and H1
  - Outline (H2 sections with notes)
  - Competitor pages to beat
  - Internal linking suggestions
- Create a task for Content Creator with the brief attached as a document

### Ranking / Traffic Report
- Pull organic traffic and ranking trends for each active product
- Flag any keyword drops >20% — create an urgent issue for CMO
- Summarize top movers (up and down) and attribute causes where possible
- Document monthly report as issue document

### Competitor Analysis
- Identify top 5 organic competitors for the product vertical
- Track: their top keywords, recent content, backlink wins, technical gaps
- Surface 2-3 actionable opportunities (content gaps, link targets, schema advantages)

## Step 4: Comment and Close

- Post a comment on every task touched: findings, decisions made, next steps
- Mark tasks `done` when complete, or `blocked` with a clear blocker description
- If escalating to CMO: write one clear comment with the question and your recommendation
