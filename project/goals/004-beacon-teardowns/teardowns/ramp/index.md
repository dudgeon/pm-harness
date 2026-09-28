# Ramp teardown (004-D2): v1 plus round 2, 2026-09-27

> Goal 004's first deep teardown. It reconstructs Ramp's internal AI "software factory" as a
> **product vision** plus **one PRD per main feature**, as close to the real thing as public sources
> allow. Geoff asked for that level of fidelity on 2026-09-27.
>
> **Round 2 (same day)** went deep on Glass at Geoff's request, and tested his hypothesis that Glass
> is where most intent shaping happens. It added X timelines, about fifteen talks and interviews,
> job postings, the screenshots inside the launch articles, and a frame-by-frame read of the PM
> shaping skill. See [intent-shaping](intent-shaping.md) and the v2 [Glass PRD](prd-glass.md).
>
> **Where it comes from.** The first source is Ramp CPO Geoff Charles's talk at the Lenny & Friends
> Summit (S1, 2026-09-10), with its slides read from the video frames. The rest comes from 85 other
> sources ([sources](sources.md)), all public except one earlier research note of ours (S56). Almost
> everything is **Ramp's own account**. Independent observation is thin (see "Evidence").
>
> **Two Geoffs.** Geoff Charles is Ramp's CPO. Geoff owns this project.

## How to read it

- **Labels.** Every requirement is marked **said** (Ramp's account), **observed** (a third party
  or a public artifact), or **inferred** (our reconstruction).
- **Citations.** Sources are keyed S1–S86. Bare timestamps point into the talk (S1).
- **What each PRD covers.** Every PRD follows the same shape:
  - problem, users and jobs, measures, requirements, how it works, architecture
  - open questions
  - **Through our lens** (goal 004, R3)
  - **What transfers to a regulated enterprise** (R4)

## The documents

| Doc | What it covers | Step in Ramp's loop |
|---|---|---|
| [vision](vision.md) | The factory as one product: the problem, beliefs, principles, the loop, the platform, measurement, sequencing, operating model, tensions | all |
| [VOTC](prd-votc.md) | The Voice of the Customer insight agent | identify |
| [Ramp Research](prd-ramp-research.md) | The agentic data analyst, now superseded, and its context layer | identify, define |
| [Glass](prd-glass.md) (v2) | The AI coworker workspace, and the PM's define workflow ("the next contract"), including the product-shaping skill | define (and platform) |
| [Intent shaping](intent-shaping.md) | Tests the hypothesis that Glass is where most intent shaping happens. Verdict: partly supported | identify, define, build |
| [Inspect](prd-inspect.md) | The background coding agent and agent platform | build: code |
| [Review Buddy](prd-review-buddy.md) | The panel of AI code reviewers | build: review |
| [Testo](prd-testo.md) | The browser QA agent | build: test (acceptance) |
| [Gadget](prd-gadget.md) | The coordination agent: "every question is an API" | coordinate |
| [Autonomous loop](prd-autonomous-loop.md) | End-to-end fixes for small issues | improve |
| [sources](sources.md) | The source register (S1–S86) | — |

## What Ramp built, in brief

Ramp treats **how it builds** as a product. It works around a loop, identify → define → build →
coordinate → improve, and builds an agent wherever the loop is blocked. All the agents read and
write one formal record that Ramp keeps "legible to your agents." A general coworker (Glass) and a
shared agent platform (Inspect) sit underneath. The results Ramp reports:

- **Inspect** builds 75% of PRs.
- **Review Buddy** handles 93% of reviews.
- **Testo** caught 425 bugs in a month.
- **Gadget** answers 85% of the questions put to PMs.
- **The autonomous loop** fixes 60% of UX issues within 24 hours.

All of these are self-reported (S1). See [vision](vision.md).

**Is Glass the analog to a PM harness?** Partly.
- Glass is Ramp's designated front door for the **define** step, and the everyday coworker for
  non-engineers.
- But the shaping loop is a relay across surfaces, with skills carrying the method: discovery in
  VOTC, framing and research in Glass or Claude Code, the prototype in Inspect, and the record in
  Notion. The brief doesn't live in Glass ([intent-shaping](intent-shaping.md)).
