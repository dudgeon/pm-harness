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
Many harness designs could work. We want to explore candidates and pick one to build and deploy
(D1) without committing too early.

## Definition of done
_Vague:_ A chosen design, with a rationale grounded in evidence, including evidence from
dogfooding v0.

## Requirements
- R1: Evaluate more than one candidate design (likely deployed agents or orchestrators).
- R2: Use evidence from running this project on project-scaffold-v1 (`scaffold-friction` notes, wiki).

## Constraints
- Inherits C1–C4. Note that C1 is a v0 default and may be revisited by this goal.

## Assumptions
- H-001: running this project on project-scaffold-v1 informs the harness design (hypothesis)
- project-scaffold-v1 is not itself a candidate harness design: grounded (DEC-003)

## Non-goals
- Building the production harness. That comes after the selection.

## Open
- Time box? Number of candidates?
- What are the evaluation criteria, and who signs off on the choice?
