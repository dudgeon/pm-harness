---
id: 002
title: Evolve project-scaffold-v1
status: draft
created: 2026-09-27
updated: 2026-09-27
ladders_to: []   # none directly; supports how the project is run (DEC-003), and feeds 001 via H-001
---

# 002 · Evolve project-scaffold-v1

## Why
This project runs on project-scaffold-v1. Keeping it working, and improving it based on friction we
hit, makes the project easier to run. What we learn may also inform the harness design (H-001).

## Definition of done
_Vague:_ This is ongoing. Each significant version is snapshotted as a durable work product.

## Requirements
- R1: Snapshot each version of the scaffold. A snapshot is a markdown file describing its artifacts,
  with a link to the commit it describes.
- R2: Serve the design aims in README.md (drop-in, guidance not a workflow engine, one
  reconciliation loop, epistemic hygiene, initiative that grows as the project gets clearer).

## Assumptions
- The scaffold is distinct from the harness: grounded (DEC-003)

## Constraints
- Inherits C1–C4.

## Non-goals
- Designing the PM harness; that's goal 001.

## Open
- What counts as a version bump (v1 → v2)?
- Should the scaffold eventually live somewhere other than this repo?
