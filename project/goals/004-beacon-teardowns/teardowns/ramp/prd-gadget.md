# PRD (reconstructed): Gadget, the coordination agent

> Reconstructed from public sources for goal 004. **This is not Ramp's document.**
>
> **Labels:**
> - **said**: Ramp's own public account
> - **observed**: a third party saw it
> - **inferred**: our reconstruction, not stated anywhere
>
> Source keys resolve in [sources](sources.md). See [index](index.md) for how the PRDs fit together.
>
> Gadget itself appears only in the talk. Its **predecessors** are well documented, though: Notion
> agents that answer product questions and categorize feedback, automated status digests, and a
> release bot. This PRD uses them to fill in how it works, and labels which is which.

## At a glance

| | |
|---|---|
| Step in Ramp's loop | **Coordinate**, the 4th of 5 |
| Bottleneck it removes | PM attention: repeated inbound questions, chasing status, launch communications |
| Primary users | People with questions (sales, CX, execs, engineers); PMs, who own the answers and get fewer interruptions |
| Surfaces | Slack (a `#project-ops` channel is shown); writes to Linear; reads Notion (S1 slide 12:06) |
| Numbers (said) | "85% of questions that are being asked to PMs now are fully answered with AI" (S1 12:56). The predecessor, a product-Q&A agent, reported "85% of all questions take no human in the loop" (S16). **These may be the same statistic** |
| Predecessors (said) | A Notion "Product Q&A Oracle" (S32, S16), a "Sales Feedback Categorizer" (S32), weekly project updates generated from five sources (S33), Slack digests written for each audience (S18), the "ramp releases" bot (S17) |
| Evidence | One talk and one slide for Gadget itself. Several first-party and vendor sources for its predecessors. **Med** confidence on scope, **Low** on Gadget's own mechanics |

## Problem

- **Attention became the bottleneck.** Once coding stopped being the constraint, "the next
  bottleneck becomes human attention" (S1 10:40). PMs were "inundated with notifications," fielding
  the same questions again and again (S1 slide 12:06).
- **Process can't fix it.** More of it "slows down the builders"; less of it leaves "everyone
  confused" (S1 11:14).
- **The old workaround was a human escalations team.** A channel for "tough product questions" used
  to be staffed by a team that "just answered these questions all day cuz they kept deals moving"
  (S16).

## Principle

**"Every question is an API"** (S1 11:14). A recurring question resolves against the **formal
record** rather than a person, which works only if "the organization [is] legible to your agents"
(S1 11:49).

Legibility is an old Ramp habit:
- **Building in the open (2023).** "Every spec, design, decision, progress and status is published
  in project-specific Slack channels" (S49).
- **One source of truth.** Ramp consolidated work into Notion so that "both humans and AI could
  operate from the same source of truth" (S32).

## Users and jobs

| User | Job | Source |
|---|---|---|
| Salesperson | Find out what a feature is, how to sell it, whether it's "available in Brazil," the use case, the price | said (S1 12:22) |
| Salesperson or CX, on tough cases | Get an answer about a complex product configuration in "1 or 2 minutes" instead of about 30 | said (S16; predecessor) |
| Exec or stakeholder | Find out "Are we on track?", with evidence and the owner of the next step | said (S1 11:49) |
| Exec, legal, partnerships, board | Read summaries of Slack project channels written for their role | said (S18) |
| PM | Get status updates, roadmap upkeep, and follow-up on late deliverables done without doing them by hand | said (S1 11:49–12:22) |
| PM, at launch | Get a release report, help-center article, internal enablement material, and Slack announcement | said (S17 "ramp releases"; S1 12:22) |
| Owner of an unanswered question | Get the question routed to them. Their answer teaches the system | said (S1 12:22–12:56; S16) |

## Requirements

### Functional

| ID | Requirement | Label | Source |
|---|---|---|---|
| G1 | **Parse** each inbound question for intent: "What is being asked?" | said | S1 slide 12:06 |
| G2 | Resolve answers from the formal record: the roadmap, specs, and customer calls in Notion, plus Slack, Linear, and tickets | said | S1 11:14 |
| G3 | Answer status questions with evidence, including "who owns the next steps" | said | S1 11:49 |
| G4 | **Route** what it can't answer to the owner: "Who owns the answer?" | said | S1 slide 12:06; 12:22 |
| G5 | **Record** changes ("What changed?") and keep the roadmap up to date | said | S1 slide 12:06; 11:49 |
| G6 | Post status updates, and ping people who are late on deliverables | said | S1 12:22 |
| G7 | Answer go-to-market questions (feature, availability by region, use case, price) | said | S1 12:22 |
| G8 | Draft launch material: help-center article, blog post, customer email. The predecessor also wrote a release report covering context, a preview, Snowflake impact, and a summary of Slack work, plus internal enablement material | said | S1 12:22; S17 |
| G9 | **Close the loop:** questions answered by humans are "fed back into the system" | said | S1 12:56 |
| G10 | **The predecessor's review loop:** each agent answer goes into a database; an escalations team marks it right or writes the correct answer; a nightly agent sweeps the wrong answers "to figure out things that we might need to update in the docs" | said (predecessor) | S16 |
| G11 | **Knowledge corrections:** users flag stale answers in a feedback database, a custom agent drafts the correction, and a knowledge manager reviews and publishes it | said (general practice at Ramp) | S33 |
| G12 | Map inbound sales feedback to the roadmap, and "close the loop when features ship" | said (predecessor) | S32 |
| G13 | Generate weekly project updates "summarized from five different sources" and published to Slack | said (predecessor) | S33 |
| G14 | Cite the record behind each answer | inferred from "answers with evidence" | S1 11:49 |

