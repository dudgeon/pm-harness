# Decision register

Every project decision that matters, and what it rests on. Decisions are never deleted. When a
decision changes, a new entry supersedes the old one.

## Grounded vs. hypothesis

Every claim a decision rests on is labeled with one of:

- **grounded**: backed by a citable source, such as a prior, data, research, a user's stated
  decision, or a shipped result. Link the source.
- **hypothesis**: believed, but not yet shown to be true. It gets an `H-NNN` ID below and a way
  to test it.

A decision that rests on a hypothesis is allowed, since it's often necessary. It must say so, and
it gets re-examined when the hypothesis is tested.

## Decisions

Format:

```
### DEC-NNN: title
- status: active | superseded by DEC-NNN | reversed
- date: YYYY-MM-DD · decided by: <who>
- scope: project | goal NNN
- decision: <what was decided>
- basis:
  - grounded: <claim> (<source>)
  - hypothesis: H-NNN
- alternatives considered: <options that were rejected, and why>
- revisit if: <a trigger, e.g. "H-001 invalidated">
- from: Q-NNN (if it resolved an open question)
```

### DEC-001: Dogfood this repo's structure as harness v0
- status: superseded by DEC-003
- date: 2026-09-27 · decided by: Geoff
- scope: project
- decision: This project runs on the `project/` structure. That structure is also one of the
  candidate harness designs goal 001 evaluates.
- basis:
  - grounded: Geoff's decision at kickoff (see [origin sketch](priors/origin-sketch.jpg))
  - hypothesis: H-001
- alternatives considered: treating the structure as plain repo scaffolding, separate from
  the product
- revisit if: H-001 is invalidated

### DEC-002: Use Claude Code as the v0 agent layer
- status: active
- date: 2026-09-27 · decided by: Geoff
- scope: project
- decision: The agent layer is CLAUDE.md plus `.claude/skills/` (constraint C1).
- basis:
  - grounded: Geoff's decision at kickoff
- alternatives considered: plain markdown with no skills; runtime-agnostic AGENTS.md
- revisit if: goal 001 selects a design with a different runtime

### DEC-003: The scaffold is separate from the harness
- status: active
- date: 2026-09-27 · decided by: Geoff
- scope: project
- decision: The `project/` file structure and its skills make up a distinct, unnamed artifact.
  It is not the PM harness, and not a v0 of it. The harness is likely a deployed agent or
  orchestrator. We keep the scaffold, manage this project with it, and give it a proper name
  (Q-002). Evolving the scaffold may become its own goal.
- basis:
  - grounded: Geoff's correction on 2026-09-27
  - hypothesis: H-001 (using the scaffold informs the harness design)
- alternatives considered: DEC-001, which treated the scaffold as harness v0
- revisit if: the harness design converges on the scaffold after all

### DEC-004: Name the scaffold project-scaffold-v1
- status: active
- date: 2026-09-27 · decided by: Geoff
- scope: project
- decision: The `project/` structure and its skills are called **project-scaffold-v1**. The name is
  descriptive rather than catchy, and the version suffix leaves room for it to evolve.
- basis:
  - grounded: Geoff's choice on 2026-09-27
- alternatives considered: catchy names (Groundwork, Cairn, Plumbline, Bearings); descriptive
  names (goal-structured project wiki, agent-maintained project record, project context tree)
- revisit if: the scaffold changes enough to warrant v2
- from: Q-002

## Hypotheses

Format:

```
### H-NNN: claim
- status: untested | testing | supported | invalidated
- raised: YYYY-MM-DD · by: <who, or which file/goal>
- test: <what evidence would support or invalidate it>
- evidence: <links, as it arrives>
- decisions resting on it: DEC-NNN
```

### H-001: Running this project on project-scaffold-v1 produces evidence that is useful for designing the harness
- status: untested
- raised: 2026-09-27 · by: kickoff
- test: `scaffold-friction` notes and wiki learnings lead to concrete harness requirements or evaluation criteria in goal 001
- evidence: (none yet)
- decisions resting on it: DEC-003 (formerly DEC-001)
