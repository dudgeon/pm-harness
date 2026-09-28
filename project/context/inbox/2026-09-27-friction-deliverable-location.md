---
source: agent, 2026-09-27 session (the Ramp teardown)
goal: 002
tags: [scaffold-friction]
---

# Goal deliverables have no standard home

Each goal is putting its deliverables in a different place:

| Goal | Deliverable | Where it lives |
|---|---|---|
| 002 | Snapshot | `snapshots/` |
| 004 | 004-D1, the landscape scan | `context/` |
| 004 | 004-D2, the teardowns | `teardowns/` |

The goal template has only `context/`, which the scaffold describes as "context specific to this
goal, filed by /ingest." A deliverable is an output, not context, so filing one there blurs the two.

Minor, but it makes deliverables harder to find across goals, and `/rollup` can't check them
consistently.

**Options:**
- Add a `deliverables/` folder to the goal template.
- Allow any location, as long as `deliverables.md` links to it.

**Implication for the harness (H-001, Q-015).** Artifacts (specs, reports, teardowns) and context
(learnings, evidence) are different entity types with different lifecycles. A PM agent's data model
probably needs both.
