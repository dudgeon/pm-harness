---
id: 006
title: Context ecosystem and data structure
status: draft
created: 2026-09-27
updated: 2026-09-27
ladders_to: [D6, D2]
---

# 006 · Context ecosystem and data structure

## Why
This is path axis 3 (Q-007). Context and traces are probably the path-dependent assets (H-009), and
the data structure is one of the hardest choices to retrofit (Q-015). The regulated setting (C7,
Q-014) shapes both. Geoff wants these questions researched and deliberated, not answered on
instinct, and this goal is where that happens.

## Definition of done
_Vague:_ A context ecosystem design, with the reasoning behind it. It covers:
- where context lives
- how it's governed and validated, and what makes it credible
- how the context-building loop runs
- how opinionated the data structure is, and which entities are recorded, shareable, or canonical
- which enterprise controls it has to satisfy

## Requirements
- R1: Research and analysis come before decisions. Don't force Q-007 or Q-015 early (Geoff,
  2026-09-27).
- R2: Derive the entities from the inputs and outputs in the taxonomy (goal 003).
- R3: Respect earned adoption. Capture context as a byproduct of work (C6, H-011, Q-013).
- R4: Serve delivery as well. SDD agents read the same layer (DEC-010, Q-008).
- R5: Work within a regulated enterprise's controls, described generically (C5, C7, Q-014).

## Constraints
- Inherits C1–C8.

## Assumptions
- DEC-011 (build context iteratively), which rests on H-007.
- H-009, H-011, H-012, and H-013 (all hypotheses).

## Non-goals
- Building the context layer. That's part of D1.
- Choosing the v1 bet. That's goal 001, which this goal feeds.

## Open
- Q-007, Q-014, and Q-015, which are its main questions.
- Ramp builds context by synthesizing it automatically from the exhaust of work. DEC-011 builds it
  through a loop that humans carry out and validate. Are those complementary, or competing?
- Declarative context (facts, constraints, decisions) and procedural context (skills and playbooks
  for doing moves): one layer or two?
