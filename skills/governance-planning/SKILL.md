---
name: governance-planning
description: >
  Develop plans through structured brainstorming adapted for heartbeat execution.
  Use when any agent needs to create a plan, proposal, or strategy document.
  Routes planning through Chief of Staff who delegates to the right C-suite
  member. Escalates to human board only when no C-level can answer. Combines
  patterns from superpowers brainstorming, agent-playbook PRD planning, conductor
  track management, NEXUS phase gates, and proactive-agent WAL protocol.
---

# Governance Planning

Structured brainstorming for governance agents. Plans are developed iteratively across heartbeats using issue comments as the conversation medium. The human board is the last resort, not the first stop.

## Hard Gate

Do NOT take implementation action until a plan is written and approved. This applies to EVERY initiative regardless of perceived simplicity. A plan can be short (a few sentences for simple tasks), but it MUST exist and be approved before execution begins.

## The Routing Rule

When any agent needs a plan:
1. Create an issue describing the planning need
2. Assign to **Chief of Staff**
3. Chief of Staff routes to the right planner:
   - Financial plans → CFO
   - Operational / compliance / risk plans → COO
   - Cross-cutting → Chief of Staff coordinates, creates subtasks for both
   - Nobody can answer → escalate to human board
4. The assigned planner runs the planning flow below

## Planning Flow (Across Heartbeats)

### Phase 1: Explore Context (1 heartbeat)

Before asking anyone anything, gather context yourself:

1. Read the planning request and all linked issues
2. Read governance context for relevant thresholds and policies
3. Pull data from Paperclip API relevant to the domain:
   - Financial: `GET /api/companies/{companyId}/costs/summary`
   - Operational: `GET /api/companies/{companyId}/dashboard`
   - Activity: `GET /api/companies/{companyId}/activity`
4. Check para-memory-files for similar past plans or patterns
5. Scan for edge cases in the existing data BEFORE asking questions — reduce redundant questions by finding answers yourself first

Post an issue comment with:
- **Context gathered:** What you already know (2-3 bullets)
- **Scope check:** Is this one plan or does it need decomposition? (Right-sized: 1-5 days, 2-4 phases, 8-20 tasks. Larger = decompose first.)
- **Questions:** 1-3 clarifying questions that you could NOT answer from existing data

Reassign to whoever needs to answer. Exit heartbeat.

### Phase 2: Propose Approaches (1 heartbeat, after answers received)

1. Read answers from the comment thread
2. Look for the 80% solution first — do NOT over-engineer
3. Propose 2-3 approaches as an issue comment:

```
## Approaches

### Option A (recommended): [name]
- **What:** [description]
- **Pro:** [benefit]
- **Con:** [cost/risk]
- **Effort:** [low / medium / high]

### Option B: [name]
- **What:** [description]
- **Pro:** [benefit]
- **Con:** [cost/risk]
- **Effort:** [low / medium / high]

### Recommendation
Option A because [specific reasoning with evidence from Phase 1 data].
```

4. Include VFM score for the recommended option (from decision-protocol):
   - High Frequency Impact (3x), Failure Reduction (3x), User Burden (2x), Self Cost (2x)
   - Minimum score to proceed: 25/50
5. Reassign to Chief of Staff for direction. Exit heartbeat.

### Phase 3: Develop Plan (1 heartbeat, after direction chosen)

1. Read which option was selected
2. Write the plan using decision-protocol (WAL: write BEFORE acting)
3. Store as issue document:

```
PUT /api/issues/{issueId}/documents/plan
{
  "title": "Plan",
  "format": "markdown",
  "body": "# [Plan Title]\n\n..."
}
```

4. Plan structure:

```markdown
# [Plan Title]

**Goal:** [One sentence — what this achieves]
**Approach:** [Selected option name and 1-2 sentence summary]
**VFM Score:** [X/50]

## Context
[Key data points from Phase 1 that inform this plan]

## Phases

### Phase 1: [Name]
- [ ] Task 1.1: [specific, actionable, with owner]
- [ ] Task 1.2: [specific, actionable, with owner]
**Checkpoint:** [What must be true before advancing]

### Phase 2: [Name]
- [ ] Task 2.1: [specific, actionable, with owner]
- [ ] Task 2.2: [specific, actionable, with owner]
**Checkpoint:** [What must be true before advancing]

## Success Criteria
- [Specific metric or outcome 1]
- [Specific metric or outcome 2]

## Risks
| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| [risk] | [1-5] | [1-5] | [action] |

## Timeline
[Estimated heartbeats or calendar time per phase]
```

