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

### DEC-005: Evolving the scaffold is goal 002, and each version gets a snapshot
- status: active
- date: 2026-09-27 · decided by: Geoff
- scope: project
- decision: Goal 002 owns the evolution of project-scaffold-v1. Each version is saved as a
  snapshot: a markdown file describing its artifacts, linked to a commit. v1 is commit `a6f5199`
  (tag `project-scaffold-v1`).
- basis:
  - grounded: Geoff's direction on 2026-09-27
- alternatives considered: no dedicated goal (evolving it informally)
- revisit if: the scaffold moves out of this repo
- from: Q-003

### DEC-006: Keep the repo generic about the enterprise
- status: active
- date: 2026-09-27 · decided by: Geoff
- scope: project
- decision: The repo is public. It describes the target environment only as "a large, complex,
  regulated enterprise," with no company, industry, or internal facts. Enterprise-specific material
  is either summarized generically or kept out of the repo (constraint C5).
- basis:
  - grounded: the repo is public on GitHub (checked 2026-09-27)
  - grounded: Geoff's choice on 2026-09-27
- alternatives considered: naming the industry only; making the repo private and being specific
- revisit if: the repo goes private, or the generic framing blocks work that needs specifics

### DEC-007: Develop toward a shared, persistent, deployed PM agent for a large regulated enterprise
- status: active
- date: 2026-09-27 · decided by: Geoff
- scope: project
- decision: The harness we're developing toward is a shared, persistent, deployed product-manager
  agent. It helps with the major moves of a product manager at a large, complex, regulated
  enterprise, and eventually drives them with decreasing human steering. Its first users are the PM
  function, including product owners. Builders of any title come later, if the roles converge
  (H-008).
- basis:
  - grounded: Geoff's direction ([thesis note](context/inbox/_processed/2026-09-27-thesis-and-direction.md))
  - hypothesis: H-002, H-003, H-006
- alternatives considered: standardized skills in each PM's own Claude Code instance as the end
  state (treated as a stop along the way, not the destination); builders as the first users
- revisit if: H-002 is invalidated
- from: vision.md "Open" (who is the user?); partly answers Q-001

### DEC-008: Adoption must be earned
- status: active
- date: 2026-09-27 · decided by: Geoff
- scope: project
- decision: Plan as if the harness gets no mandated rollout. It has to be so clearly better than
  the status quo that people choose it, and it spreads inside the enterprise on its merits
  (constraint C6).
- basis:
  - grounded: Geoff's direction on 2026-09-27
- alternatives considered: a top-down rollout
- revisit if: the adoption model changes
- consequences: each user needs value before any organization-level payoff (H-011, Q-013). The
  first moves need to be ones where the gain is obvious to the person doing them (Q-006).

### DEC-009: Working assumption: the terminal state is a fully synthetic PM
- status: active (working assumption)
- date: 2026-09-27 · decided by: Geoff
- scope: project
- decision: Plan as if the end state is a fully synthetic PM agent. The terminal state is
  genuinely unknown. The path runs through stops: PMs casually using a chat assistant, then PMs
  using standardized shaping skills in their own Claude Code instance, then a shared deployed agent,
  then further stops as steering decreases ([path](context/wiki/path.md)).
- basis:
  - grounded: Geoff's direction ("let's assume") in the [thesis note](context/inbox/_processed/2026-09-27-thesis-and-direction.md)
- alternatives considered: an augmented human PM as the end state
- revisit if: Q-011 (where the judgment moves end up) resolves against it, or accountability
  requirements in a regulated enterprise rule it out

### DEC-010: Working assumption: delivery is agentic, via spec-driven development
- status: active (working assumption)
- date: 2026-09-27 · decided by: Geoff
- scope: project
- decision: Assume software delivery happens through agentic spec-driven development (SDD), which
  needs well-defined specs. PM moves that feed delivery must produce specs SDD can consume, and
  acceptance consumes what SDD builds (constraint C8, Q-008).
- basis:
  - grounded: Geoff's direction ("let's assume") in the [thesis note](context/inbox/_processed/2026-09-27-thesis-and-direction.md)
