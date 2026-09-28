# Wiki log

Append-only. One entry per `/ingest` or `/lint` run.

```
## YYYY-MM-DD: ingest | lint
- <inbox item> → <page(s) created/updated>
- flagged: Q-NNN …
```

## 2026-09-27: scaffold
- Created the wiki structure.

## 2026-09-27: goal 002
- Created goal 002 (DEC-005) and snapshotted project-scaffold-v1 at `a6f5199`.

## 2026-09-27: ingest (Geoff's thesis, the beacon scan, and follow-up answers)
- **Thesis note** (Geoff, chat) produced:
  - decisions DEC-006 to DEC-011
  - hypotheses H-002 to H-012
  - constraints C5 to C8
  - questions Q-004 to Q-014; Q-001 sharpened
  - wiki pages [pm-moves](pm-moves.md), [path](path.md), and [context-layer](context-layer.md)
- **Data-structure question** (Geoff, chat): Q-015, H-013, and the [data-model](data-model.md)
  page. Geoff wants it researched, not decided on instinct.
- **Answers from Geoff:**
  - keep the repo generic (C5)
  - PMs now, builders later (H-008)
  - adoption has to be earned (C6)
  - sanctioned tooling, recorded generically
  - SDD is being piloted
  - build the taxonomy from industry practice, not the proprietary one (DEC-012)
  - effort evidence will come from Geoff's experience, interviews or surveys, and public studies
- **Beacon scan** (a background agent, public sources) produced:
  - the digest `goals/004-beacon-teardowns/context/landscape-scan.md`
  - evidence on H-002, H-005, H-007, H-009, and H-011
  - `from:004` tasks in goals 001, 003, 005, and 006
  - updates to three wiki pages
- **Three scaffold-friction notes** → `goals/002-project-scaffold/context/friction.md`, with tasks
  in 002 and evidence on H-001.
- **Goals:** created 003 (taxonomy), 004 (beacon teardowns), 005 (effort and delegation
  baseline), and 006 (context ecosystem and data structure), all `draft`. Goal 001 was re-scoped
  to own the v1 bet.
- **Deliverables:** D2 sharpened into "the v1 bet"; D3 to D6 added.
- **Deferred:** the vision rewrite. Geoff said "not yet"; revisit once the workstreams settle.
  There's no goal to hold that task yet (friction logged).
- **Flagged, all non-blocking:**
  - Q-011: where the judgment moves end up
  - Q-012: whether C1 applies to the harness
  - Q-013: earned adoption vs. organization-level benefits
  - Q-015: the data structure

## 2026-09-27: ingest (Ramp CPO talk) and the first deep teardown (Ramp)
- **Source.** Geoff Charles (Ramp CPO), "What product looks like when coding is solved," at the
  Lenny & Friends Summit (recorded 2026-09-10). Captured from YouTube captions plus slide frames →
  [digest](../inbox/_processed/2026-09-27-ramp-cpo-talk.md). The full transcript and texts from
  other key sources are kept locally in `inbox/_local/`, not committed.
- **Produced** [Ramp teardown v1](../../goals/004-beacon-teardowns/teardowns/ramp/index.md) (004-D2):
  a vision plus eight PRDs, citing sources S1–S50.
- **Goal 004,** at Geoff's direction:
  - definition sharpened: `active`, a concrete definition of done, R5–R7, new open questions
  - tasks and deliverables updated
  - landscape digest marked superseded for Ramp
- **Questions.** Raised Q-016 (one PM agent, or a factory of agents?). Added notes to Q-006, Q-007,
  Q-008, Q-009, Q-010, Q-011, Q-013, and Q-014.
- **Evidence.** Added to H-002 through H-013, plus a correction to the earlier Ramp evidence under
  H-007.
- **Tasks.** `from:004` tasks added to goals 001 (3), 003 (2), 005 (2), and 006 (4, plus one
  corrected).
- **Wiki.**
  - [pm-moves](pm-moves.md): Ramp's loop
  - [context-layer](context-layer.md): legibility, loops with owners, the split on traces; the
    memory claim corrected
  - [path](path.md): Glass is closer to the hybrid than to stop 3
- **Corrections to the beacon scan:**
  - Glass's harness is the Claude Agent SDK.
  - Glass's memory sources.
  - The Inspect post's date, and a misattributed quote.
  - The token-spend post is about Ramp's customer product.
  - Ramp Research has been superseded.
- **Friction.** Two scaffold-friction notes left in the inbox for the next `/ingest`:
  third-party sources in a public repo, and where goal deliverables live.
- **Flagged, non-blocking:** Q-016.

## 2026-09-27: ingest (Ramp round 2: Glass and intent shaping)
- **Prompt.** Geoff asked for a high-resolution read of Glass. He offered a hypothesis to
  challenge: "Glass is where the majority of intent shaping happens."
