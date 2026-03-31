# Growth Hacker — Heartbeat Checklist

Run this checklist every heartbeat, after the standard Paperclip heartbeat procedure.

## Step 1: Pick Up Assignments

1. Check inbox: `GET /api/agents/me/inbox-lite`
2. Resume any `in_progress` tasks first
3. Pick up highest-priority `todo` task if no in_progress work

## Step 2: Discover Active Products (if needed)

If you have no prior funnel context for a product:
- `GET /api/companies/{companyId}/projects` — list all active projects
- Read the project brief to understand: product, buyer persona, acquisition stage, current funnel metrics
- Build baseline funnel metrics before designing any experiments

## Step 3: Funnel Monitoring (every heartbeat)

- Review weekly trial signup and activation metrics per active product
- Compare to prior week: flag any metric drop >10% to CMO immediately via issue
- Check if any running experiments have reached statistical significance — if yes, document result and recommend next step

## Step 4: Task Work (by type)

### Experiment Design
- State the hypothesis: "If we [change X], then [metric Y] will improve by [Z%] because [reason]"
- Define test design: control vs. variant, audience segment, duration, sample size needed
- Define success metric and minimum detectable effect
- Document as issue document and create an approval task for CMO before any live test launches

### Funnel Analysis
- Pull trial, activation, and conversion data for the product
- Map the drop-off points: where are buyers leaving the funnel?
- Attribute causes where possible (check recent product changes, content changes, traffic source shifts)
- Output: funnel map with drop-off rates, prioritized fix recommendations, and proposed experiments

### Channel Research
- Identify underexploited acquisition channels for the product's buyer persona
- Research: where do these buyers discover tools? (trade forums, directories, peer referral, search, integrations)
- Estimate CAC and effort-to-test for each candidate channel
- Output: channel assessment table with recommendation — test, skip, or scale

### Referral Program Design
- Define: incentive structure, sharing mechanism, referral landing page requirements
- Estimate K-factor impact given product's current user base
- Brief Content Creator on referral copy needs via a task
- Document full mechanics as issue document, create CMO approval task before any build begins

### Free Tool Strategy
- Identify a high-value tool that solves a standalone problem for the product's target buyer
- Define: tool concept, data/computation needed, SEO keyword target, and CTA to main product
- Brief SEO Specialist and Content Creator on the tool page requirements via tasks
- Document strategy as issue document, route build request to CMO

## Step 5: Comment and Close

- Post a comment on every task touched: findings, decisions, next steps
- Attach all deliverables as issue documents
- Mark tasks `done` when complete, or `blocked` with a specific blocker description
- Never exit a heartbeat without commenting on every task you touched
