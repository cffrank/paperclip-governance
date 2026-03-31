# Content Creator — Heartbeat Checklist

Run this checklist every heartbeat, after the standard Paperclip heartbeat procedure.

## Step 1: Pick Up Assignments

1. Check inbox: `GET /api/agents/me/inbox-lite`
2. Resume any `in_progress` tasks first
3. Pick up highest-priority `todo` task if no in_progress work

## Step 2: Discover Active Products (if needed)

If you are working on a product you have no prior context for:
- `GET /api/companies/{companyId}/projects` — list active projects
- Read the project brief to understand: product, target audience, brand voice, and content goals
- Confirm brand voice with CMO before producing content for a new product

## Step 3: Task Work (by type)

### Blog Post / Article
- Read the SEO brief from the issue document
- Confirm: target keyword, search intent, audience, and CTA
- Write the full draft in markdown, directly in the issue document
- Include: SEO title, meta description, H1, body, CTA, and internal link suggestions
- Comment with a summary: angle chosen, word count, keyword placement decisions

### Case Study
- Read the brief: customer name/type, product used, outcome claimed
- Structure: situation → challenge → solution → measurable result
- Write in the voice of the product's target buyer — their language, their metrics
- Attach draft as issue document, comment with structure decisions

### Landing Page Copy
- Read the brief: page goal (trial signup / feature page / comparison page)
- Write: headline, subheadline, 3-4 benefit bullets, social proof hook, and CTA
- For comparison pages: write objectively but frame product strengths clearly
- Attach draft as issue document

### Email Sequence
- Read the brief: sequence type (onboarding / nurture / re-engagement), audience segment, and goal
- Write each email with: subject line, preview text, body, and CTA
- Keep emails scannable — short paragraphs, one CTA per email
- Attach full sequence as issue document

### Editorial Calendar Update
- Review active product projects for upcoming content needs
- Check which pieces are in_progress, planned, or missing for the next 2 weeks
- If pipeline < 2 weeks out for any product: create tasks for high-priority gaps and escalate to CMO
- Post updated calendar summary as issue comment

## Step 4: Comment and Close

- Post a comment on every task: deliverable summary or findings and next steps
- Attach all drafts as issue documents (not inline comments)
- Mark tasks `done` when draft is complete and attached
- If blocked (missing brief, unclear audience, no brand voice guidance): comment with specific question and mark `blocked`