5. Comment with link: `[Plan](/<prefix>/issues/<identifier>#document-plan)`
6. Reassign to Chief of Staff for review. Exit heartbeat.

**No placeholders in plans.** Every task must be specific and actionable. These are plan failures — never write them:
- "TBD", "TODO", "figure out later"
- "Add appropriate handling" (without specifying what)
- "Similar to Phase 1" (repeat the detail)
- Tasks without clear owners or checkpoints

### Phase 4: Review and Approve (1 heartbeat)

Chief of Staff reviews the plan:

1. **Self-review checklist** (run before sending to human):
   - Placeholder scan: Any "TBD", "TODO", vague tasks? → reject, send back
   - Consistency: Do phases build on each other logically?
   - Scope: Is this right-sized or does it need decomposition?
   - Authority: Is everything within governance context thresholds?
   - Evidence: Are success criteria measurable, not subjective?

2. **Decision:**
   - **Approved:** Comment "Plan approved", assign to planner for execution
   - **Revise:** Comment with specific revision requests, reassign to planner
   - **Escalate:** Above authority threshold → escalate to human board with plan attached
   - **Dual sign-off** (for cross-cutting plans): Both CFO and COO must approve their sections before Chief of Staff gives final approval

Do NOT mark the issue as done. Leave in_progress until execution completes.

### Phase 5: Execute (multiple heartbeats)

1. Planner works through tasks using status markers:
   - `[ ]` — Pending
   - `[~]` — In Progress
   - `[x]` — Complete
   - `[-]` — Skipped (with reason)
   - `[!]` — Blocked (with blocker description)

2. At each phase checkpoint:
   - Verify checkpoint criteria are met with evidence (not assertions)
   - Comment with checkpoint status
   - If checkpoint fails: do NOT advance. Fix or escalate.

3. Use quality-gate skill at major milestones.

4. Update plan document with progress (use `baseRevisionId`).

### Phase 6: Close and Learn (1 heartbeat)

After all phases complete:
1. Verify success criteria are met (evidence required)
2. Write outcome summary as comment
3. Record lessons learned in para-memory-files
4. If outcome differs from plan: note what changed and why (decision-protocol)
5. Mark issue done

## Multi-Heartbeat Recovery

Plans span multiple heartbeats. On each heartbeat for a planning task:

1. **READ:** Check the issue document for current plan state
2. **RECOVER:** Read recent comments for any updates since last heartbeat
3. **DECIDE:** What phase are we in? What's the next action?
4. **PERSIST:** Update plan document or post comment with progress
5. **REPORT:** Comment on the issue before exiting

"Awaiting response" is a valid state — do not treat it as failure. If you posted questions in Phase 1 and no one has answered yet, exit the heartbeat. You'll pick it up when answers arrive.

## When to Skip Phases

Not every task needs the full flow. Skip to Phase 3 (write plan directly) when:
- The task is routine and follows an established pattern
- The approach is obvious from governance context
- The task can complete in 1-2 heartbeats
- No trade-offs exist between approaches

Use the full flow when:
- The task is new or ambiguous
- Multiple valid approaches exist
- The outcome affects budget, strategy, or compliance
- Chief of Staff explicitly requests a plan

## Reverse Prompting

At Phase 1, after gathering context, ask yourself: "What would genuinely help this company that hasn't been asked for?" If you spot an opportunity while researching, note it. Surface it as an additional recommendation in Phase 2 — don't wait to be asked.

## Related Skills

- company-governance-context provides thresholds and policies for plans
- decision-protocol provides WAL and VFM scoring (use for Phase 3)
- escalation-protocol if planning exceeds C-suite authority
- quality-gate verifies phase checkpoints and plan completion
- governance-reporting consumes plan outcomes for board reports

For detailed plan templates and review checklists, read `references/planning-frameworks.md`.
