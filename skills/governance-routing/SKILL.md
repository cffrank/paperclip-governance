---
name: governance-routing
description: >
  Routes governance work to the right agent and the right skill. Use when any
  agent receives a task that needs planning, review, investigation, or
  strategic decision. The Chief of Staff is the hub — all routing goes through
  them. This skill does NOT replace brainstorming, planning, or review skills.
  It decides WHO uses them and WHEN, adapted for heartbeat execution.
---

# Governance Routing

This skill is the traffic controller. It decides who handles what and which skill they use. The actual work is done by the installed skills (superpowers, gstack, etc.).

## Hard Gate

Do NOT skip routing. Every non-trivial task goes through the Chief of Staff first. The Chief of Staff decides the path — not the requesting agent.

## The Routing Table

When the Chief of Staff receives a task or escalation, route by type:

### Planning & Design
| Signal | Route to | Skill to use |
|---|---|---|
| New initiative, vague idea | Chief of Staff | `office-hours` (validate problem first) |
| Validated idea needs design | Chief of Staff → domain expert | `brainstorming` (explore → design → spec) |
| Approved design needs plan | Domain expert | `writing-plans` (spec → implementation plan) |
| Plan needs strategic review | Chief of Staff | `plan-ceo-review` (challenge premises, lock scope) |
| Run full review pipeline | Chief of Staff | `autoplan` (CEO → Design → Eng reviews) |

### Financial
| Signal | Route to | Skill to use |
|---|---|---|
| Cost anomaly detected | CFO | `financial-analysis` |
| Monthly budget cycle due | CFO | `budget-review` |
| Budget rebalancing needed | CFO → Chief of Staff for approval | `decision-protocol` |
| Financial question from any agent | CFO | `financial-analysis` |

### Operational
| Signal | Route to | Skill to use |
|---|---|---|
| Agent health issue | COO | `operational-health` |
| Stale/blocked task detected | COO | `operational-health` |
| Compliance review due | COO | `compliance-review` |
| New risk identified | COO | `risk-assessment` |
| Process improvement needed | COO | `governance-routing` → plan via `brainstorming` |

### Investigation & Safety
| Signal | Route to | Skill to use |
|---|---|---|
| Bug or unexpected behavior | COO | `investigate` (root cause first, then fix) |
| Security concern | Chief of Staff | `cso` (security audit) |
| Production issue | COO | `investigate` + `guard` (safety mode) |
| Scope needs restricting | Any agent | `freeze` (lock edits to affected area) |

### Review & Reporting
| Signal | Route to | Skill to use |
|---|---|---|
| Work ready for review | Chief of Staff | `review` (pre-landing analysis) |
| Weekly/monthly report due | Chief of Staff assembles | `governance-reporting` |
| Retrospective due | Chief of Staff | `retro` (metrics and trends) |

### Escalation
| Signal | Route to | Skill to use |
|---|---|---|
| Above CFO/COO authority | Chief of Staff | `escalation-protocol` |
| Above Chief of Staff authority | Human board | `escalation-protocol` |
| CFO and COO disagree | Chief of Staff arbitrates | See Consensus Pattern below |
| Nobody can answer | Human board | `escalation-protocol` |

## Heartbeat Adaptation

External skills (superpowers, gstack) assume live interactive sessions. In heartbeat execution, adapt:

- **"Ask the user"** → post issue comment, reassign to responder, exit heartbeat
- **"Wait for approval"** → reassign to reviewer, exit heartbeat
- **"Run subagent"** → create subtask assigned to the right agent
- **"Present options"** → post options as issue comment with clear choices
- **One question per heartbeat** → don't batch questions, ask one, exit, pick up next heartbeat

The conversation happens via issue comments. Each heartbeat is one turn.

## Consensus Pattern

When a decision needs input from multiple C-suite agents (cross-cutting):

1. Chief of Staff creates parallel subtasks — one per agent
2. Each agent provides their analysis independently (no cross-contamination)
3. Chief of Staff reads all inputs and creates a **consensus table:**

```markdown
## Consensus Table

| Dimension | CFO Assessment | COO Assessment | Agreement |
|---|---|---|---|
| Budget impact | Low risk | — | — |
| Operational impact | — | Medium risk | — |
| Timeline feasible | Yes | Yes | CONFIRMED |
| Approach preference | Option A | Option B | DISAGREE |

### Confirmed (both agree)
- Timeline is feasible

### Taste Decisions (disagree — needs judgment)
- Approach preference: CFO prefers A (lower cost), COO prefers B (faster execution)
- **Recommendation:** [Chief of Staff's recommendation with reasoning]
```

4. **CONFIRMED** items → auto-decided, no escalation needed
5. **DISAGREE** items → classified as **taste decisions**:
   - If within Chief of Staff authority → Chief of Staff decides, logs rationale
   - If above authority → escalates to human board with the consensus table

## Auto-Decision Principles

When the Chief of Staff or any agent needs to make a mechanical decision (not a taste decision), apply these principles in priority order:

1. **Completeness** — choose the more thorough option (cost of completeness with AI is near-zero)
2. **Boil the lake** — if it's in the blast radius and <1 day effort, include it
3. **Pragmatic** — same problem, two fixes? pick the cleaner one
4. **DRY** — duplicates? reject
5. **Explicit over clever** — obvious > abstraction
6. **Bias toward action** — merge > review cycles, decide > deliberate

**Taste decisions** (where reasonable people disagree) are NEVER auto-decided. They are explicitly surfaced with the reasoning from both sides.

## Required Outputs

"Looks good" is not an acceptable governance review. Every routing decision and review must produce:

- **Decision audit trail entry** (via decision-protocol): who decided, what, why, what was rejected
- **Evidence** for the decision (API data, metrics, document references)
- **Taste decisions surfaced** explicitly when applicable
- **Next action** clearly assigned to a specific agent

## Related Skills

This skill references but does NOT replace:
- `office-hours`, `brainstorming`, `writing-plans` (from superpowers/gstack — planning process)
- `plan-ceo-review`, `autoplan` (from gstack — review pipeline)
- `investigate`, `cso`, `review`, `retro` (from gstack — investigation and review)
- `careful`, `freeze`, `guard` (from gstack — safety guardrails)
- `financial-analysis`, `budget-review`, `compliance-review`, `risk-assessment`, `operational-health` (our domain skills)
- `decision-protocol`, `escalation-protocol`, `quality-gate`, `governance-reporting` (our operational skills)
