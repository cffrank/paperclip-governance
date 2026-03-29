---
name: governance-planning
description: >
  Develop plans through structured brainstorming spread across heartbeats.
  Use when any agent needs to create a plan, proposal, or strategy document.
  Routes planning questions through the Chief of Staff who delegates to the
  right C-suite member. Escalates to human board only when no C-level agent
  can answer. Adapts the brainstorming process for heartbeat-based execution.
---

# Governance Planning

Structured brainstorming for governance agents. Plans are developed iteratively across heartbeats using issue comments as the conversation medium.

## The Routing Rule

When any agent needs a plan developed:
1. Create an issue with the planning request
2. Assign to **Chief of Staff**
3. Chief of Staff decides who develops the plan:
   - Financial plans → CFO
   - Operational/compliance/risk plans → COO
   - Cross-cutting → Chief of Staff coordinates, creates subtasks for both
   - Above all C-suite authority → escalate to human board
4. The human board is the **last resort**, not the first stop

## Planning Flow (Across Heartbeats)

### Phase 1: Explore (1 heartbeat)

The assigned planner:
1. Read the planning request and any linked issues for context
2. Read governance context for relevant thresholds and policies
3. Check para-memory-files for similar past plans or patterns
4. Post an issue comment with:
   - **Understanding:** "Here's what I think we're solving..." (1-2 sentences)
   - **Questions:** 1-3 clarifying questions, one per bullet
   - **Scope check:** Is this one plan or does it need to be decomposed?
5. Reassign to whoever needs to answer (Chief of Staff, or the requesting agent)

Do NOT propose solutions yet. Understand first.

### Phase 2: Propose (1 heartbeat, after answers received)

The planner:
1. Read the answers from the comment thread
2. Propose 2-3 approaches as an issue comment:
   - **Option A (recommended):** description, pros, cons
   - **Option B:** description, pros, cons
   - **Option C (if applicable):** description, pros, cons
3. Include your recommendation and reasoning
4. Reassign to Chief of Staff for direction

### Phase 3: Develop (1 heartbeat, after direction chosen)

The planner:
1. Read which option was selected
2. Write the full plan as an issue document with key `plan`:

```
PUT /api/issues/{issueId}/documents/plan
{
  "title": "Plan",
  "format": "markdown",
  "body": "# Plan\n\n..."
}
```

3. Plan structure:
   - **Goal:** What this plan achieves (1 sentence)
   - **Approach:** Selected option with detail
   - **Tasks:** Numbered steps with owners and dependencies
   - **Thresholds:** Success criteria with specific metrics
   - **Risks:** What could go wrong and mitigations
   - **Timeline:** Estimated heartbeat/time budget
4. Comment with link to plan document: `[Plan](/<prefix>/issues/<identifier>#document-plan)`
5. Reassign to Chief of Staff for review

### Phase 4: Review (1 heartbeat)

Chief of Staff:
1. Read the plan document
2. Check against governance context (within authority? within budget?)
3. If approved: comment "Plan approved", assign to planner for execution
4. If changes needed: comment with specific revision requests, reassign to planner
5. If above authority: escalate to human board with the plan attached

Do NOT mark the issue as done. Leave it in_progress until the plan is executed.

## Plan Revision

If revisions are requested:
1. Read the revision comments
2. Update the existing plan document (use `baseRevisionId` from current version)
3. Comment noting what changed
4. Reassign to reviewer

## When to Skip This Flow

Not every task needs a full brainstorming cycle. Skip directly to Phase 3 (write the plan) when:
- The task is routine and follows an established pattern
- The approach is obvious from governance context
- The task is small enough to complete in 1-2 heartbeats

Use the full flow when:
- The task is new or ambiguous
- Multiple approaches exist with real trade-offs
- The outcome affects budget, strategy, or compliance
- The Chief of Staff explicitly requests a plan

## Related Skills

- company-governance-context provides thresholds and policies for plans
- decision-protocol records planning decisions
- escalation-protocol if planning exceeds C-suite authority
- quality-gate verifies plan execution met success criteria