- alternatives considered: none discussed
- revisit if: the enterprise's delivery model turns out differently, or SDD proves unworkable

### DEC-011: Build context up iteratively, not up front
- status: active
- date: 2026-09-27 · decided by: Geoff
- scope: project
- decision: Don't try to gather and record the enterprise's knowledge up front. Get the
  architecture and workflows right, then build context through repeated loops: agents orchestrate
  discovery, humans carry it out, and results are validated and governed as they're added
  ([context layer](context/wiki/context-layer.md)).
- basis:
  - grounded: Geoff's direction in the [thesis note](context/inbox/_processed/2026-09-27-thesis-and-direction.md)
  - hypothesis: H-007
- alternatives considered: comprehensive knowledge capture up front (judged impractical)
- revisit if: H-007 is invalidated

### DEC-012: Build the PM moves taxonomy from industry practice and original work
- status: active
- date: 2026-09-27 · decided by: Geoff
- scope: goal 003
- decision: Build the taxonomy from industry best practice and from scratch. Don't base it on the
  enterprise's own lifecycle taxonomy.
- basis:
  - grounded: Geoff's direction on 2026-09-27. The enterprise's taxonomy is proprietary (C5), and
    it predates AI. In Geoff's assessment, its step definitions are vague, some steps have false
    precision, and others lack detail. Goal 003 treats those flaws as things to avoid.
- alternatives considered: adapting the enterprise's existing taxonomy
- revisit if: adoption turns out to need a mapping to the enterprise's lifecycle

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
- evidence:
  - 2026-09-27 (for, by analogy): the context-building loop in DEC-011 has the same shape as
    the scaffold's reconciliation loop. The agent orchestrates, a human discovers and
    validates, and a trust order governs. That makes the scaffold a small-scale test bed for it
    ([context layer](context/wiki/context-layer.md)).
  - 2026-09-27 (for): the first friction note, about confidential context in a public repo,
    points to a harness requirement: an enterprise context layer needs access tiers
    ([note](context/inbox/_processed/2026-09-27-friction-private-context.md)).
- decisions resting on it: DEC-003 (formerly DEC-001)

### H-002: A shared harness that builds up governed context beats individual local AI use
- status: untested
- raised: 2026-09-27 · by: Geoff ([thesis note](context/inbox/_processed/2026-09-27-thesis-and-direction.md))
- claim: Over time, moving PMs from local AI instances (or no AI) to a shared harness produces
  benefits that individual use can't. The harness builds trustworthy context into an increasingly
  complete, credible context layer, and uses agents to drive PM moves under human steering. The
  expected benefits are H-004, H-005, and H-006.
- test: run the same moves two ways, with standardized skills in individual instances and with a
  shared harness. Compare context reuse across PMs, how often constraints get re-discovered,
  effort per move, and delegation level.
