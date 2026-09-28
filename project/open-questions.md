# Open questions and contradictions

Every contradiction or tension the agent notices goes here. Blocking items are also raised
with the user immediately.

Format:

```
### Q-NNN: short title
- status: open | resolved
- blocking: yes | no
- between: <source A> ↔ <source B>
- raised: YYYY-MM-DD
- notes: …
- resolution: DEC-NNN (and which files were updated)
```

## Open

### Q-001: What does "deployed" mean for the harness?
- status: open
- blocking: no
- between: vision.md ↔ (unspecified)
- raised: 2026-09-27
- workstream: goal 001
- notes: This shapes D1 and the eventual runtime choice (C1 is only a v0 default).
  - Sharpened 2026-09-27: the direction is now a shared, persistent, deployed agent (DEC-007),
    reached through a series of stops (DEC-009). What's still open is **which deployment model v1
    targets** (path axis 2). PMs already have sanctioned access to a chat assistant, Claude Code /
    Claude Enterprise, and an internal LLM platform, so stop 2 needs no new tooling. H-009 suggests
    v1 can start small on deployment topology if context and traces are shared from day one. See
    [path](context/wiki/path.md).

### Q-004: What are the major PM moves, and what are their inputs, process, and outputs?
- status: open
- blocking: no, but Q-005, Q-006, Q-007, and Q-008 all build on it
- between: DEC-007 ↔ (unknown)
- raised: 2026-09-27
- workstream: goal 003
- notes: Geoff says "this all rests upon a more complete sense than I have about the major product
  moves we should focus on, and a usable taxonomy" ([thesis note](context/inbox/_processed/2026-09-27-thesis-and-direction.md)).
  A seed list and a proposed annotation schema are in [pm-moves](context/wiki/pm-moves.md).
  - 2026-09-27 (an outside method): Ramp Labs built a taxonomy of agentic work from the bottom up.
    - It split about 250,000 Inspect traces into "work items," each with one objective and one
      outcome.
    - It clustered them into 30 categories, to attribute ROI.
    - Goal 003 could use the same method on our own traces: derive moves from observed work, not
      only from theory
      ([Ramp sources](goals/004-beacon-teardowns/teardowns/ramp/sources.md), S53).

### Q-005: Where does PM effort go today, and how much of it needs creativity or judgment?
- status: open
- blocking: no
- between: H-003, H-004 ↔ (no evidence yet)
- raised: 2026-09-27
- workstream: goal 005
- notes: This tests the value case. It needs the taxonomy (Q-004) as its unit of analysis.
  Enterprise data can enter the repo only as generic summaries (C5).

### Q-006: Which moves should the harness take on first? (path axis 1)
- status: open
- blocking: no
- between: DEC-007 ↔ (unknown)
- raised: 2026-09-27
- workstream: goal 001 (informed by 003 and 005)
- notes: Candidate criteria:
  - effort share
  - judgment content
  - context yield (H-010)
  - risk in a regulated setting (C7)
  - measurability
  - frequency
  - whether the gain is obvious to the person doing the move (C6)

  Depends on Q-004 and Q-005.
  - 2026-09-27: one candidate to weigh, not a choice: spec-shaping moves for the teams piloting SDD.
    They feel the need for well-defined specs most sharply, which suits earned adoption.
  - 2026-09-27 (outside evidence): Ramp chooses by **bottleneck**: "Find that one bottleneck that
    you think can 10x your company and just start there," and expect the next one to appear.
    Ramp's actual first moves were context-bound Q&A:
    - data questions (Ramp Research, 2025)
    - product questions (a Notion agent, "85% … no human in the loop")
    - customer-signal synthesis

    Coding came next, and the PM define step came last. "Which move is the binding constraint
    right now?" is a candidate meta-criterion
    ([Ramp teardown](goals/004-beacon-teardowns/teardowns/ramp/index.md)).

### Q-007: How should we think about the context ecosystem? (path axis 3)
- status: open
- blocking: no
- between: DEC-011 ↔ (unknown)
- raised: 2026-09-27
- workstream: goal 006
- notes: Open threads:
  - architecture: federated, curated, or hybrid
  - governance: ownership, validation, provenance, freshness, access tiers
  - what "trustworthy" and "credible" mean in operational terms
  - how the context-building loop actually runs

  Working principles are in [context-layer](context/wiki/context-layer.md).
  - 2026-09-27 (outside evidence): Ramp runs two context-building loops in production:
    - **The product-Q&A loop.** Every answer goes into a database, an expert marks it right or
      corrects it, and a nightly agent turns wrong answers into doc updates.
    - **Ramp Research.** Instead of checking each answer, domain owners write tests for the
      context layer.

    Ramp's rule of thumb: "every AI system is two systems at least," the conversation plus the
    loop that routes failures to whoever can fix them
    ([Ramp teardown](goals/004-beacon-teardowns/teardowns/ramp/index.md)).

