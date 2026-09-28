---
id: 004
title: Beacon teardowns
status: active
created: 2026-09-27
updated: 2026-09-27
ladders_to: [D5, D2]
---

# 004 · Beacon teardowns

## Why
Several "beacons" (e.g., Ramp's Glass) are making headway
([thesis note](../../context/inbox/_processed/2026-09-27-thesis-and-direction.md)). Learning how they
handle first moves, deployment, context, traces, and controls is cheaper than finding it all out
ourselves. This goal answers Q-009.

Geoff wants a high-fidelity read of each prioritized beacon: "basically a full complement of PRDs
for the main features and product vision for the overall product" (chat, 2026-09-27).

## Definition of done
For each prioritized beacon, a teardown that reconstructs its product as PM artifacts:
- a **product vision** for the whole
- a **PRD for each main feature**

Each should be as close to the real thing as public sources allow. Each teardown must also:
- cite every claim and label it (said / observed / inferred)
- read its subject through the common lens (R3)
- say what transfers (R4)

The goal also delivers a synthesis across beacons (004-D3). The goal is done when the prioritized
teardowns and the synthesis exist and Geoff has reviewed them. Ramp came first and sets the
template ([teardowns/ramp](teardowns/ramp/index.md)).

## Requirements
- R1: Use public information only (GC1).
- R2: Separate what a company *says* from what others have *observed*, and cite everything.
- R3: Read every teardown through the same lens: the three path axes (first moves, deployment
  model, context approach) plus traces and controls.
- R4: Say what transfers to a regulated enterprise (C7), and what doesn't.
- R5: Reconstruct each prioritized beacon as a product vision plus one PRD per main feature, as
  close to the real thing as the evidence allows. Label inferred content, and list what the public
  record doesn't say (Geoff, 2026-09-27).
- R6: Map each feature to the PM moves it covers ([pm-moves](../../context/wiki/pm-moves.md)) and
  a delegation level ([path](../../context/wiki/path.md#delegation-levels)), so teardowns feed
  goals 003, 005, and 001.
- R7: Primary sources first:
  - Talks, first-party posts, and what's on screen in videos come first. Secondary summaries are
    leads to follow up.
  - Third-party material goes into the public repo only as digests with short quotes and links.
  - Full texts and transcripts stay local, in `context/inbox/_local/`, which git ignores.

## Constraints
- GC1: Publicly available information only (Geoff, thesis note).
- Inherits C1–C8.

## Assumptions
- Public accounts represent what beacons actually do well enough to learn from: a weak hypothesis,
  since companies tend to publish their successes.
- Beacons' numbers are self-reported, and their definitions drift between sources. The Ramp
  teardown found Inspect's share of PRs quoted anywhere from 30% to 76.5%, under different
  definitions. Treat numbers as ranges, and track them over time.

## Non-goals
- A market study, or choosing a vendor.
- Non-public information about any company.

## Open
- How many teardowns are enough?
- Which beacons come after the first five?
- Should the other deep teardowns get Ramp's full treatment (vision plus PRDs), or a lighter version
  scaled to the evidence? (Ramp had unusually rich public material.)
- Beacons' tools have "a shelf life of weeks" (Ramp, S14 in the teardown). How do we keep
  teardowns current, and when does one count as stale?
