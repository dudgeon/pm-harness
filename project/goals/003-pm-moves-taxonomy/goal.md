---
id: 003
title: PM moves taxonomy
status: draft
created: 2026-09-27
updated: 2026-09-27
ladders_to: [D3, D2]
---

# 003 · PM moves taxonomy

## Why
Geoff: "this all rests upon a more complete sense than I have about the major product moves we
should focus on, and a usable taxonomy" ([thesis note](../../context/inbox/_processed/2026-09-27-thesis-and-direction.md)).
The same list of moves is the unit of analysis for four things:
- effort (goal 005)
- choosing the first moves (goal 001)
- the context ontology (goal 006): inputs are the context the layer must hold, and outputs are the
  context it gains
- the spec contract with delivery (Q-008)

This goal answers Q-004.

## Definition of done
_Vague:_ A usable taxonomy of the major PM moves at a large regulated enterprise. For each move it
gives the inputs, process, outputs, judgment content, the context the move consumes and produces,
and its delegation potential. "Usable" means goals 001, 005, and 006 can work from it without
inventing their own.

## Requirements
- R1: Build from industry best practice and from scratch, not from the enterprise's own lifecycle
  taxonomy (DEC-012).
- R2: Avoid the flaws of the pre-AI taxonomy (DEC-012): vague step definitions, false precision in
  some steps, too little detail in others. Keep the granularity consistent, and define each move
  well enough to annotate.
- R3: Annotate each move using the schema in [pm-moves](../../context/wiki/pm-moves.md): inputs,
  process, outputs, judgment content, effort share, delegation level, risk, delivery touchpoint,
  frequency.
- R4: Cover the moves that touch delivery (shaping into specs, acceptance) in enough depth to
  define the spec contract with SDD (Q-008, C8).
- R5: Describe what each move needs and produces, not who happens to do it today, so the taxonomy
  holds as delegation shifts.

## Constraints
- Inherits C1–C8. C5 matters most here: nothing proprietary goes into the repo.

## Assumptions
- The moves split into judgment moves and context-bound moves: H-003 and H-006 (hypotheses).
- One taxonomy can serve four analyses (effort, first moves, context ontology, spec contract):
  agent synthesis, untested.

## Non-goals
- A complete ontology of all enterprise work.
- Using or reproducing the enterprise's proprietary lifecycle taxonomy.
- Deciding how moves' inputs and outputs are stored. That's the data structure (goal 006, Q-015).

## Open
- How big is a move? Are moves universal, or specific to an enterprise?
- Where do the judgment moves end up (Q-011), and does the taxonomy need to cover them in the same
  depth?
- Do moves operate on products, projects, or something else (Q-015)?
- Will adoption eventually need a mapping from this taxonomy to the enterprise's lifecycle? Not now.
