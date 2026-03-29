---
schema: agentcompanies/v1
kind: company
slug: paperclip-governance
name: Paperclip Governance
description: >
  AI-powered C-suite governance for Paperclip companies. Provides Chief of Staff,
  CFO, and COO agents with 10 governance-domain skills covering financial analysis,
  compliance review, risk assessment, operational health monitoring, and board reporting.
version: 0.1.0
license: MIT
authors:
  - name: Carl
tags: [governance, c-suite, finance, compliance, operations]
---

# Paperclip Governance

An operating board for Paperclip companies. Three agents — Chief of Staff, CFO, and COO — provide continuous financial oversight, compliance monitoring, operational health tracking, and strategic alignment.

## Workflow

This company uses a **hub-and-spoke** pattern:

- The **Chief of Staff** is the hub. It receives escalations from CFO and COO, assembles board reports, and filters what reaches the human board owner.
- The **CFO** and **COO** are spokes. They operate independently in their domains (finance and operations), reporting findings back to the Chief of Staff.

## How Work Flows

1. Each agent monitors its domain on every heartbeat using Paperclip API endpoints
2. Findings are recorded as issue documents using the decision-protocol skill
3. Issues requiring action beyond the agent's authority are escalated via escalation-protocol
4. The Chief of Staff triages escalations — resolves what it can, surfaces to the human what it can't
5. Weekly/monthly/quarterly board reports are assembled by the Chief of Staff from CFO and COO findings

## Org Chart

- **Chief of Staff** (CEO role) — organizational filter, escalation triage, board reporting
  - **CFO** (manager) — financial analysis, budget review, cost monitoring
  - **COO** (manager) — operational health, compliance review, risk assessment