- The closer analog to what DEC-007 describes is the **whole factory**: several agents, each with a
  single job, sharing one context layer. See Q-016.

## Through our lens, across the factory (goal 004, R3)

| Axis | What Ramp does |
|---|---|
| **First moves** | The context-bound, high-frequency, low-risk moves came first: data Q&A (2025), product Q&A (85% with no human), customer-signal synthesis. Coding came next. The PM define step and autonomous fixes came last. The rule: "find that one bottleneck that you think can 10x your company and just start there" (S1) |
| **Deployment model** | **Mixed on purpose.** Glass runs locally, one per person. Inspect is hosted and shared. The insight, coordination, and fix agents are shared services in Slack. Nothing is one "PM agent" |
| **Context approach** | One formal record (Notion, Linear, Slack, Snowflake, code) and procedural context in Git (Dojo skills, review rules, AGENTS.md). **Curated layers with named owners** sit on top: Ramp Research's domain docs are tested with evals, product-ops docs are fixed after every failed session, and VOTC keeps provenance |
| **Traces** | **Split.** Inspect traces every session end to end and links each PR to its session. VOTC answers carry "View trace." The loop carries one signal from start to finish. But Glass captures **nothing centrally, by design**, and Ramp names the cost: owners can't tell which skills work (S16) |
| **Controls** | Engineering controls, not regulatory ones: SSO, each person's own permissions, PRs under the human's identity, least privilege, sanitized replicas, review tiered by risk, release tiers, one-click approvals. The governance for data and model risk in a regulated setting is mostly absent from the public record |

## What transfers to a regulated enterprise (R4)

**Transfers:**
- **Legibility as a design goal:** "every question is an API," answered from the formal record.
- **Context loops with owners:** answer databases with human marks, nightly sweeps into the docs,
  evals of the context layer, and domain owners.
- **Procedural context in Git**, reviewed like code, with Git hidden from authors.
- **PRs under the human's identity**, plus attribution per prompt and session traces.
- **Review tiered by risk.** Ramp names a high-risk list (auth, identity, data access, network
  access, money movement). A regulated enterprise would define its own list the same way.
- **Testing across the role × entitlement matrix.**
- **Proposal cards** that record each human approval.
- **"The next contract"** as the shape of the spec handoff.

**Needs adapting:**
- *Data.* Customer data in VOTC; test data seeded from production for Testo.
- *Review policy.* "Automatically handled" review needs human attestation, tiered by risk.
- *Visibility.* Public-by-default sessions need need-to-know access.
- *Memory.* Mining people's Slack and calendars for memory raises privacy questions.
- *Customer-facing claims.* Go-to-market answers and launch copy need compliance review.
- *Models.* Choosing models across all providers runs into model-risk governance.

**Doesn't transfer:**
- The **mandate-and-leaderboard** adoption model, unlimited tokens, and "no tiered access based on
  role" (S14). These run against C6 (earned adoption) and C7. What *does* transfer is Ramp's own
  finding that "the product is the enablement," and that the people who got the most value were
  "the ones who installed a skill on day one" (S2).

## What this means for our project

Filed as questions, tasks, and evidence. See the wiki log entry for 2026-09-27.

1. **The unit of design may be a factory, not an agent.** DEC-007 says "a shared, persistent,
   deployed PM agent." Ramp instead builds one agent per bottleneck on shared context, plus a
   general coworker. This is logged as **Q-016** for goal 001, to research rather than decide now.
2. **Sequencing by bottleneck** is a candidate rule for choosing first moves (Q-006). Ramp's first
   moves were **context-bound Q&A**: data, product questions, customer signal. That fits H-003,
   H-004, and H-010.
3. **The spec contract (Q-008)** has a concrete public reference. It has three parts: evidence that
   the problem is real, requirements written for coding agents (with a human version and a more
   robust agent version), and a working prototype on the real codebase.
4. **Context-building loops work in production** (DEC-011, H-007).
   - The product-Q&A loop (a human marks each answer; a nightly sweep updates the docs) reached
     "85% … no human in the loop."
   - Ramp Research moved human effort from **checking each answer** to **evaluating the context
     layer**. Goal 006 should look closely at both.
