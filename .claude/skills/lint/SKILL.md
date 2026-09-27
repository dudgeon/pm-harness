---
name: lint
description: Reconcile the whole project and check its health. Covers cross-goal implications, conflicts, stale decisions and hypotheses, gaps in the deliverables ladder, and wiki hygiene, going beyond the latest changes. Use when asked to lint, audit, health-check, or review the project, or periodically.
---

# /lint

Lint runs the same reconciliation loop as `/ingest` (see CLAUDE.md), but across **the whole
project**. Ingest follows one new item outward; lint looks at how everything fits together,
including connections that nobody triggered. It's longer-running, so take the time.

## 1. Catch up

Find everything that changed since the last lint entry in `project/context/wiki/log.md`, using git
history where it's available. Run the reconciliation loop on anything that hasn't been traced yet.
If the inbox has items waiting, ingest them first.

## 2. Reconcile across the project

Read every goal whose status isn't `done` or `dropped`, plus the vision, the constraints, the
decisions, and the wiki. Look for:

- **Cross-goal implications** that haven't been traced yet: findings, decisions, or finished
  deliverables in one goal that touch another goal's requirements, assumptions, or deliverables.
  Add `from:` tasks to the affected goals.
- **Contradictions** between goals, between goals and constraints or priors, between wiki pages,
  or between the wiki and priors. Flag conflicts involving priors; don't resolve them.
- **Decisions and hypotheses:**
  - revisit triggers that have fired;
  - invalidated hypotheses that decisions or assumptions still rest on (follow the links and add
    tasks);
  - untested hypotheses with no test planned;
  - resolved questions with no matching `DEC-NNN`;
  - choices visible in the files that were never recorded as decisions.
- **Unfounded assertions:** claims stated as fact without a source, and assumptions with no label.
- **Vagueness that now blocks work:** `active` goals with no definition of done; constraints marked
  `?` that a goal depends on.

## 3. Health

- **Ladder:** goal deliverables that don't ladder up; project deliverables that nothing feeds;
  mismatches between `ladders_to` and a goal's `deliverables.md`.
- **Tasks:**
  - `active` goals with no open tasks;
  - `done` goals with open tasks;
  - `blocked:` tags pointing at resolved questions;
  - `from:` tasks whose source was later reversed;
  - a stale `project/tasks.md` (run `/rollup`).
- **Wiki:** orphan pages; broken links; claims with no source; goal-context pages that now matter
  to more than one goal (promote them); stale pages.
- **Open questions** that have gone quiet.

## 4. Close out

Apply the "freely do" changes, and propose everything else. Run `/rollup` if you added tasks.
Append an entry to `log.md` with the scope checked, the tasks created (goal → task), the questions
raised, and the proposals made. In the report, group findings as **blocking**, **should fix**, and
**nit**.
