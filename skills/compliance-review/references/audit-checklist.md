# Compliance Audit Checklist

Detailed checklist for periodic compliance reviews. Maps to governance charter requirements.

## Budget Compliance

- [ ] All agents spending within allocated budget
- [ ] No unauthorized budget rebalancing
- [ ] Budget exhaustion events documented and addressed
- [ ] Cost trends within acceptable range (from governance context)

## Task Management Compliance

- [ ] No tasks in_progress beyond stale threshold without update comment
- [ ] No tasks blocked beyond escalation threshold without escalation
- [ ] All subtasks have parentId set (hierarchy maintained)
- [ ] No tasks cancelled by agents outside the assigning team
- [ ] All in_progress tasks have an active assignee

## Escalation Compliance

- [ ] Blocked tasks have blocker comments explaining what's stuck
- [ ] Escalations include: what was tried, recommendation, urgency
- [ ] Chain of command followed (not skipping levels)
- [ ] No silent blocked work (status updated before heartbeat exit)

## Approval Gate Compliance

- [ ] Agent hires went through approval workflow
- [ ] Budget changes above threshold got proper authorization
- [ ] Strategic decisions consulted human board per governance context
- [ ] Approval responses within reasonable timeframe

## Communication Compliance

- [ ] Agents commenting on tasks before exiting heartbeats
- [ ] Ticket references formatted as links (per paperclip skill)
- [ ] Issue documents used for plans and reports (not inline descriptions)
- [ ] @-mentions used sparingly (budget-conscious)

## Severity Definitions

| Severity | Definition | Action |
|---|---|---|
| Info | Process could be improved | Note in report, recommend improvement |
| Warning | Policy bent but not broken | Create advisory comment on relevant issue |
| Violation | Policy broken | Create remediation issue, assign to manager |
| Critical | Systemic or repeated violation | Escalate to Chief of Staff immediately |