5. **Traces are where the path gets locked in** (H-009, H-005).
   - Ramp's two main platforms made opposite choices. Inspect traces everything; Glass traces
     nothing.
   - Glass's team names the cost.
   - Ramp Research's interface was retired, and its context layer survived. That's the pattern
     H-009 predicts.
6. **Where the PM role ends up (Q-011):** factory builder, tastemaker, or GM, with 22 PMs in a
   company of 1,600 (S1, S18). For Ramp, judgment and taste stay human. Coordination and the
   inputs to identification get automated.
7. **Ramp's adoption model differs from ours (C6).** Ramp mandated, measured, and ranked usage.
   Only the product-led half of its playbook fits earned adoption.

Added in round 2:

8. **Skills carry the method; apps come and go (H-009).**
   - Ramp's PM shaping skill ran in Claude Code in March. By September the CPO placed define in
     Glass.
   - The same skill bundle (Ramp Research) runs in both Glass and Inspect (S66).
   - Design implication: invest in the skills and the record, and keep the host swappable.
9. **A front door wired to context earns adoption (C6, DEC-008, H-011).**
   - Glass went from 3 to 976 weekly users in four weeks with no launch announcement (S78).
   - But it was built for everyone first. PM skills arrived later, as a kit.
10. **The spec contract (Q-008) gains a discipline and shows a gap.**
    - The discipline, from the shaping skill:
      - a one-sentence framing gate
      - an evidence bar (quantified, attributed, honest about causality)
      - requirement IDs tied to evidence
      - closed questions with sources
      - research kept as files
    - The gap: the skill stops at "specific enough to prototype." Acceptance criteria appear only
      at the Inspect session boundary (S20).
11. **Nobody at Ramp owns the brief's home yet.**
    - A designer calls the missing project "source of truth" a blocker (S62).
    - Research tooling is "fairly chaotic" (S61).
    - Inspect's plan to hold "the brief… the research" isn't in its docs (S20).
    - A governed, shared place for the brief, its evidence, and its prototype is open ground for
      us (H-002, H-012).

## Evidence and gaps

- **Independent observation** is limited to:
  - public GitHub output from Inspect and Review Buddy (S21)
  - an HN thread on Inspect (S41)
  - open-source rebuilds (S42)
  - one attendee recap (S37)
  - YouTube comments (S38)

  Nobody outside Ramp has verified any speed or quality metric.
- **Paywalled:** the Pragmatic Engineer piece on Inspect (preview only, S19). The product-shaping
  skill in Peter Yang's paywalled post no longer matters: all 253 lines were read from the video
  frames (S55) and cross-checked against a public copy (S79).
- **Not found (round 2):**
  - a recording of Ramp's design-tooling demo (S83)
  - the promised write-up on Glass's distribution and auth
  - what's in Dojo's Product and Design kits
  - who has owned Glass since June 2026
- **Not shown on screen:** the talk's stat slides for 93%, 425, 85%, and 60% were never broadcast.
- **Corrections to the [first-pass scan](../../../../context/inbox/_processed/2026-09-27-beacon-scan.md)**
  (§0):
  - **The Glass article.** It's now recovered (S2), and it discloses the harness (the Claude Agent
    SDK, per S14). The daily memory pipeline mines past sessions, Slack, Notion, and Calendar.
    Linear appears in the initial memory, not the daily pipeline.
  - **The Inspect post.** It's dated 2026-01-12. The quote "engineers, product managers, designers"
    comes from Modal's case study (S23), not Ramp's post. Inspect v1 was a Chrome extension. PR
    share went 30% → 75%.
  - **The token-spend post (S10)** is about Ramp's customer product, not internal tracking.
  - **Ramp Research** has been superseded by skills.
- **Open questions** are listed in each PRD. The biggest ones:
  - what "automatically handled" means
  - Testo's data handling
  - who owns Glass now
  - whether Gadget is a product or an automation

## Next steps for this teardown

See [goal 004's tasks](../../tasks.md). In short:
- Close the PRDs' open questions as new public material appears.
- Review the fidelity and format with Geoff.
- Reuse the format, scaled to the evidence, for the next beacons.
