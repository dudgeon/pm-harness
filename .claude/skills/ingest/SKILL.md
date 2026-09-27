---
name: ingest
description: Reconcile new material into the project. Works on inbox items, or on facts, notes, or documents the user just provided. Use when asked to ingest, file, or process something, or when the user drops in new information.
---

# /ingest

Runs the reconciliation loop from CLAUDE.md on **new material only**. What counts as new:

- If the user provided something in this session, use that.
- Otherwise, use each item in `project/context/inbox/`, skipping `README.md` and `_processed/`.

For each item:

- **Place it.** A learning that matters to more than one goal goes in the project wiki. A learning
  specific to one goal goes in that goal's `context/`. Put the general part and the specific part
  in their own places and link them. Prefer updating an existing, topic-shaped page over creating
  a new one. Update the relevant `index.md` and cite the source.
- **Label, trace, surface, sharpen.** Do these as CLAUDE.md describes, including adding tasks to
  every goal the item affects.
- **Close out.** Move processed inbox items to `inbox/_processed/`. If material came from chat and
  is evidence, save it there as the source first. Append an entry to `project/context/wiki/log.md`.

Trace implications as far as the new material reaches; that's the scope. Leave project-wide
health checks to `/lint`.

`scaffold-friction` items go to the context of the goal that evolves project-scaffold-v1, if there
is one; otherwise they go to the project wiki. Also note any implications for harness design
(H-001).
