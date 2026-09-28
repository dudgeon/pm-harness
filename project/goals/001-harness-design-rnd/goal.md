---
id: 001
title: Harness design R&D
status: draft
created: 2026-09-27
updated: 2026-09-27
ladders_to: [D2, D1]
---

# 001 · Harness design R&D

## Why
The aim is to choose the v1 bet without committing too early. Early choices constrain later ones on
three axes ([path](../../context/wiki/path.md)):
- which moves to start with (Q-006)
- which deployment model v1 targets (Q-001)
- how to approach the context ecosystem (Q-007)

This goal pulls the work of goals 003–006 together into a single decision.

## Definition of done
_Vague:_ A v1 bet (D2) that names the first moves, the deployment model, and the context approach,
along with the path they sit on and a rationale grounded in evidence. The evidence includes the
teardowns, the effort baseline, and what we learn from dogfooding the scaffold.

## Requirements
- R1: Evaluate more than one candidate position along the path. Examples:
  - standardized skills in each PM's own Claude Code
  - hybrids that write to a shared context store
  - a shared, deployed agent
- R2: Use evidence from goals 003–006, and from running this project on project-scaffold-v1
  (`scaffold-friction` notes, the wiki).
- R3: Keep later stops open. Check every candidate against H-009, which says context and traces
  should be shared from day one.
- R4: The bet has to be plausible under earned adoption (C6) and a regulated enterprise's controls
  (C7).

## Constraints
- Inherits C1–C8. C1 may not apply to the harness at all (Q-012).

## Assumptions
- H-001: running this project on project-scaffold-v1 informs the harness design (hypothesis).
- project-scaffold-v1 is not itself a candidate harness design: grounded (DEC-003).
- H-002, H-009, and H-010 are the hypotheses this goal leans on hardest.

## Non-goals
- Building the production harness. That comes after the bet.

## Open
- What's the time box, and how many candidates should we compare?
- Who signs off on the bet?
- Does C1 constrain the harness (Q-012)?
