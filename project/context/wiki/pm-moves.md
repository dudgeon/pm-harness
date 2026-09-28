# PM moves (working notes)

> Seed material for Q-004. The taxonomy itself is a goal deliverable; this page holds what's known
> so far and a proposed shape for it.

## Geoff's proto-map

This comes from the [thesis note](../inbox/_processed/2026-09-27-thesis-and-direction.md). It's
grounded as Geoff's current model. The split between the two groups is itself a hypothesis (H-003,
H-006).

**Judgment moves.** People should spend more of their effort here (H-006):
- identifying problems (empathy, business judgment)
- identifying solutions (taste)
- accepting built solutions and releasing them to customers (business rigor, well-managed rigor)

**Context-bound moves.** Geoff believes most effort goes here today (H-003), mostly on
re-discovering constraints and managing dependencies (H-004):
- supporting in-market solutions
- shaping intent
- managing delivery
- the intent-refinement loop
- managing dependencies

## The moves as a loop (agent sketch)

1. **Problem identification.** Judgment: empathy, business judgment.
2. **Solution identification.** Judgment: taste.
3. **Shaping intent** into a spec. Context-bound.
4. **Delivery** via SDD (DEC-010). For the PM this is context-bound: managing delivery and
   dependencies. The intent-refinement loop runs between 3 and 4.
5. **Acceptance.** Judgment: rigor.
6. **Release.** Judgment: rigor.
7. **In-market support.** Context-bound. Its signals feed back into 1.

The judgment moves are the turns: deciding what problem, what solution, and whether to ship. The
context-bound moves are the straights, where decided intent moves through the organization.
Geoff sees the refinement loop between 3 and 4 as the place where constraints get re-discovered.

## Proposed annotation schema (agent proposal)

For each move, record:

| Field | What it captures | Feeds |
|---|---|---|
| Inputs | What the move consumes, and which of it is context the layer must hold | context ecosystem (Q-007) |
| Process | The steps, and who does what today | harness design |
| Outputs | What the move produces, and which of it becomes context the layer gains | context ecosystem (Q-007) |
| Judgment content | Empathy, business judgment, taste, rigor, or none | first moves (Q-006), terminal state (Q-011) |
| Effort share | The share of PM effort it takes today | value case (Q-005) |
| Delegation level | Today's level, and the ceiling given current context ([levels](path.md#delegation-levels)) | traces (H-005), first moves |
| Risk | Does it affect customers? Is it relevant to controls? | first moves, controls (Q-014) |
| Delivery touchpoint | Does it produce a spec, or consume a build? | spec contract (Q-008) |
| Frequency | How often it happens | first moves (more learning loops) |

**Why one taxonomy for four jobs.** The same list of moves can be the unit of analysis for four
questions:
- effort (Q-005)
- choosing the first moves (Q-006)
- the context ontology (Q-007): inputs are the context the layer must hold, and outputs are the
  context it gains
- the spec contract (Q-008)

Keeping one taxonomy keeps those four analyses consistent. This is agent synthesis.

## Starting points

**Direction (DEC-012).** Build from industry best practice and from scratch, not from the
enterprise's own lifecycle taxonomy. That taxonomy is proprietary and predates AI. In Geoff's
assessment, its step definitions are vague, some steps have false precision, and others lack
detail. Treat those as flaws to avoid.

**Industry frameworks to survey.** None of these have been read for this project yet, so verify
them before relying on them.
- Pragmatic Institute's framework, SVPG's product operating model, Shape Up's shaping,
  continuous-discovery practice, and jobs-to-be-done.
- The PM / product owner split in scaled-agile frameworks such as SAFe, which is common in large
  enterprises.

**Outside breakdowns** from the [beacon scan](../inbox/_processed/2026-09-27-beacon-scan.md):
- **Spec Kit's idea assessment** (July 2026, §8): intake, research, define, shape, decide. It ends
  in go, needs-clarification, or kill. It's a breakdown of shaping.
- **AWS AI-DLC** (§9): intent → requirements → units of work → code, with human approvals logged.
  It covers the move from shaping into delivery.
- **Agents for PM moves.** LinkedIn has trust, growth, research, and analyst agents (§1). Atlassian
  has PRD, theme, and customer agents (§2). Together they show which moves beacons automate first.
- **Ramp's factory loop** ([Ramp teardown](../../goals/004-beacon-teardowns/teardowns/ramp/vision.md),
  2026-09): identify → define → build → coordinate → improve, with an agent for each bottleneck.
  It adds two things our sketch doesn't have yet:
  - **Coordinate** is a step of its own: status, Q&A, launch communications.
  - **Acceptance testing** is automated (Testo), while the decision to accept stays human.

  Ramp's first automated moves were context-bound Q&A (data, product, customer signal), which fits
  H-003. Its handoff from shaping to delivery is "the next contract": evidence, requirements written
  for agents, and a working prototype (Q-008).
- **Ramp's product-shaping skill** (read in full in round 2,
  [Glass PRD](../../goals/004-beacon-teardowns/teardowns/ramp/prd-glass.md), part B) breaks moves 1–3
  down concretely:
  - **Frame:** seven questions, and a gate: the problem must fit in one sentence before research
    starts.
  - **Research:** streams the PM chooses, run in parallel. Each writes a file, held to an evidence
    bar.
  - **Shape:** requirement IDs tied to evidence, closed questions with their sources, and a
    seven-section spec that stops at "specific enough to prototype."

  At Ramp these moves are a relay across tools, not one agent's job: discovery in VOTC, framing in
  Glass or Claude Code, the prototype in Inspect, the record in Notion
  ([intent-shaping](../../goals/004-beacon-teardowns/teardowns/ramp/intent-shaping.md)).

- **Outside move definitions from the second pass** ([landscape](../../goals/004-beacon-teardowns/landscape.md), 2026-09-28):
  - **Critique a spec.** Uber's PRD Evaluator sets its depth by risk, separates critical
    requirements from optimizations, and returns write-ready fixes. LinkedIn runs a spec past
    critique agents for each craft (trust, growth, research, analyst).
  - **Decide.** Spec Kit's idea assessment ends in go, needs-clarification, or kill. Claire Vo
    labels each commitment a probe, an experiment, or a promise.
  - **Define AI features by evals**, not prose: Box, Block's Moneybot, Atlassian, Anthropic.
  - **Clarify.** The tools have converged on one pattern: a plan step before build, then questions
    one at a time with a recommended answer, logged with dates in the spec.

## Open

- How big is a "move"?
- Are the moves universal, or specific to an enterprise?
- Is "managing dependencies" a move of its own, or part of several others?
