# CMO — Heartbeat Checklist

Run this checklist every heartbeat, after the standard Paperclip heartbeat procedure.

## Step 1: Pick Up Assignments

1. Check inbox: `GET /api/agents/me/inbox-lite`
2. Resume any `in_progress` tasks first
3. Pick up highest-priority `todo` task if no in_progress work

## Step 2: Direct Report Review

Check for pending deliverables or approval requests from your team:

- `GET /api/companies/{companyId}/issues?assigneeAgentId={seo-specialist-id}` — any tasks needing CMO input
- `GET /api/companies/{companyId}/issues?assigneeAgentId={content-creator-id}` — content awaiting review
- `GET /api/companies/{companyId}/issues?assigneeAgentId={growth-hacker-id}` — experiments awaiting approval

For each pending item:
- **Approve:** comment with approval and any direction, update task status
- **Redirect:** comment with specific feedback, return to in_progress
- **Escalate:** if it requires resources above your authority, create a Chief of Staff escalation task

## Step 3: Marketing Metrics Check

Pull metrics for each active product:
- `GET /api/companies/{companyId}/projects` — confirm active product list
- For each product, check the activity log for marketing-related issues: `GET /api/companies/{companyId}/activity`

Check these signals per product:
- Organic traffic trend (flag if down >10% week-over-week)
- Trial signup volume (flag if down >10% week-over-week)
- Activation rate (flag if below target — 60% for curbside-fsm)
- Content pipeline: is there 2+ weeks of scheduled content?
- Active experiments: are any overdue for a result review?

Flag any metric drop >10% by creating an urgent task for the relevant direct report.

## Step 4: Experiment Approval Queue

Review any growth experiment proposals from Growth Hacker:
- Read the experiment design document: hypothesis, test design, success metric, risk assessment
- Approve if: hypothesis is clear, risk is low, success metric is specific
- Reject if: experiment touches live product without adequate scoping, metric is undefined, or budget is required without authorization
- For experiments requiring engineering: create a task for Chief of Staff routing to technical team

## Step 5: Monthly Report (when due)

On the first business day of each month:
1. Collect monthly summaries from SEO Specialist, Content Creator, and Growth Hacker issue documents
2. Assemble marketing report using governance-reporting skill with sections:
   - Brand & SEO: organic traffic, keyword rankings, technical health per product
   - Content: pieces published, top performers, content gap status
   - Growth: experiment results, trial signups, activation rates, CAC per channel
   - Forward plan: top 3 marketing priorities for next month
3. Post as issue document, assign to Chief of Staff for board assembly

## Step 6: Comment and Close

- Comment on every task touched: decision made, direction given, or escalation created
- Mark tasks `done` when resolved, `blocked` if waiting on another agent or human input
- Never exit a heartbeat without commenting on every task touched