### Context and integrations

- **Reads** (said, S1 11:14; slide 12:06):
  - Notion: roadmap, specs, customer calls
  - Linear: tasks and owners, status and roadmap, launch timing
  - Slack and tickets
- **Writes** (said): roadmap updates, status posts, pings, and answers fed back (S1). Also answer
  databases and doc corrections, per the predecessor (S16, S33).
- **Documentation** (said, S16): Ramp's product-operations team is "aligned against every product"
  and owns "impeccably good" documentation. Every failed support-agent session "is an immediate
  ping" to product ops to fix the docs. Gadget's answers depend on that docs discipline.

### Human in the loop and controls

- Humans answer what Gadget can't, and review answers after the fact. In the predecessor, the
  escalations team marked every answer right or wrong (S16). **Said.**
- The talk describes launch content as something Gadget "can write" or "can help write." Human
  editing is inferred.
- **Not public:**
  - whether writes to the roadmap need approval
  - whether customers ever see Gadget's answers

## How it works (reconstructed flow)

1. A question arrives in Slack.
2. **Parse** the intent.
3. Look it up in the record: Linear, Notion, Slack, tickets.
4. If Gadget is confident, it answers with evidence. **Route:** otherwise it sends the question to
   the owner.
5. **Record:** Gadget writes status changes to the record, and feeds human answers back.
6. **Nightly sweep** (predecessor): wrong or corrected answers become doc updates.
7. **Proactive work:** status digests, pings, and release packets.

## Architecture

- **Known:**
  - PARSE → ROUTE → RECORD, in Slack, backed by Linear and Notion (S1 slide 12:06).
  - The predecessor was built on **Notion custom agents**: "the first time we had a tool inside
    Ramp that you could use to reliably set up a fully autonomous agent that wasn't an engineering
    project" (S16). It hit limits ("It didn't have Snowflake") (S16).
- **Unknown:** whether Gadget runs on Notion agents, on Inspect's agent platform (200+ agents,
  S19), or on Glass.
- **A clue (round 2):** in April 2026, a "Product Question Agent" was one of the Notion agents
  listed inside Glass's agents panel (S78). The Notion agents were still running then, and Glass
  surfaced them rather than replacing them. Inspect's docs use a `@project-manager` status agent as
  their example of a custom agent (S20). Either could host Gadget.

## Open questions

- Is the talk's 85% the same statistic as the predecessor's 85%?
- What counts as "fully answered," and how is accuracy checked after the answer goes out?
- Where do fed-back answers live, and who validates them?
- How are pings governed (tone, frequency, opt-out)?

## Through our lens (goal 004, R3)

| Axis | Ramp's answer |
|---|---|
| First move | High-frequency, low-risk Q&A about status and product facts. It replaced a human escalations desk with an obvious payoff (answers in 1–2 minutes instead of about 30) |
| Deployment model | One shared agent for the organization, in Slack. The predecessor was a no-code Notion agent |
| Context approach | Federated reads over the systems of record, **plus writes back**: records updated, answers fed back, nightly sweeps into the docs. The context-building loop from DEC-011, running in production |
| Traces | Answer databases with a mark for each answer (predecessor); "Record: What changed?" |
| Controls | Human review of answers after the fact, and routing for unknowns |
| PM moves ([pm-moves](../../../../context/wiki/pm-moves.md)) | Managing delivery (status, dependencies), release (launch communications), in-market support (go-to-market Q&A). All context-bound |
| Delegation ([levels](../../../../context/wiki/path.md#delegation-levels)) | Q&A at **L4** (85% with no human; after-the-fact review). Launch content at **L2**. Record updates **L3–L4** (not public) |

## What transfers to a regulated enterprise (R4)

**Transfers:**
- **"Every question is an API"** against the formal record, which aims straight at H-004.
- **The review loop:** an answer database, a human marking each answer, and a nightly sweep into
  the docs. It's the cleanest public version of DEC-011's context-building loop, and it produces
  evidence of validation as it runs (H-012).
- **Legibility as a design goal.** Status and decisions published where agents can read them
  (H-013).

**Needs adapting:**
- *Regulated claims.* Answers about pricing, availability, and eligibility can count as regulated
  claims. Answer from approved sources only, with provenance, and mark answers internal-only.
  Customer-facing launch content goes through compliance review.
- *Records and access.* Q&A and status records may fall under retention rules, and answers must
  respect access tiers (C7, Q-014).

**Doesn't transfer as-is:**
- Pinging people who are late. In a matrixed enterprise it can read as surveillance (Q-013). It
  needs team opt-in and norms.
