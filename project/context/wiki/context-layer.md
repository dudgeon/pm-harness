# The context layer: working principles

> Working notes for Q-007. The principles here are hypotheses until tested.

## What Geoff said

From the [thesis note](../inbox/_processed/2026-09-27-thesis-and-direction.md):

- Context should build up in governed stores that agents can access, instead of staying as tacit
  knowledge held by SMEs (H-004).
- The layer should be trustworthy, and should become increasingly complete and credible.
- It gets built iteratively, not up front (DEC-011, H-007). Agents orchestrate discovery, humans
  carry it out, and results are validated and governed as they're added. Repeating that loop
  gradually improves the context until it's good enough for full automation.

## Working principles (agent synthesis, to test)

1. **Credibility is explicit.** Every claim carries its provenance (source, owner, date) and a
   trust tier. Grounded claims outrank hypotheses.
2. **The agent orchestrates discovery, and humans carry it out.** The agent knows what's missing
   and whom to ask. The human finds out and validates. The agent files the result.
3. **Traces show where context is missing.** Each time a human corrects the agent or supplies a
   fact, that marks a gap the loop should close (H-005, H-007).
4. **Context is a byproduct, not a chore.** It's captured as a side effect of moves users already
   want done (H-011, C6, Q-013).
5. **The layer is shared with delivery.** SDD agents read the same layer. They can check specs
   against known constraints before building, which shortens the refinement loop from both ends
   (DEC-010, Q-008).
6. **The layer is governed like a record.** In a regulated enterprise it needs access tiers,
   classification, and retention (C7, Q-014). Provenance and traces may also serve as control
   evidence (H-012).

## What the beacons do

From the [beacon scan](../inbox/_processed/2026-09-27-beacon-scan.md) and the
[Ramp teardown](../../goals/004-beacon-teardowns/teardowns/ramp/index.md). All of it is
self-reported unless marked otherwise.

- **Skills live in versioned, reviewed files.**
  - Ramp's Dojo holds 350+ markdown skills, "Git-backed, versioned, and reviewed like code."
  - LinkedIn's CAPT playbooks get InfoSec review.
  - Tessl, AWS steering files, and Spec Kit's constitution work the same way.
  - *Round 2:* Dojo reached about 800 skills by May, grouped into 12 function kits, including
    Product and Design.
  - The same skill bundle runs in more than one harness (Ramp Research in both Glass and Inspect).
    Connecting a data source can install its skills.
  - Curation matters. Ramp's own ablation on another product found most skills neutral or harmful
    and a slimmer bundle better
    ([Ramp sources](../../goals/004-beacon-teardowns/teardowns/ramp/sources.md), S66, S78, S86).
- **Memory is synthesized from the exhaust of work.** Ramp rebuilds each user's memory every 24
  hours from Slack, Notion, Linear, and Calendar, scoped to that user's permissions (§0). This is
  principle 4 without a human validation step, and it's an alternative to the loop in DEC-011.
  - *Corrected from primary sources, 2026-09-27:*
    - The daily pipeline mines past sessions, Slack, Notion, and Calendar.
    - Memory is written once. The agent never edits it mid-session, and it's kept in files the
      user can inspect.
    - In v2, users review what gets remembered.

    So there is a light human check after all ([Glass PRD](../../goals/004-beacon-teardowns/teardowns/ramp/prd-glass.md)).
  - *Round 2, from screenshots:*
    - A memory agent proposes entries into an Approve/Dismiss queue.
    - Entries fall into fixed categories: People, Active Work, Capabilities, Preferences,
      Organization.
    - There's also team memory, a per-user voice file, and per-project memory.
- **The brief has no governed home at Ramp.** Spec drafts are local files, the record is in Notion,
  and prototypes are Inspect sessions. A Ramp designer calls the missing project "source of truth"
  a blocker. That's a gap a shared context layer could fill
  ([intent-shaping](../../goals/004-beacon-teardowns/teardowns/ramp/intent-shaping.md)).
- **Standards and expert knowledge as governed context** (second pass, [landscape](../../goals/004-beacon-teardowns/landscape.md)):
  - *Cloudflare* writes standards like RFCs, with named owners, stable IDs, and a lifecycle from
    approved to enforced. An AI reviewer enforces them on every merge request. Compliance teams now
    add standards too.
  - *Meta's Organizational Second Brain* turns expert corrections into reviewed diffs to its
    knowledge files, and each one joins a regression suite.
  - *Box* gates retrieval by article metadata, and a weekly review of unresolved requests feeds
    human-reviewed fixes.
  - *Answers banked in the spec, with dates:* Spec Kit's clarification log, BMAD's typed decision
    log, and AI-DLC's question files. None records who had the authority to answer (H-014).
- **The organization is made legible to agents.** Ramp consolidates work into one formal record
  and answers questions from it: "every question is an API." Answers from humans get fed back
  ([Gadget PRD](../../goals/004-beacon-teardowns/teardowns/ramp/prd-gadget.md)).
- **Context loops with owners.** "Every AI system is two systems at least": the conversation, plus
  the loop that routes failures to whoever can fix them. Ramp runs two such loops:
  - *The product-Q&A agent.* Experts mark each answer, and a nightly agent turns wrong answers into
    doc updates, reaching "85% of all questions take no human in the loop."
  - *Ramp Research.* Domain owners test the context layer instead of reviewing each answer.

  These are principles 2 and 3 running in production.
- **Traces are split by platform.** Inspect traces every session end to end. Glass captures none,
  by design ("we don't monitor anything in Glass"), and its team names the cost: skill owners get
  no feedback. Relevant to H-005 and H-009.
- **Learnings get written back.** LinkedIn's agents are told to write what they learn back into
  playbooks, and every call is logged (§1, from a third-party summary). This is a
  context-building loop running in production.
- **Permissions come from the source.** Atlassian's Teamwork Graph keeps source-system permissions
  and is open to outside agents through MCP (§2). A regulated enterprise may already own this layer.

**Agent observation.** The beacons converge on keeping *procedural* context (how to do a move,
written as a skill) in files. That sits alongside *declarative* context (facts, constraints,
decisions). The taxonomy connects the two: each move could have a skill, which is procedural, and
the move's inputs and outputs are declarative. The layer may need both kinds (goal 006, Open).

## The scaffold as a small-scale version (agent observation)

project-scaffold-v1 already runs this loop for a single project:

- The agent reconciles new information, asks questions, and files the results.
- The human supplies facts and validates.
- The trust order governs: priors, then goals, then wiki, then inbox, with grounded claims above
  hypotheses.

That makes the scaffold a cheap test bed for principles 1–3. This is evidence for H-001 by analogy.

Its first friction note hits principle 6 at a smaller scale. Context that must stay out of a public
repo has nowhere to go ([note](../inbox/_processed/2026-09-27-friction-private-context.md)).

## Open design space (Q-007)

- **Where context lives.** Options:
  - federated: agents read systems of record through connectors
  - curated: a separate, validated layer
  - hybrid: curated claims whose provenance points back into systems of record
- **Format.** Markdown in git, a knowledge graph, a vector index, structured records, or a mix.
- **Ownership.** By domain, which raises the question of who validates what.
- **Freshness.** Expiry dates, and triggers for re-validating a claim.