### Q-008: What is the spec contract between PM moves and agentic delivery?
- status: open
- blocking: no
- between: DEC-010 ↔ (unknown)
- raised: 2026-09-27
- workstream: goals 003 and 006, for now
- notes: Open threads:
  - what SDD needs from a spec to build without constant refinement
  - what acceptance needs back from SDD
  - how delivery agents use the same context layer
  - whether SDD is in use at the enterprise yet (answer generically, per C5)

  Updates:
  - 2026-09-27: some teams at the enterprise are piloting SDD (Geoff), so real specs will soon
    exist to learn from.
  - 2026-09-27: outside, spec tooling is moving upstream. Spec Kit added an idea-assessment
    process in July 2026, and AWS AI-DLC logs human approvals all the way from intent to code
    ([beacon scan](context/inbox/_processed/2026-09-27-beacon-scan.md), §8–9).
  - 2026-09-27 (outside evidence): Ramp's CPO calls the handoff **"the next contract."** It has
    three parts:
    - qualitative and quantitative evidence that the problem is real
    - "the actual requirements that they can use for their coding agents"
    - a working prototype on the real codebase

    Not a long spec, and not a prototype alone. The spec comes in two versions: a short one for
    humans, and an "agent version that is much more robust." The spec template is a SKILL.md, and a
    conversational product-shaping skill produces it
    ([Glass PRD](goals/004-beacon-teardowns/teardowns/ramp/prd-glass.md), part B).
  - 2026-09-27 (outside evidence, round 2): the shaping skill itself, read from the video frames.
    - Its discipline:
      - a one-sentence framing gate
      - an evidence bar (quantified, attributed, honest about causality)
      - requirement IDs tied to evidence
      - closed questions with their sources
      - research kept as files
    - Its seven-section spec stops at "specific enough to prototype," with **no acceptance
      criteria**.
    - At Ramp, acceptance criteria show up only at the Inspect session boundary. The docs ask each
      session for "acceptance criteria that define success."

    ([Glass PRD](goals/004-beacon-teardowns/teardowns/ramp/prd-glass.md), part B;
    [Inspect](goals/004-beacon-teardowns/teardowns/ramp/prd-inspect.md), I13)
  - 2026-09-27 (secondary: an earlier research note, still to be verified):
    - Of 17 companies checked, only Coinbase Wallet, which is regulated, documents a pre-build
      contract with acceptance criteria.
    - Its rule is "plan, don't prompt." The plan holds:
      - the user outcome
      - current behavior
      - the repositories involved
      - acceptance criteria
      - edge cases
      - the evidence the agent must return
    - When a build fails, engineers fix the plan, not the code.
    - AWS AI-DLC traces requirements to tests.
    - The note also offers a seven-step yardstick for the idea-to-code loop. No company documents
      all seven steps.

    ([earlier research note](context/inbox/_processed/2026-09-20-pm-idea-to-code-stripe-ramp.md))

  - 2026-09-28 (second pass): the tools have converged on a spec contract, and Ramp's is now the
    outlier:
    - a read-only plan step before build
    - clarifying questions asked one at a time with a recommended answer, then logged with dates in
      the spec; unanswered questions become recorded assumptions
    - stable requirement IDs as trace keys
    - machine-checkable acceptance criteria (EARS or Given/When/Then)
    - verification against the spec; Kiro links property-based tests to requirements

    Coinbase's plan contract is now confirmed first-party: a skill drafts it, simulator fleets verify
    it "against your spec," and failures get fixed in the plan. Uber and Cloudflare review written
    intent before build, but neither publicly wires that review into its build agents
    ([landscape](goals/004-beacon-teardowns/landscape.md)).

