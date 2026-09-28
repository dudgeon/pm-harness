# PRD (reconstructed): Ramp Research, the agentic data analyst

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
| Step in Ramp's loop | Supports **identify** and **define** (the quantitative half of "nail the job to be done") |
| Bottleneck it removes | "The data bottleneck." Questions piled up in `#help-data` behind one on-call analyst: "decisions wait and most questions go unasked" (S9) |
| Users | Anyone: sales ("what are our customers in Milwaukee?"), support, marketing, PMs (S17). Data-team members were the first users, since they could fix the docs (S16) |
| Surfaces | A Slack app: a public channel, private bot conversations, and alert and project channels (S9, S16). Later reachable from Glass (S2, S16) |
| Launched | Early August 2025 (S9) |
| Numbers (said) | 1,800+ questions from 300 users in the first ~6 weeks. In one 4-week stretch, 1,476 questions answered versus 66 in `#help-data`. "10–20x" more questions asked overall (S9) |
| Status | **Superseded as a product.** By March 2026 the CPO called it "outdated," replaced by "Snowflake CLI plus Claude plus skills" (S17), and a phase that was "quietly sunset" (S14). Its **context layer** lives on, as a skill bundle in both Glass and Inspect (S66) |
| Evidence | A detailed first-party post, a first-party video conversation, and CPO interviews. **High** confidence |

## Problem

"Data questions don't exactly crash the system, but they quietly slow every decision." The answer
arrives "after the decision window has narrowed" (S9).

## Requirements (all said, S9, unless marked)

| ID | Requirement | Label | Source |
|---|---|---|---|
| RR1 | Answer data questions in Slack, "24/7, in minutes – not hours" | said | S9 |
| RR2 | Aggregate and index the metadata from dbt, Looker, and Snowflake so the agent can find the right models | said | S9 |
| RR3 | Give the agent **domain docs** written by the domain owners on the analytics team, "organized into a file system" | said | S9, S16 |
| RR4 | Give the agent tools to "inspect column values, branch, and backtrack," reasoning "the way a human analyst would," rather than relying on vector search alone | said | S9 |
| RR5 | **No access to PII** | said | S9 |
| RR6 | Preview CSVs in the thread, so people can check results without opening BI tools | said | S9 |
| RR7 | Keep each thread stateful for multi-turn clarification | said | S9 |
| RR8 | Work in existing workflows, such as alert channels (diagnosing failed transactions) and project channels (scoping features) | said | S9 |
| RR9 | **Evaluate the context layer, not each answer.** Domain experts list high-priority concepts and write end-to-end tests. A dbt mini-framework asserts on intermediate steps: expected tool calls, table references, and query shape | said | S9 |
| RR10 | Let usage guide coverage: "as more questions got asked, it also guided them to what are the next tables to document" | said | S16 |
| RR11 | A headless API, so teams can customize it (planned in 2025) | said (planned) | S9 |

## How it evolved

1. **A custom GPT** covering "five or six" tables. One employee documented the columns with help
   from a data scientist. Its first 20–30 users said "this is absolutely wrong" (S16).
2. **Formalized by the data team.** Domain docs, evals, and monitoring (S16). It launched in
   August 2025 (S9).
3. **Uptake in Slack**, first in the public channel and then as a private bot: "my private
   consigliere … data person" (S16).
4. **Replaced** by skills for coding agents, via the Snowflake CLI, Claude, and a "data analyst
   skill" (S17). The CPO's four phases are Notion AI → Ramp Research → Snowflake skills → "interactive
   and self-improving" (S14).
5. The August 2026 report still lists "Ramp Research" among agents on Inspect (S19). **Resolved in
   round 2:** the name lives on as a *skill bundle*: "a skill bundle that we make available in
   different harnesses. We make it available in Inspect. We make it available in Glass" (S66,
   June 2026). It installs itself when someone connects Snowflake in Glass (S66). So the product
   was retired, but its context layer and skills carried over to every harness. In March 2026 its
   Slack channel, `#ask-ramp-research`, had 1,034 members (S55, observed).

## Human in the loop

- **Per-question review didn't scale.** "Our first approach … pinged domain owners for every
  in-domain question. This solution didn't scale" (S9). So Ramp moved human effort to **the
  context layer**: domain docs and tests.
- **The feedback loop is "update context, run tests, and confirm improvements"** (S9).

## Through our lens (goal 004, R3)

| Axis | Ramp's answer |
|---|---|
| First move | Data Q&A: high frequency, low risk, with an obvious payoff to the person asking. One of Ramp's earliest agents |
| Deployment model | A shared Slack app; later a skill any agent can load |
| Context approach | **A curated context layer:** indexed metadata plus domain docs written by humans, evaluated with tests. "The context layer behind Ramp Research is also an incredibly valuable technical asset" (S9) |
| Traces | Stateful threads, and evals that check intermediate steps |
| Controls | No PII. The context layer is owned by domain owners and tested |
| PM moves | Inputs to problem identification (1) and to shaping (3), on the quantitative side |
| Delegation | **L4** for answers (the AI answers, and domain owners check through tests, not per answer) |

**Why this matters for us.** Ramp Research is the clearest public case of **H-009**: the interface
was thrown away within months, and **the context layer survived** and moved into skills. It's also
a working model for the loop in **DEC-011**:
- humans own and validate the context layer
- tests measure its credibility
- usage shows where the gaps are

## What transfers to a regulated enterprise (R4)

**Transfers almost whole:**
- Domain docs owned by named experts.
- Evals over the context layer rather than review of every answer. That makes the quality of the
  context measurable (H-007, Q-010).
- No PII by design.
- Answers that show their working (SQL, CSV previews).

**Needs adapting:**
- *Controls on data access.* Row-level entitlements and the classification of warehouse data apply
  (C7).
- *Model risk.* Using agent-generated analysis in decisions may bring model-risk governance.
