# Snapshot: project-scaffold-v1

- **Commit:** [`a6f5199`](https://github.com/dudgeon/pm-harness/tree/a6f519944b6f2dc522ecd5b15a8d3bf94f866271) (tag `project-scaffold-v1`)
- **Date:** 2026-09-27
- **Origin:** [hand-drawn sketch](../../../priors/origin-sketch.jpg). Decisions: DEC-003 (the scaffold is separate from the harness) and DEC-004 (its name)

This is a markdown file structure plus Claude Code skills for running one project with an agent.
The files carry the memory, so any fresh session can pick up where the last one left off.

## Artifacts

| Artifact | Purpose |
|---|---|
| `CLAUDE.md` | Agent guidance: a map, the trust order, the reconciliation loop, what to do freely vs. ask first vs. never do, how initiative grows as the project gets clearer, and conventions |
| `README.md` | The scaffold's five design aims |
| `project/vision.md` | Why the project exists and what winning looks like |
| `project/constraints.md` | Project constraints `C1…`, each with a firmness (firm, soft, or ?) and a source |
| `project/deliverables.md` | Project deliverables `D1…`; goal deliverables ladder into these |
| `project/decisions.md` | Decision register `DEC-NNN` (basis, alternatives, revisit trigger) and hypotheses `H-NNN` (test, evidence) |
| `project/open-questions.md` | Contradictions and unresolved questions `Q-NNN`; each resolves into a decision |
| `project/tasks.md` | Generated rollup of all goal tasks |
| `project/priors/` | Context outside the project (human-written or linked). The agent may propose changes but never makes them |
| `project/context/inbox/` | Raw, unfiled material; moved to `_processed/` once ingested, and kept for provenance |
| `project/context/wiki/` | Agent-maintained learnings shared across goals (`index.md`, append-only `log.md`) |
| `project/goals/NNN-slug/` | `goal.md` (status, definition of done, requirements, assumptions, non-goals), `deliverables.md`, `tasks.md`, and `context/` for goal-specific learnings |
| `project/goals/_template/` | Starting files for a new goal |

## Skills (`.claude/skills/`)

| Skill | Role |
|---|---|
| `/next` | Offers 3–5 ranked options for moving the project forward; how much initiative it takes depends on how well-defined the project is |
| `/ingest` | Runs the reconciliation loop on new material (the inbox, or something the user just provided) |
| `/lint` | Runs the reconciliation loop across the whole project, plus health checks |
| `/new-goal` | Turns a vague ask into a draft goal, interviewing the user to sharpen it |
| `/rollup` | Regenerates `project/tasks.md` and checks the deliverables ladder |

## Key mechanics

- **Trust order:** priors > vision, constraints, and goals > wiki > inbox. At every level, grounded
  claims outrank hypotheses.
- **Reconciliation loop:** place the new information, label it (grounded or hypothesis), trace its
  implications (adding `from:NNN` tasks to the goals it affects), surface conflicts, sharpen, report.
- **Vague to sharp:** goals and constraints start fuzzy and get sharpened as the work needs them to be.
- **Contradictions** are logged in `open-questions.md`, and raised immediately if they block work.

## Known gaps at this version

- It hasn't been used on real work yet, so there are no `scaffold-friction` notes so far.
- There's no criterion yet for what makes a new version (see goal 002, Open).
