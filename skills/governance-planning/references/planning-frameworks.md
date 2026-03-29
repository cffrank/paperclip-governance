# Planning Frameworks Reference

Detailed frameworks loaded on demand. Sourced from superpowers, agent-playbook, conductor, NEXUS, and proactive-agent.

## Plan Document Templates

### Financial Plan Template (CFO)

```markdown
# Financial Plan: [Title]

**Goal:** [What financial outcome this achieves]
**Approach:** [Selected approach]
**VFM Score:** [X/50]

## Current State
- Total monthly spend: $[X] of $[Y] budget
- Per-agent breakdown: [table]
- Trend: [increasing/stable/decreasing]

## Phases

### Phase 1: Analysis
- [ ] Pull current cost data from all endpoints
- [ ] Compare against budget allocations
- [ ] Identify top 3 variance drivers
**Checkpoint:** Variance analysis complete with evidence

### Phase 2: Recommendation
- [ ] Score each recommendation with VFM
- [ ] Draft rebalancing proposal
- [ ] Model projected impact
**Checkpoint:** Recommendations ready for Chief of Staff review

### Phase 3: Implementation
- [ ] Submit approved changes
- [ ] Monitor for 1 week
- [ ] Verify projected impact matches actual
**Checkpoint:** Changes verified with post-implementation data

## Success Criteria
- Budget utilization within [X-Y]% range
- No agents hitting budget limits unexpectedly
- Variance from plan < [X]%

## Risks
| Risk | L | I | Mitigation |
|---|---|---|---|
| Rebalancing disrupts active work | 2 | 3 | Schedule during low-activity period |
```

### Operational Plan Template (COO)

```markdown
# Operational Plan: [Title]

**Goal:** [What operational outcome this achieves]
**Approach:** [Selected approach]
**VFM Score:** [X/50]

## Current State
- Agent health: [X] active, [Y] issues
- Task velocity: [ratio]
- Stale tasks: [count]
- Compliance status: [summary]

## Phases

### Phase 1: Assessment
- [ ] Run full operational health check
- [ ] Run compliance review
- [ ] Identify root causes (not just symptoms)
**Checkpoint:** Root cause analysis complete

### Phase 2: Remediation Design
- [ ] Propose fixes for each root cause
- [ ] Score each fix with VFM
- [ ] Identify quick wins vs. structural changes
**Checkpoint:** Remediation plan reviewed by Chief of Staff

### Phase 3: Implementation
- [ ] Execute quick wins first
- [ ] Implement structural changes
- [ ] Monitor metrics for improvement
**Checkpoint:** Metrics show improvement trend

## Success Criteria
- Task stale rate < [X]%
- Agent error rate = 0%
- Velocity ratio > [X]

## Risks
| Risk | L | I | Mitigation |
|---|---|---|---|
| Fix introduces new issues | 2 | 4 | Monitor closely for 48h post-change |
```

### Strategic Plan Template (Chief of Staff)

```markdown
# Strategic Plan: [Title]

**Goal:** [What strategic outcome this achieves]
**Approach:** [Selected approach]
**VFM Score:** [X/50]

## Context
- Governance context summary: [relevant excerpts]
- Financial position: [from CFO]
- Operational health: [from COO]

## Phases

### Phase 1: Research
- [ ] Gather input from CFO (financial implications)
- [ ] Gather input from COO (operational implications)
- [ ] Review governance context thresholds
**Checkpoint:** All C-suite input received

### Phase 2: Proposal
- [ ] Draft strategic proposal with 2-3 options
- [ ] Score each option (impact, risk, cost, timeline)
- [ ] Prepare board summary if escalation needed
**Checkpoint:** Proposal ready for review

### Phase 3: Decision
- [ ] Present to appropriate authority (self/human board)
- [ ] Record decision using decision-protocol
- [ ] Communicate decision to affected agents
**Checkpoint:** Decision recorded and communicated

### Phase 4: Execution
- [ ] Create execution tasks assigned to responsible agents
- [ ] Monitor progress via governance reporting
- [ ] 7-day follow-up on decision outcomes
**Checkpoint:** Execution verified with evidence

## Success Criteria
- Decision made within [X] heartbeats
- All stakeholders informed
- Execution tracked to completion
```

## Over-Engineering Prevention

Before finalizing any plan, ask:

1. **Does a simpler solution exist?** Look for the 80% solution. A quick process change (1-2 tasks) is almost always better than a structural overhaul (10+ tasks).

2. **Is an existing mechanism sufficient?** Check if current Paperclip features, existing skills, or established workflows already handle this. Don't build what's already there.

3. **Why doesn't the simple approach work?** If you're proposing something complex, write down specifically why the simple version fails. If you can't articulate it, use the simple version.

4. **Can we decompose?** If the plan has >5 phases or >25 tasks, it's too large. Break it into independent sub-plans that each deliver value on their own.

## Scope Sizing Guide

From conductor track management:

| Size | Phases | Tasks | Duration | Signal |
|---|---|---|---|---|
| Right-sized | 2-4 | 8-20 | 1-5 days | Clear start and end, manageable in scope |
| Too large | >5 | >25 | >1 week | Multiple unrelated outcomes, needs decomposition |
| Too small | 1 | 1-2 | <few hours | Skip formal planning, just do it |

## Self-Review Checklist

Run this before submitting any plan for review:

### Placeholder Scan
- [ ] No "TBD", "TODO", "figure out later" anywhere in plan
- [ ] No "add appropriate [X]" without specifying what X is
- [ ] No "similar to Phase N" — repeat the detail
- [ ] Every task has a clear owner
- [ ] Every phase has a checkpoint with specific criteria

### Consistency Check
- [ ] Phases build on each other logically
- [ ] Task owners match agent roles (CFO doesn't own operational tasks)
- [ ] Success criteria are measurable (numbers, not feelings)
- [ ] Timeline estimates are realistic for heartbeat cadence

### Authority Check
- [ ] All actions within governance context thresholds
- [ ] Escalation points identified for above-threshold decisions
- [ ] Budget implications noted if applicable

### Evidence Check
- [ ] Data sources specified for each assessment
- [ ] Checkpoints require evidence, not assertions
- [ ] Success criteria can be verified from Paperclip API data

## Parallel Planning Pattern

From NEXUS phase-gate model. When a plan requires input from multiple agents:

1. **Chief of Staff creates parallel subtasks** (one per agent needed)
2. Each agent researches independently in their domain (parallel heartbeats)
3. **Convergence:** Chief of Staff reads all inputs, synthesizes into unified plan
4. **Dual sign-off:** Both contributing agents confirm their sections are accurate

Example: Cross-cutting plan needs financial AND operational analysis
- Subtask 1 → CFO: "Analyze financial implications of [X]"
- Subtask 2 → COO: "Analyze operational implications of [X]"
- Chief of Staff waits for both, then writes unified plan

## Decision Record Integration

Every plan that gets approved should generate a decision record (via decision-protocol):

- **What:** The plan that was approved
- **Evidence:** Data from Phase 1 exploration
- **Alternatives:** Options B and C from Phase 2
- **VFM Score:** From the recommended option
- **Follow-up:** Check outcome at plan completion + 7 days after
