# PRD (reconstructed): the autonomous small-issue loop

> Reconstructed from public sources for goal 004. **This is not Ramp's document.**
>
> **Labels:**
> - **said**: Ramp's own public account
> - **observed**: a third party saw it
> - **inferred**: our reconstruction, not stated anywhere
>
> Source keys resolve in [sources](sources.md). See [index](index.md) for how the PRDs fit together.

## At a glance

| | |
|---|---|
| Step in Ramp's loop | **Improve**, the 5th of 5, which then starts the loop again |
| What it is | An "autonomous agent [that] owns the whole loop" for small issues, from signal to shipped fix to knowledge-base update (S1 slide 13:56). It's built from Inspect automations, Slack proposals, and VOTC |
| Bottleneck it removes | PM attention spent on small reactive fixes, "the dopamine hit" (S1 12:56–13:28) |
| Users | Whoever reports an issue (customers, sales, staff). The owning team approves with one click |
| Numbers (said) | "60% of UX issues … are fixed within 24 hours" (S1 14:01) |
| Related loops (said) | OCA for incidents: "575 of the 1,220 PRs merged to address incidents" in 4 weeks (S28). Ramp Labs' self-maintaining app (S29) |
| Evidence | The talk and a slide, the Inspect docs, CPO interview demos, and related first-party posts. **Med** confidence on the steps, **Low** on policy |

## Principle

"Autonomous agent owns the whole loop. **One signal stays attached to its context, decisions,
code, and outcome**" (S1 slide 13:56).

"Humans are in the loop only just barely. Thousands of little loops … so you can focus on the big
ones" (S1 14:01).

The Head of Engineering puts it more generally: "feedback-loop agents take that signal, implement
it, merge it, validate post-deploy, continuously" (S26).

## The eight steps (said, from the slide at 13:56 and speech at 13:28–14:01)

| # | Step | What happens | System | Supporting evidence |
|---|---|---|---|---|
| 01 | Route | To the right team | — | A repo classifier routes Slack prompts (S7) |
| 02 | Dedupe | Match against the Linear backlog | Linear | Inspect is integrated with Linear's agent API (S24) |
| 03 | Prioritize | Rank the work: "It counts. It ranks." | VOTC + Snowflake | See [VOTC](prd-votc.md) |
| 04 | Investigate | Reproduce the issue and plan the fix | Inspect | |
| 05 | Approve | One click in Slack: "Hey, is this ready to go? I'm ready to code." | Slack | Documented as `post_automation_proposal`, "an Inspect-managed Slack card with Accept and Reject actions" (S20) |
| 06 | Build | Write the code | Inspect | |
| 07 | Verify | Tests and CI/CD | GitHub | Review Buddy and Testo presumably run too (inferred) |
| 08 | Update | Update the knowledge base at launch | Notion | So that Gadget and support can answer questions about the fix (inferred) |

## Other requirements

| ID | Requirement | Label | Source |
|---|---|---|---|
| L1 | Take in issues from customers, salespeople, and staff, including UX channels, escalations, and confused support tickets | said | S1 14:01; S17 |
| L2 | Handle only "small things," and leave larger work to PMs | said | S1 13:28 |
| L3 | Carry one signal end to end with its context, decisions, code, and outcome | said (slide) | S1 slide 13:56 |
| L4 | Get a human's one-click approval before any code is written | said | S1; S20 |
| L5 | For escalations and support tickets, "AI takes the first step… creates the actual PR" for "the PM or the product operator or even the engineer to review and ship" | said | S17 |
| L6 | Run "thousands" of loops in parallel. Automated sessions now outnumber human ones in Inspect | said | S1 14:01; S27 |
| L7 | A policy for what counts as "small," based on risk, blast radius, and area of code | inferred (a policy must exist) | none |

## Related Ramp loops (said)

| Loop | Summary | Human control | Source |
|---|---|---|---|
| **OCA**, the on-call assistant | Runs on incidents and on customer tickets escalated to engineering. It posts an update at about 5 minutes and a report at about 13, and asks Inspect for a fix PR. "575 of the 1,220 PRs merged to address incidents" in 4 weeks | "nothing it triggers gets merged without a human" | S28 |
| **Self-maintaining Ramp Sheets** (Ramp Labs) | An agent writes a Datadog monitor for each merged PR (1,000+ monitors). Monitor alerts start Inspect fix sessions. There's also nightly QA | "no code is merged without engineer review" | S29 |
| **Security agent team** | About 100 security issues fixed in 6 days: a coordinator, detectors, adversarial managers (which rejected 40% as false positives), a validator, and a fixer | "without a human in the loop (until PR review)" | S43 |
| **Release gate** (Dec 2025) | "teams can ship to early access tier whenever they want but need review for general release… Leadership has 48h to review or it ships" | review at GA, with a deadline | S40 |

## Open questions

- What qualifies as "small," and who set the policy?
- The 60%: what's the denominator, and what happens to the other 40%?
- Does the approver see the plan, the diff, or both?
- Does the reporter hear back when the fix ships?

## Through our lens (goal 004, R3)

| Axis | Ramp's answer |
|---|---|
| First move | Small UX fixes from in-market signals. They're frequent and low-stakes, and it's obvious when one lands |
| Deployment model | Shared automations on Inspect, tied together through Linear, Slack, GitHub, and Notion |
| Context approach | Uses the context the other agents built (VOTC demand, the Linear backlog, the codebase), and writes back to the knowledge base |
| Traces | **One signal carries its context, decisions, code, and outcome from start to finish.** This is the most complete trace *design* in the talk |
| Controls | One-click approval before code. Human merge review in the related loops. CI/CD. A release gate at GA |
| PM moves | In-market support (7) → problem identification (1) → delivery (4) → release (6), for small items |
| Delegation | **L3**: the AI does the work, and a human approves with one click. Close to L4 in effort |

## What transfers to a regulated enterprise (R4)

**Transfers:**
- **End-to-end traceability** of one signal through its context, decisions, code, and outcome. It's
  an audit trail already in the shape change management needs (H-012).
- **Proposal cards with Accept and Reject.** A clean, recorded point of human approval.
- **Humans stay the merge gate** in the related loops (OCA, Ramp Labs), even when agents do
  everything else.

**Needs adapting:**
- *Risk tiers.* The policy for which changes can take one-click approval must be explicit and signed
  off by whoever owns change management. Anything that touches customers, money, or regulated
  disclosures probably needs more than one click (C7).

**Doesn't transfer as-is:**
- 24-hour fixes, where release windows are fixed. The loop can still run up to the release gate.