### Q-009: What are the beacons doing on each axis, and what transfers to a regulated enterprise?
- status: open
- blocking: no
- between: DEC-007 ↔ (public evidence)
- raised: 2026-09-27
- workstream: goal 004
- notes: Use public information only. Compare the beacons (e.g., Ramp's Glass) on:
  - first moves
  - deployment model
  - context approach
  - traces
  - controls

  The first-pass scan is done (2026-09-27). It covers Glass plus 14 other beacons and names 5
  priorities for deep teardowns ([digest](goals/004-beacon-teardowns/context/landscape-scan.md)).
  - 2026-09-27: the first deep teardown, Ramp v1, is done: a product vision plus eight feature PRDs
    from the CPO's talk and 49 other public sources
    ([teardown](goals/004-beacon-teardowns/teardowns/ramp/index.md)).

  - 2026-09-27 (Ramp rounds 2 and 3): Glass in depth. The hypothesis about intent shaping was
    tested (partly supported), and outside views were added.
  - 2026-09-28: the second-pass landscape scores about 50 entities across five kinds of beacon. It
    ranks the next round in tiers, with Coinbase, Uber, and AWS (AI-DLC with Kiro) first
    ([landscape](goals/004-beacon-teardowns/landscape.md)).

### Q-010: How will we measure progress?
- status: open
- blocking: no
- between: vision.md (what winning looks like) ↔ (no measures yet)
- raised: 2026-09-27
- workstream: goal 005
- notes: Candidate measures:
  - effort by move category (H-006)
  - context coverage and credibility (H-007)
  - delegation level per move, from traces (H-005)
  - how often constraints get re-discovered (H-004)
  - spec rework during delivery (DEC-010)
  - organic adoption and retention (C6)

  - 2026-09-27 (outside evidence): Ramp's self-reported measures, as candidates:
    - the share of questions asked of PMs that AI fully answers (85%)
    - small UX issues fixed within 24 hours (60%)
    - "fewest human touches per safely merged PR"
    - bugs caught before customers (425 in 30 days)
    - the share of PRs from non-engineers

    On velocity itself, the CPO relies on judgment rather than a metric: hire "a driver that knows
    what speed looks like" ([Ramp vision](goals/004-beacon-teardowns/teardowns/ramp/vision.md)).
  - 2026-09-27 (outside evidence, round 2):
    - Glass tracked weekly unique users, sessions, and "user actions," which went from 3 to 976
      users in four weeks. It also tracks spend per skill.
    - Ramp Labs attributes AI spend to outcomes. It splits traces into "work items" (one objective,
      one outcome each) and classifies them.
    - That's a candidate way to measure value per move from traces (H-005)
      ([Glass](goals/004-beacon-teardowns/teardowns/ramp/prd-glass.md),
      [Ramp sources](goals/004-beacon-teardowns/teardowns/ramp/sources.md), S53).

### Q-011: Where do the judgment moves end up in the terminal state?
- status: open
- blocking: no
- between: DEC-009 (a fully synthetic PM) ↔ H-006 (humans shift to judgment work) ↔ C7
  (accountable humans in a regulated enterprise)
- raised: 2026-09-27
- notes: If the PM becomes fully synthetic, who identifies problems, applies taste to solutions,
  and accepts what gets built? Possible answers:
  - Agents eventually do these too, and humans keep only accountability.
  - They migrate to other humans (business owners, design, risk).
  - A thin human PM role remains.

  The answer decides whether the taxonomy and the context layer must eventually cover judgment
  moves (customer-empathy inputs and taste exemplars, for example) or can stay focused on the
  context-bound moves. DEC-009 stands as a working assumption in the meantime.
  - 2026-09-27 (outside evidence, self-reported): Ramp's CPO sees three PM tracks:
    - the technical PM who builds "the factory"
    - the **tastemaker**, "holding the steering wheel … holding the bar for what great product,
      great taste looks like"
    - the **GM**, who owns "the actual business outcome"

    Ramp runs 22 PMs in a company of 1,600. For Ramp, taste and business judgment stay human, while
    coordination and the inputs to problem identification are automated. That's closest to "a thin
    human PM role remains," plus a new role building the factory
    ([Ramp vision](goals/004-beacon-teardowns/teardowns/ramp/vision.md)).

### Q-012: Does C1 (Claude Code native) constrain the harness, or only how we run this project?
- status: open
- blocking: no
- between: C1 / DEC-002 ↔ DEC-007 (a shared, deployed agent), DEC-003 (the scaffold is not the harness)
- raised: 2026-09-27
- notes: C1 predates DEC-003. Proposed reading: C1 governs the scaffold, and the harness runtime
  stays open (goal 001). Claude Code / Claude Enterprise is already sanctioned, so a Claude-based
  stop 2 is feasible either way. Needs Geoff's confirmation, since resolving it edits a constraint.

### Q-013: How do organization-level benefits avoid taxing individual users?
- status: open
- blocking: no
- between: C6 / DEC-008 (earned adoption) ↔ H-004, H-005 (governed context and traces benefit the
  organization)
- raised: 2026-09-27
- notes: Contributing context and having your work traced can feel like overhead, or like
  surveillance. If users bear the cost while the organization gets the benefit, the harness won't
  earn its adoption. H-011 proposes a byproduct principle. The first moves (Q-006) and the design
  of trace capture (H-005) both need to pass this test.
  - 2026-09-27 (outside evidence): Ramp shows both sides.
    - **The tax side:** Gadget "pings people who are late on their deliverables," and a usage
      leaderboard is visible to everyone.
    - **Glass avoids the tax, at a cost:** it doesn't monitor sessions at all ("we don't monitor
      anything in Glass"), and its team says the price is that skill owners get no feedback.
    - **The byproduct side:** VOTC's personalized podcasts deliver value to the individual first.
    - **Ramp's adoption was partly mandated**, so its playbook doesn't test C6 cleanly
      ([Ramp teardown](goals/004-beacon-teardowns/teardowns/ramp/index.md)).

### Q-014: Which enterprise controls bound the design, and how do we record them in a public repo?
- status: open
- blocking: no (it will block choosing v1's deployment model)
- between: C7 ↔ C5
- raised: 2026-09-27
- workstream: goal 006
- notes: Relevant controls:
  - data classification
  - access control
  - audit and records retention
  - model risk management
  - approvals for third-party AI
  - human accountability for decisions that affect customers

  These are priors, and they belong to other people. Most are confidential, so they can't be stored
  or linked here. Proposal: record generic summaries in `priors/index.md`, with owners described by
  role. Logged as [scaffold friction](context/inbox/_processed/2026-09-27-friction-private-context.md).
  - 2026-09-27 (outside evidence): Ramp practices that would collide with typical controls:
    - test environments seeded from "actual production data" (Testo)
    - 93% of PRs "automatically handled" by an AI reviewer, where it's unclear whether a human
      approves
    - sessions public by default
    - "no tiered access based on role"
    - agents posting in Slack as the user

    The controls Ramp does have are engineering controls: PRs under the human's identity, least
    privilege, sanitized replicas, review tiered by risk, release tiers. Each teardown PRD has a
    "what transfers" section ([Ramp teardown](goals/004-beacon-teardowns/teardowns/ramp/index.md)).
  - 2026-09-27 (outside evidence, round 2):
    - More Ramp controls worth borrowing:
      - Glass's per-tool Auto/Allow/Ask permission modes, and its memory approval queue
      - agent identities with attribution, scope capped at the human sponsor's, and expiry by
        default (S84)
      - shadow mode and per-agent exposure budgets for risk agents, where "every autonomous risk
        decision is still made by an auditable model, governed under an approved policy" (S85)
    - A gap Ramp names itself: local agents inherit the user's identity in data systems, and its
      data lead wants "a stiffer guardrail" (S66).
    - An earlier research note (secondary) checked 17 companies. None documents how feature-specific
      legal or compliance requirements are elicited, written into the spec, or tested in a live
      delivery flow. Coinbase and Monzo, both regulated, describe risk-tiered review and sandboxing
      instead. If that holds up, it's open ground for the harness.

    ([Glass](goals/004-beacon-teardowns/teardowns/ramp/prd-glass.md),
    [Ramp sources](goals/004-beacon-teardowns/teardowns/ramp/sources.md),
    [earlier research note](context/inbox/_processed/2026-09-20-pm-idea-to-code-stripe-ramp.md))

  - 2026-09-28 (second pass: regulated organizations across several industries):
    - Humans approve every merge. Nobody publicly lets agents deploy.
    - Risk tiers along four axes: review depth by change risk, agent permissions by domain, autonomy
      by how critical the system is, and tool risk at procurement.
    - Sandboxes behind a single egress proxy.
    - Agents registered with their own identity and a named human owner.
    - AI-assisted changes marked and traceable.
    - Golden sets of expert-approved examples serve as behaviour specs for operations agents.
    - Coding agents are governed as tools under SDLC controls, not validated as models. Agents that
      act in operations get model-style validation: evals, golden sets, audit.
    - Uber's traces show approval fatigue: past about 50 approvals a session, "human oversight
      becomes a rubber stamp."
    - **Still nobody publicly draws out feature-specific legal or compliance requirements into specs
      or tests.** The closest are Cloudflare's owner-maintained standards, which now include
      compliance, and Meta's compliance "second brain."

    ([landscape](goals/004-beacon-teardowns/landscape.md))

### Q-015: How opinionated should the underlying data structure be, and which entities should be recorded, shareable, and canonical?
- status: open
- blocking: no, but it's one of the stickiest choices on path axis 3, because schemas are hard to
  retrofit ([path](context/wiki/path.md))
- between: DEC-007 (a shared, persistent agent) ↔ C6 (earned adoption: structure can tax users) ↔
  C7 (canonical records attract records governance) ↔ the systems of record the enterprise already has
- raised: 2026-09-27 · by: Geoff: "There's a big question about the underlying data structure and
  how opinionated it should be. Should projects be recorded, shareable, canonical? How about goals?"
- workstream: goal 006 (research first; don't force a decision)
- notes: Recorded, shareable, and canonical are three separate properties, and each can be set per
  entity type. There's also a question underneath: is "project" the right primary unit, or is it
  "product"? project-scaffold-v1 is a lightly opinionated answer at the scale of one project, so it
  doubles as a live experiment (H-001, H-013). A per-entity starting point is in
  [data-model](context/wiki/data-model.md).

### Q-016: One PM agent, or a factory of single-purpose agents on shared context?
- status: open
- blocking: no (it shapes goal 001's list of candidate designs)
- between: DEC-007 ("a shared, persistent, deployed product-manager agent") ↔ Ramp's pattern
- raised: 2026-09-27 · by: agent, from the [Ramp teardown](goals/004-beacon-teardowns/teardowns/ramp/index.md)
- workstream: goal 001 (research; don't force a decision)
- notes: Ramp's pattern has three parts:
  - a general coworker, Glass, as each person's workbench
  - one agent per bottleneck in the loop: VOTC, Inspect, Review Buddy, Testo, Gadget, the
    autonomous loop
  - one formal record, kept "legible to your agents," that all of them read and write

  Ramp's beliefs behind it: "bottlenecks shift as you eliminate them" and "invest in the factory."
  On that view, the lasting asset is the ability to add a new move-level agent quickly on shared
  context, not any single agent (consistent with H-009).

  This isn't necessarily a conflict. The vision already allows "an agent or agent orchestrator,"
  and DEC-007's "agent" could be a family of agents. But the unit of design differs:
  - one agent that owns the PM role, or
  - agents that own bottlenecks, with the PM role spread across them and the humans

  It bears on Q-001 (what "deployed" means), Q-006 (first moves), and Q-007 (the shared layer the
  agents need).
  - 2026-09-27 (round 2): Ramp answers "both."
    - Three general-purpose surfaces run side by side:
      - Glass, for non-technical staff
      - Inspect, for "builders"
      - Claude's own apps, for about 2,000 employees under enterprise auth
    - Single-purpose agents run alongside them.
    - The judgment-heavy define step uses a general agent carrying a portable skill. The
      high-volume identify and coordinate steps use single-purpose agents.
    - Glass's lead left in June, and nobody has explained in public how the three surfaces overlap.

    ([intent-shaping](goals/004-beacon-teardowns/teardowns/ramp/intent-shaping.md))

  - 2026-09-28 (second pass): the leading factories pair many single-purpose agents with a shared
    context layer and a general front door.
    - Uber runs research, PRD-review, build, and review agents over one context graph and skills
      marketplace, entered from Slack.
    - Coinbase runs a Slack-native harness over Linear, its source of truth.
    - Vendors now sell the general layer. Claude folded in Cowork on 2026-09-16, with org plugin
      marketplaces, and OpenAI offers workspace agents.
    - Box's CEO says a shared agent must be "like any other user in the system," with its own
      identity.

    The general coworker is becoming a commodity. What's distinctive is the context, and the
    single-purpose agents built on it (H-009)
    ([landscape](goals/004-beacon-teardowns/landscape.md)).

## Resolved

### Q-003: Should evolving project-scaffold-v1 be its own goal?
- status: resolved
- blocking: no
- between: DEC-003 ↔ (goal list)
- raised: 2026-09-27
- resolution: DEC-005, which creates goal 002.

### Q-002: What is the scaffold called?
- status: resolved
- blocking: no
- between: DEC-003 ↔ (unnamed)
- raised: 2026-09-27
- resolution: DEC-004 (project-scaffold-v1). The goal question moved to Q-003. Updated CLAUDE.md,
  vision.md, goal 001, and the ingest skill.