- **Sources.**
  - X timelines of Ramp leaders and builders.
  - About fifteen talks and interviews, transcribed where captions were blocked.
  - Ramp job postings.
  - The screenshots inside the Glass launch articles.
  - A frame-by-frame read of the PM product-shaping skill.
  - An earlier research note Geoff supplied →
    [filed](../inbox/_processed/2026-09-20-pm-idea-to-code-stripe-ramp.md) as secondary evidence.

  Sources S51–S86 in the [register](../../goals/004-beacon-teardowns/teardowns/ramp/sources.md).
  Transcripts and the skill's full text stay local in `inbox/_local/`.
- **Produced:**
  - [intent-shaping](../../goals/004-beacon-teardowns/teardowns/ramp/intent-shaping.md), which
    tests the hypothesis. Verdict: partly supported. Glass is the designated front door for
    define. The shaping loop is a relay across VOTC, Glass or Claude Code, Inspect, and Notion,
    and the brief has no governed home.
  - [Glass PRD v2](../../goals/004-beacon-teardowns/teardowns/ramp/prd-glass.md).
  - Updates to the Inspect, VOTC, Ramp Research, and Gadget PRDs, the vision, and the index.
- **Corrections:**
  - The CPO's Glass slide has a third branch, "build the prototype" (fixed in the Glass PRD).
  - Ramp Research is retired as a product but lives on as a skill bundle in Glass and Inspect.
- **Evidence.** Added to H-002, H-005 (two bullets), H-007, H-008, H-009, H-011, H-012, and
  H-013.
- **Questions.** Notes added to Q-004, Q-008, Q-010, Q-014, and Q-016.
- **Tasks:**
  - `from:004` tasks added to goals 001 (2), 003 (1), 005 (1), and 006 (1).
  - Three existing tasks extended.
  - Goal 004 gained a verification task for the earlier note's scorecard (Coinbase Wallet and Monzo
    first).
- **Wiki.**
  - [pm-moves](pm-moves.md): the shaping skill as a breakdown of moves 1–3
  - [path](path.md): Ramp's own path from stop 2 to the hybrid
  - [context-layer](context-layer.md): skill portability and curation, the memory approval queue,
    and the brief's missing home
- **Flagged, non-blocking:** Q-016. Ramp runs three general-purpose surfaces side by side (Glass,
  Inspect, and Claude's own apps), and their overlap isn't explained in public.

## 2026-09-28: ingest (the second-pass landscape, and Glass round 3)
- **Prompt.** Geoff asked for more informed takes on Glass, a survey of PM-focused agents and of
  coding agents with intent-definition features, and profiles of companies touting agentic delivery
  (Stripe, Block, Coinbase, Atlassian, Shopify, Meta, Uber, Airbnb, then Box). He also wanted a look
  at Lenny's ecosystem. Then: flesh out goal 004 and prioritize the next round.
- **Method.**
  - Seven research passes in parallel, on public sources only.
  - Each checked engineering blogs and the public posts of CEOs, CPOs, and CTOs (now R8).
  - Their notes and transcripts stay local in `inbox/_local/research-2026-09-28/`.
- **Produced:**
  - The [second-pass landscape](../../goals/004-beacon-teardowns/landscape.md) (004-D1): about 50
    entities on one scorecard, what the landscape says, the gaps no beacon fills, and a tiered plan.
    Tier 1 is Coinbase, Uber, and AWS (AI-DLC with Kiro).
  - Glass round 3: [outside views](../../goals/004-beacon-teardowns/teardowns/ramp/prd-glass.md#outside-views-round-3)
    and a comparison with vendor coworker apps. Sources S87–S94.
- **Goal 004,** at Geoff's direction:
  - tiered depth for teardowns
  - R8 (blogs and executive posts), R9 (depth by tier), R10 (keep the enterprise generic)
  - two open questions answered
  - tasks rewritten around the tiers; the old deep-teardown tasks for LinkedIn, Citi, AWS, and
    Atlassian superseded
  - a task for Lenny's access, with a licensing caveat
- **Questions.** Notes added to Q-008 (the converged spec contract), Q-009, Q-014 (regulated control
  patterns), and Q-016 (the general coworker is becoming a commodity).
- **Hypotheses.**
  - Evidence added to H-005, H-007, H-008, H-009, H-011, and H-012.
  - New H-014: the harness can stand out by closing the gaps the beacons leave, such as routing
    questions to named experts, drawing compliance requirements from control owners, and tracing
    requirements into production.
- **Tasks.** `from:004` tasks added to goals 001 (2), 003 (1), 005 (1), and 006 (2).
- **Wiki.**
  - [pm-moves](pm-moves.md): outside definitions for critiquing a spec, deciding, clarifying, and
    defining by evals
  - [context-layer](context-layer.md): standards and expert knowledge as governed context
- **Kept out of the repo on purpose (C5):** findings that point to one industry, such as one
  country's regulator guidance, are summarized to Geoff privately instead.