- evidence:
  - 2026-09-27 (for, weak: self-reported and read through secondary summaries): Ramp built its
    internal harness, Glass, after individual AI-tool adoption reached about 99%. At that point
    "most people were stuck" on setup, with no way to share what they learned. Ramp's answer was
    a shared harness with shared skills and memory
    ([beacon scan](context/inbox/_processed/2026-09-27-beacon-scan.md), §0).
  - 2026-09-27 (mixed, self-reported, from primary sources): Ramp's setup is split.
    - Glass is per-person and local: shared skills, but memory kept per user, and no central
      traces.
    - Ramp's other agents are shared services on one formal record: Inspect, VOTC, Gadget, Ramp
      Research.
    - Ramp credits the gains to the shared parts ("one person's breakthrough should become
      everyone's baseline").

    ([Ramp teardown](goals/004-beacon-teardowns/teardowns/ramp/index.md))
  - 2026-09-27 (mixed, round 2: self-reported, plus screenshots):
    - For the "shared" half: once connectors and skills were set up centrally and shared, Glass
      went from 3 to 976 weekly users in four weeks, without a mandate.
    - Against the "governed context" half, Ramp offers no support:
      - Glass keeps memory per user and nothing centrally.
      - Internal-tool governance is "yeah, chaos."
      - A Ramp designer calls the missing project "source of truth" a blocker.

    ([Glass](goals/004-beacon-teardowns/teardowns/ramp/prd-glass.md),
    [intent-shaping](goals/004-beacon-teardowns/teardowns/ramp/intent-shaping.md))
- decisions resting on it: DEC-007

### H-003: Most enterprise PM effort goes to work that doesn't need creativity or judgment
- status: untested
- raised: 2026-09-27 · by: Geoff ([thesis note](context/inbox/_processed/2026-09-27-thesis-and-direction.md))
- claim: Most PM effort at large enterprises is misspent on supporting in-market products,
  shaping intent, managing delivery, and intent-refinement loops. Those loops mostly re-discover
  constraints and manage dependencies.
- test: an effort baseline measured against the moves taxonomy (Q-004, Q-005), drawing on Geoff's
  observations, interviews or surveys with PMs, and published surveys of how PMs spend their time.
  Internal calendar and time data isn't available (Geoff, 2026-09-27), so treat the results as
  directional.
- evidence:
  - 2026-09-27 (for, weak: self-reported, and not from a regulated enterprise): Ramp's CPO says:
    - AI now fully answers 85% of the questions asked of PMs.
    - PMs "naturally gravitate towards the small reactive things."

    Both suggest a large share of PM attention had gone to context-bound work
    ([Gadget](goals/004-beacon-teardowns/teardowns/ramp/prd-gadget.md),
    [autonomous loop](goals/004-beacon-teardowns/teardowns/ramp/prd-autonomous-loop.md)).
- decisions resting on it: DEC-007 (the value case)

### H-004: Missing context, not the work itself, drives that effort
- status: untested
- raised: 2026-09-27 · by: Geoff (implied by "re-discovering constraints"; made explicit by the agent)
- claim: Much of the effort in H-003 goes to finding out things someone in the organization
  already knows, such as constraints, dependencies, policies, and history. That knowledge is tacit
  and held by SMEs. Governed stores that agents can access would cut the cost.
- test: in the effort baseline, measure the share of effort spent finding or re-discovering
  existing knowledge, and track how often the same constraint is re-discovered across initiatives.
- evidence:
  - 2026-09-27 (for, weak: self-reported): Ramp's questions were answerable from the formal record.
    That's 85% of the questions asked of PMs, and 85% of "tough product questions" for an earlier
    agent. So the knowledge already existed, and finding it was the cost. Ramp's first step was to
    consolidate its knowledge "so that both humans and AI could operate from the same source of
    truth" ([Gadget](goals/004-beacon-teardowns/teardowns/ramp/prd-gadget.md)).
- decisions resting on it: DEC-011

### H-005: Persisted agent traces let us understand and influence AI fluency and delegation
- status: untested
- raised: 2026-09-27 · by: Geoff ([thesis note](context/inbox/_processed/2026-09-27-thesis-and-direction.md))
- test: from pilot traces, can we tell each user's delegation level for each move
  ([delegation levels](context/wiki/path.md#delegation-levels))? And do interventions informed by
  the traces, such as coaching, defaults, or templates, raise it?
- evidence:
  - 2026-09-27 (for the "understand" half): Anthropic measures delegation from real traces.
    New users auto-approve about 20% of the time and experienced users over 40%, and experienced
    users also interrupt more ([Measuring AI agent autonomy in practice](https://www.anthropic.com/research/measuring-agent-autonomy),
    2026-02-18). Its AI Fluency Index detects 11 of 24 fluency behaviors in conversations
    ([AI Fluency Index](https://www.anthropic.com/research/AI-fluency-index), 2026-02-23). Both
    came from the [beacon scan](context/inbox/_processed/2026-09-27-beacon-scan.md), §13.
  - 2026-09-27 (open on the "influence" half): vendor dashboards (Atlassian, Glean, Microsoft)
    track adoption and cost, not fluency or delegation. No public evidence was found that
    interventions informed by traces raise delegation (beacon scan, "Gaps").
  - 2026-09-27 (design evidence, self-reported): Ramp's two platforms made opposite choices.
    - **Inspect** traces every session end to end: 800k sessions and 30M tool calls kept in a data
      lake. It ties each PR to its session, and Ramp uses the traces to review and tune the
      platform.
    - **Glass** captures no central traces.

    Neither publishes measures of fluency or delegation. Ramp's leaderboard counts usage
    (sessions, skills, apps)
    ([Inspect](goals/004-beacon-teardowns/teardowns/ramp/prd-inspect.md),
    [Glass](goals/004-beacon-teardowns/teardowns/ramp/prd-glass.md)).
  - 2026-09-27 (for the "influence" half, weak: said, round 2):
    - Ramp's CEO credits Inspect's adoption less to the agent than to its visible sessions. There's
      a live board where anyone can "follow along and see what other people are doing and spark new
      ideas and get proficient faster."
    - That's traces used to raise fluency, but no measure has been published.
    - Glass meters spend per skill, but not session content.

    ([Inspect](goals/004-beacon-teardowns/teardowns/ramp/prd-inspect.md), requirement I14)
  - 2026-09-27 (for the "understand" half, med: first-party):
    - Ramp Labs turns Inspect traces into "work items," each with one objective and one outcome.
    - It classifies about 250,000 of them into 30 categories, to tie AI spend to the work done.
    - That's traces used to understand *what* AI is doing, which is a step toward delegation by
      move.

    ([Ramp sources](goals/004-beacon-teardowns/teardowns/ramp/sources.md), S53)
  - 2026-09-28 (for, med: first-party, second pass):
    - Uber's ADR captures prompt, reasoning, tool call, and outcome across its agent clients, at
      50k+ sessions a day. Its finding: past about 50 approvals a session, oversight becomes a rubber
      stamp. That's traces used to redesign the human's role.
    - Coinbase recorded each PR's prompt, rules, and share of AI-written code, and used the data to
      evaluate prompt efficacy and defect rates.
    - Devin's Session Insights flags scope ambiguity in past sessions and returns improved prompts.

    ([landscape](goals/004-beacon-teardowns/landscape.md))
- decisions resting on it: (none yet)

### H-006: The harness shifts human effort toward judgment work
- status: untested
- raised: 2026-09-27 · by: Geoff ([thesis note](context/inbox/_processed/2026-09-27-thesis-and-direction.md))
- claim: Over time, humans spend less effort shaping and delivering intent that's already been
  decided. They spend more on creativity and critical thinking: empathy and business judgment in
  identifying problems, taste in identifying solutions, and rigor in accepting built solutions and
  releasing them to customers.
- test: compare effort by move category before and after a pilot, against the H-003 baseline.
- evidence:
  - 2026-09-27 (for, weak: said): Ramp frames its agents as moving people toward judgment.
    - Senior engineers review only the high-risk 7% of PRs.
    - PMs automate the small loops so they can focus on "the big ones."
    - The CPO names a "tastemaker" track for PMs.
    - Ramp's ops lead describes the goal as "fewer low-stakes decisions, more high-stakes
      judgments."

    ([Ramp vision](goals/004-beacon-teardowns/teardowns/ramp/vision.md))
- decisions resting on it: DEC-007

### H-007: Iterative loops build enough context for automation, where up-front capture wouldn't
- status: untested
- raised: 2026-09-27 · by: Geoff ([thesis note](context/inbox/_processed/2026-09-27-thesis-and-direction.md))
- claim: Repeated loops of discovery and validation, orchestrated by agents and carried out by
  humans, will hill-climb to the context that full automation needs. Capturing the enterprise's
  knowledge up front is impractical.
- test: in a pilot domain, track context coverage and credibility over time, and the share of
  moves agents complete without a human supplying context. Compare the cost with past up-front
  knowledge-management efforts.
- evidence:
  - 2026-09-27 (for, weak: a third-party summary): LinkedIn's agents are told to write what they
    learn back into playbooks. The playbooks get InfoSec review, and every call is logged. That's
    a context-building loop running in production
    ([beacon scan](context/inbox/_processed/2026-09-27-beacon-scan.md), §1).
  - 2026-09-27 (an alternative design): Ramp doesn't use a loop that humans carry out. It rebuilds
    each user's memory automatically every 24 hours from Slack, Notion, Linear, and Calendar (beacon
    scan, §0). Goal 006 should weigh this against the loop in DEC-011.
  - 2026-09-27 (for, med: first-party): Ramp runs two context-building loops in production, both
    validated by humans.
    - **The product-Q&A agent.** Experts mark each answer, and a nightly agent turns wrong answers
      into doc updates. It reached "85% of all questions take no human in the loop."
    - **Ramp Research.** Reviewing each answer didn't scale, so domain owners now test the context
      layer instead.

    ([Ramp teardown](goals/004-beacon-teardowns/teardowns/ramp/index.md))
  - 2026-09-27 (correction to the bullet above, from primary sources): Glass's daily pipeline mines
    past sessions, Slack, Notion, and Calendar. Linear feeds only the initial memory. Memory v2 also
    lets users review suggestions. So Ramp's memory isn't purely automatic either
    ([Glass](goals/004-beacon-teardowns/teardowns/ramp/prd-glass.md)).
  - 2026-09-27 (for, med: first-party, round 2): Glass's lead describes one improvement loop for
    every agent Ramp builds:
    1. Curate basic context and tools.
    2. Ship to real users.
    3. Automatically surface the sessions that went wrong.
    4. Generate suggested fixes to the context.
    5. Have a human validate them before they go live.

    "Way more effective to put your energy into building the improvement loop than overthinking
    the perfect v1." The same pattern shows up in two other places:
    - Glass's memory agent proposes entries into an Approve/Dismiss queue.
    - The head of design built a taste skill the same way: output, feedback, update the skill,
      repeat.

    ([Ramp vision](goals/004-beacon-teardowns/teardowns/ramp/vision.md),
    [Glass](goals/004-beacon-teardowns/teardowns/ramp/prd-glass.md))
  - 2026-09-28 (for, med: first-party, second pass):
    - Meta's Organizational Second Brain turns expert corrections into reviewed diffs to its
      knowledge files, and each one joins a regression suite.
    - Shopify's River went from a 36% to a 77% merge rate because people wrote down what it lacked,
      not because models changed.
    - Box runs a weekly review of unresolved requests, which feeds human-reviewed fixes to its IT
      assistant's knowledge.
    - AWS AI-DLC's "learnings ritual" saves lessons to team or project memory after checking them
      against org rules.

    ([landscape](goals/004-beacon-teardowns/landscape.md))
- decisions resting on it: DEC-011

### H-008: PM, design, and engineering converge into "builders"
- status: untested
- raised: 2026-09-27 · by: Geoff (the thesis note shifts from "PMs" to "builders"; Geoff confirmed in chat that this is a hypothesis, not a starting assumption)
- test: watch who adopts the harness and for which moves, and what the beacons report (Q-009).
- evidence:
  - 2026-09-27 (for, weak: said): "Anyone at Ramp can now code."
    - September 2026: about 1,000 PRs in a month from non-engineers.
    - April 2026: 12% of human-initiated PRs, "thousands per month."
    - The CPO lets engineers and designers "wear that PM hat" as long as accountability is clear,
      and expects the crafts to converge.

    ([Inspect](goals/004-beacon-teardowns/teardowns/ramp/prd-inspect.md),
    [Ramp vision](goals/004-beacon-teardowns/teardowns/ramp/vision.md))
  - 2026-09-27 (for, weak: said, round 2):
    - Ramp's head of design: "designers writing code, writing specs; … PMs making prototypes."
    - PM postings say "everyone is a builder who owns problems end to end."
    - A procurement designer and her engineers push PRs together, and "product kind of like
      guides that process."

    Two qualifiers:
    - Ramp still names distinct sensitivities for each craft. Design brings "how do I want people
      to feel."
    - PMs pick up a new "air traffic control" job once everyone can ship.

    ([intent-shaping](goals/004-beacon-teardowns/teardowns/ramp/intent-shaping.md),
    [Ramp vision](goals/004-beacon-teardowns/teardowns/ramp/vision.md))
  - 2026-09-28 (mixed, second pass):
    - For:
      - Coinbase's CEO announced "one person teams" that combine engineer, designer, and PM.
      - Uber's Agentic Pods pair engineers with domain experts, with no PM named.
      - Anthropic's 30–40 PMs nearly all code.
      - LinkedIn renamed its APM program "Associate Product Builder."
    - Qualifiers:
      - Atlassian lets PMs commit code only where the codebase's risk allows.
      - Box's CEO expects PMs to survive as customer-facing specialists.
      - Salesforce says it has no clear answers yet on PM and designer roles.

    ([landscape](goals/004-beacon-teardowns/landscape.md))
- decisions resting on it: DEC-007 (who the later users are)

### H-009: Context and traces are the path-dependent assets; the runtime isn't
- status: untested
- raised: 2026-09-27 · by: agent (synthesis)
- claim: The costly path-dependence risks are where context builds up and whether traces get
  captured. A v1 that writes to a shared, governed store and saves traces from day one keeps later
  stops open, whatever its deployment model. Context stranded in individual instances, and traces
  that were never captured, can't be recovered cheaply.
- test: in the beacon teardowns, check whether anyone had to migrate context or regretted missing
  traces. Estimate the migration costs between stops ([path](context/wiki/path.md)).
- evidence:
  - 2026-09-27 (consistent with, weak): across the beacons, procedural context lives in versioned,
    reviewed files that don't depend on any one runtime. Examples are Ramp's Dojo, LinkedIn's
    CAPT, Tessl, AWS steering files, and Spec Kit's constitution
    ([beacon scan](context/inbox/_processed/2026-09-27-beacon-scan.md), summary).
  - 2026-09-27 (for, med: first-party):
    - **Ramp Research.** Its interface was retired within months. Its context layer ("an incredibly
      valuable technical asset") moved into skills.
    - **Glass.** It never captured central traces, and its team says it now can't tell skill owners
      which skills work. That's the cost of traces never captured.
    - **Inspect.** It captured everything and mines it.

    ([Ramp teardown](goals/004-beacon-teardowns/teardowns/ramp/index.md))
  - 2026-09-27 (for, med: first-party, round 2): the method outlived its host.
    - Ramp's PM shaping skill ran in Claude Code in March. By September the CPO placed define in
      Glass.
    - Ramp Research ships as "a skill bundle that we make available in different harnesses," both
      Inspect and Glass.
    - Glass itself is called "provider agnostic."
    - The host may change again. Glass's lead left, and Ramp now provisions about 2,000 employees
      into Claude's own apps.

    ([intent-shaping](goals/004-beacon-teardowns/teardowns/ramp/intent-shaping.md))
  - 2026-09-28 (for, med: second pass):
    - Skills became portable across hosts. Spec Kit, BMAD, and AI-DLC each install into several
      agents.
    - The shell is becoming a commodity. Since 2026-09-16, Claude offers most of Glass's features as
      a vendor product, and Glass's creator is building a model-agnostic successor.
    - Shopify's gains came from context, not models (River's merge rate).

    ([landscape](goals/004-beacon-teardowns/landscape.md); [Glass PRD](goals/004-beacon-teardowns/teardowns/ramp/prd-glass.md#outside-views-round-3))
- decisions resting on it: (none yet)

### H-010: Moves that generate context make the best first tasks
- status: untested
- raised: 2026-09-27 · by: agent (synthesis)
- claim: The best first moves save effort and also leave validated, reusable context behind as
  a byproduct. Examples are constraint discovery, dependency mapping, and answering in-market
  support questions. Such moves seed the context layer while earning adoption (DEC-008).
- test: score candidate moves on effort share, delegability, context yield, and risk (Q-006).
  Pilot the top ones and measure how often later tasks reuse the context they produced.
- evidence:
  - 2026-09-27 (consistent with, weak): Ramp's earliest agents answered questions, and those moves
    generated context as they ran.
    - **Data questions.** Ramp Research's usage showed which tables to document next.
    - **Product questions.** Wrong answers became doc updates.

    ([Ramp Research](goals/004-beacon-teardowns/teardowns/ramp/prd-ramp-research.md),
    [Gadget](goals/004-beacon-teardowns/teardowns/ramp/prd-gadget.md))
- decisions resting on it: (none yet)

### H-011: Organization-level benefits only arrive as byproducts of individual value
- status: untested
- raised: 2026-09-27 · by: agent (follows from DEC-008)
- claim: If adoption has to be earned, users adopt only what helps them directly. Governed context
  and trace capture must come as byproducts of work users already want done, never as extra steps.
  Knowledge systems decay when contributors pay the cost and others get the benefit.
- test: in pilots, measure how much context arrives as a byproduct versus through extra effort,
  and retention by user. Look for the pattern in the beacon teardowns.
- evidence:
  - The "contributors pay, others benefit" failure is a common observation about
    knowledge-management tools, but we haven't sourced it.
  - 2026-09-27 (for, weak: self-reported): Ramp's per-user memory is built from the exhaust of
    work (Slack, Notion, Linear, Calendar) with no extra effort from users. That's context as a
    byproduct ([beacon scan](context/inbox/_processed/2026-09-27-beacon-scan.md), §0).
  - 2026-09-27 (mixed): some Ramp examples fit the byproduct principle:
    - VOTC pushes personalized digests to each account owner, so the individual gets value first.
    - Gadget spares PMs interruptions while it writes to the record.

    But Ramp also mandated usage and ranked people on a leaderboard, so its adoption doesn't test
    the principle cleanly ([Ramp teardown](goals/004-beacon-teardowns/teardowns/ramp/index.md)).
  - 2026-09-27 (for, med: first-party with screenshots, round 2):
    - Glass went from 3 to 976 weekly users in four weeks, with "no company-wide launch
      announcement or top-down mandate."
    - Its sponsor: "The investment followed the results, not the other way around."
    - Shared skills, the organization-level benefit, grew as a byproduct: 15, then 350+, then about
      800 in three months.

    ([Glass](goals/004-beacon-teardowns/teardowns/ramp/prd-glass.md),
    [Ramp vision](goals/004-beacon-teardowns/teardowns/ramp/vision.md))
  - 2026-09-28 (for, weak: press reports plus first-party):
    - Meta and Amazon rolled back usage leaderboards, according to press reports.
    - Uber found that sharing wins beat directives.
    - Box uses its per-person token list to find practices worth teaching, not to rank people.

    ([landscape](goals/004-beacon-teardowns/landscape.md))
- decisions resting on it: (none yet)

### H-012: In a regulated enterprise, context with provenance and traces double as control evidence
- status: untested
- raised: 2026-09-27 · by: agent (synthesis)
- claim: Context with provenance, plus traces of what the agent and the human each did, can serve
  as evidence for existing controls: why a decision was made, which constraints were checked, and
  who approved. That could turn risk and compliance functions from gatekeepers into sponsors.
- test: map candidate trace and context records to typical control requirements (Q-014), and
  check how the beacons handle audit.
- evidence:
  - 2026-09-27 (for, weak: said, about quality rather than regulation). Ramp uses traces for audit
    in several places:
    - Review Buddy reads "all the prompts that led you to build that code" to "audit how you used
      AI."
    - Inspect opens PRs under the user's identity, so nobody can approve their own change, and it
      attributes every prompt.
    - The autonomous loop keeps "one signal … attached to its context, decisions, code, and
      outcome."
    - VOTC answers carry "View trace."

    These are quality and engineering controls. None is described as regulatory evidence
    ([Ramp teardown](goals/004-beacon-teardowns/teardowns/ramp/index.md)).
  - 2026-09-27 (a design pattern, round 2): Ramp's PM shaping skill builds provenance in:
    - requirement IDs tied to evidence
    - closed questions with their sources
    - research saved as files

    Ramp uses this for quality, not control. Glass shows the gap: local agents inherit the user's
    identity, and nothing is traced centrally
    ([Glass](goals/004-beacon-teardowns/teardowns/ramp/prd-glass.md)).
  - 2026-09-28 (for, med: second pass):
    - The UK Home Office requires AI-assisted changes to be marked and traceable.
    - AWS AI-DLC tags every claim with its source, treats requirement IDs as permanent trace keys,
      and keeps a 105-event audit trail.
    - Cloudflare's standards carry stable IDs and a lifecycle from approved to enforced. Its AI
      reviewer enforces them on every merge request.
    - Singapore GovTech's CTO frames the audit questions a spec-first regime must answer: who wrote
      the specification, and who approved the agent's reading of it?

    ([landscape](goals/004-beacon-teardowns/landscape.md))
- decisions resting on it: (none yet)

### H-013: An opinionated structure costs users little if the agent maintains it
- status: untested
- raised: 2026-09-27 · by: agent (from Q-015)
- claim: Users talk and the agent files. Given that, a typed core of entities with IDs and links
  can deliver most of the benefits of a rigid schema without the adoption cost (C6): aggregation,
  cross-project visibility, and rollups. The cost that remains is that agent-filed structure can be
  wrong, so it needs the validation loop (DEC-011).
- test: in this project (goal 002) and in pilots, measure how often humans edit structure directly
  versus the agent filing it, how often the agent misfiles, and what the friction notes say.
- evidence:
  - This project is the first direct test, since the scaffold's first design aim is "drop-in."
    No direct evidence yet.
  - 2026-09-27 (consistent with, weak, from outside):
    - Ramp's Gadget writes the record itself ("Record: What changed?").
    - Ramp's knowledge loops have agents draft corrections that people approve.

    ([Gadget](goals/004-beacon-teardowns/teardowns/ramp/prd-gadget.md))
  - 2026-09-27 (consistent with, weak, round 2): Glass files structure for its users.
    - Its memory agent sorts what it learns into fixed categories (People, Active Work,
      Capabilities, Preferences, Organization), and the user approves each entry.
    - Publishing a skill hides Git behind a "publish" button.
    - A Ramp data lead names "the baked in opinions to how we think about different projects" as
      what set Glass apart from Claude Desktop.

    ([Glass](goals/004-beacon-teardowns/teardowns/ramp/prd-glass.md))
- decisions resting on it: (none yet)

### H-014: The harness can stand out by closing the gaps the beacons leave
- status: untested
- raised: 2026-09-28 · by: agent (synthesis of the second-pass landscape)
- claim: The beacons have converged on a baseline for intent definition that a PM harness must
  meet: a plan step before build, structured clarifying questions, answers logged in the spec,
  requirement IDs, and machine-checkable acceptance criteria. The harness's distinctive value would
  come from what no beacon does in public:
  - routing open questions to named experts, and keeping each answer with who gave it and their
    authority to decide
  - drawing legal and compliance requirements from the control owners into the spec and its tests
  - tracing requirements through tests into production
  - keeping discovery evidence linked to the spec as new evidence arrives
  - shaping intent with several people over time, with explicit decision rights
- test:
  - Keep checking each new teardown for anyone doing these (goal 004).
  - In a pilot, compare shaped specs with and without expert routing. Measure rework caused by late
    expert or compliance input, and how often banked answers get reused.
- evidence:
  - 2026-09-28 (for, med): the second-pass landscape found no public example of the first two across
    about 50 entities. The closest are:
    - Meta's compliance "second brain"
    - Cloudflare's owner-maintained standards
    - AWS AI-DLC's stakeholder map and compliance agent
    - Anthropic's PM plugin, which tags questions by who should answer them but doesn't route them

    ([landscape](goals/004-beacon-teardowns/landscape.md))
- decisions resting on it: (none yet)

