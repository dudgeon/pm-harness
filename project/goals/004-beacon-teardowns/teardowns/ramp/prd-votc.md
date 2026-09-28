# PRD (reconstructed): Voice of the Customer (VOTC), the customer-insight agent

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
| Step in Ramp's loop | **Identify**, the 1st of 5 |
| Bottleneck it removes | Sifting customer pain out of noisy, siloed, very high-volume signal. "The first thing we invested in" (S17) |
| Primary users | PMs; anyone who asks in Slack; account owners, who get personalized audio briefings. Other agents also consume it: Glass for "nail the job to be done," and the autonomous loop for ranking work (S1 slides) |
| Surfaces | The VOTC Agent (a Slack app with "View trace"), the Customer Insights Dashboard (probably "the Explorer"), personalized podcasts (S1 slides 05:00, 05:36). In March 2026 the Slack agent answered in `#ask-votc-agent`, with Braintrust traces behind each answer (S55, observed). It runs on the Inspect platform (S19) |
| Stack (said, from a slide) | Gong, Zendesk, and Datadog → Snowflake plus a turbopuffer semantic index → per-item summaries (GPT-5 + Gemini) → UMAP + HDBSCAN clustering → Prefect schedule → the Explorer and Slack (S1 slide 05:00). Ramp's ML and agent platform runs on Prefect (S34) |
| Numbers (said) | A demo covered 90 days of tickets and chats "in 8 minutes," which it compared with "8 days for a human" (S17) |
| Lineage | "Toby," which analyzed call summaries (2024, S35) → `#gong-hate` → the VOC agent, which "replaced a person that we hired" (S17, Mar 2026) → VOTC, with three surfaces (S1, Sep 2026) |
| Evidence | The CPO's talk plus three slides, two CPO interviews, and a 2024 Ramp blog post. **Med-High** confidence on architecture, **Low** on governance |

## Problem

Customer pain "lives somewhere," and that somewhere is everywhere:
- Gong, Zendesk, LogRocket, surveys
- "very angry email to an executive" (S1 04:04)
- Salesforce notes, in-app chats, and emails to account managers (S17)

Ramp has "50,000 plus customers … over a million end users," so "the question is around like how
do you actually sift through all this noise?" (S17). Plain LLM use can't cope: "a 1 million token
window, that's less than 0.5% of Gong transcripts at Ramp" (S1 04:04).

## Users and jobs

| User | Job | Source |
|---|---|---|
| PM | Answer "any question that product managers have around their persona, their pain points, their workflows, and the gaps of their products" | said (S17) |
| PM | Go deeper in a conversation: pull customer quotes, LogRocket sessions, and customer IDs, then "draft … in my Gmail account" an email asking to book meetings | said (S17) |
| PM | Pick "exactly which customers to talk to," because "the data is traceable" | said (S1 05:46) |
| PM or researcher | Get customers' own words (e.g., how admins describe credit-limit frustrations) to design a survey | said (S1 slide 05:36) |
| Account owner | Hear last quarter's feedback from their accounts as a ~12.5-minute, two-host audio briefing covering praise, gripes, and churn risk | said (S1 slide 05:36) |
| Leadership | Weigh pain by money: VOC is "fully linked to … the contribution profit and the … value at risk for our company" | said (S18) |
| Other agents | Glass (user research), the autonomous loop (ranking) | said (S1 slides 06:40, 13:56) |
| Designer or PM, recruiting | VOTC sits inside a wider research system. Agents find the right customers, mine past calls for prior research, and draft a research plan. A research team of three schedules the sessions. Product and design ran "150, 200 research sessions this month" | said (S69, S61) |

## Goals and success measures

- **Said:**
  - Get people "access to this data as fast as possible," without replacing customer
    conversations (S1 05:46).
  - Research that used to take two weeks for five customer interviews is now "basically gone" for
    research on pain (S18).
- **Said (demo):** 90 days of tickets and chats in 8 minutes versus about 8 days for a person (S17).
- **Not public:** usage, accuracy, or impact metrics.

## Requirements

### Functional

| ID | Requirement | Label | Source |
|---|---|---|---|
| V1 | Take in every customer signal: Gong recordings, Salesforce notes, in-app surveys, support tickets, in-app chats (including chats with Omni, Ramp's in-product AI), emails to account managers, product sessions (LogRocket, Datadog), and incidents | said | S1 04:04; slides; S17 |
| V2 | Join the signal to the warehouse: Snowflake data and product analytics | said | S17 |
| V3 | Normalize each item: "AI reads each item into a consistent summary" | said | S1 slide 05:00 |
| V4 | Store prepared feedback **with its source** (Snowflake), and index it semantically (turbopuffer) | said | S1 slide 05:00 |
| V5 | Cluster comments into "clear themes and product areas" (UMAP + HDBSCAN) | said | S1 slide 05:00 |
| V6 | Know the product: offerings, features, documentation, and team structures | said | S1 04:40; slide 05:36 |
| V7 | Let the user pick sources for a question (support tickets, chat logs, sales research, feature requests) and a time window | said (demo) | S17 |
| V8 | Answer by finding "the relevant group" and checking the source. Every answer links to a **trace** | said | S1 slides 05:00, 05:36 |
| V9 | Keep a multi-turn thread going deeper: quotes, sessions, customer IDs, drafted outreach | said (demo) | S17 |
| V10 | Extract "every single emotion and every single pain point," and tie each one to contribution profit and value at risk | said | S18 |
| V11 | A dashboard: filters, leading themes with counts, and on-demand "Generate analysis" | said (slide) | S1 slide 05:36 |
| V12 | A personalized podcast "tailored to you as the account owner" | said (slide) | S1 slide 05:36 |
| V13 | Run on a schedule (Prefect) | said (slide) | S1 slide 05:00 |
| V14 | Serve other agents and processes. Examples: the GA release template asks "Are customers raving about this (LLM on Zendesk tickets, Sprig surveys, and Gong transcripts)" | said | S40; S1 slides |
| V15 | Map items to accounts, and dedupe across sources before counting | inferred (from V12 and the counts) | S1 slide 05:36 |

### Human in the loop and controls

- **Humans own the judgment.** VOTC decides *which* customers to talk to, not whether to talk to them.
  Research on *solutions* still happens with people, by putting a prototype on the customer's own
  data in front of them: "walk me through like what are you thinking" (S18). **Said.**
- **Traceability** ("View trace"; each item keeps its source) is the visible quality control.
  **Said.**
- **Not public:**
  - PII handling
  - who can see which accounts
  - retention
  - how summaries and clusters are evaluated

## How it works (reconstructed flow)

1. **Gather**, on a Prefect schedule: new calls, tickets, chats, sessions, surveys, and emails.
2. **Summarize** each item consistently, and keep its source.
3. **Remember and organize:** Snowflake plus turbopuffer, then UMAP + HDBSCAN themes mapped to
   product areas, and weighted by contribution profit and value at risk (S18).
4. **Deliver:**
   - the dashboard
   - the Slack agent (answers with traces, and multi-turn follow-ups that can draft outreach)
   - quarterly personalized podcasts
5. **Feed** other agents: Glass (define), the autonomous loop (prioritize), and the release review
   (is anyone "raving"?).

## How it evolved

| When | What | Source |
|---|---|---|
| 2024 | "agentic AI to analyze hundreds of thousands of customer calls and generate custom summaries for teams… affectionately named **Toby**" | S35 |
| 2025 | Feb: synthesizing customer data is "basically now fully automated via… AI"; internal teams build the pipelines. Dec: the GA template uses an LLM over tickets, surveys, and Gong | S18 (quoting Feb 2025), S40 |
| Early | `#gong-hate`: a daily firehose of complaints that "got out of hand really quickly" | S1 04:40 |
| Dec 2025 | A "voice of the customer analytics suite" filters LogRocket sessions for rage clicks and summarizes them. A UXR tool generates research questions and finds "the people that you should talk to" | S62 |
| Mar 2026 | The "voice of the customer" agent "replaced a person that we hired"; 8 minutes versus 8 days in the demo | S17 |
| Aug 2026 | `#gong-love`, a nightly sentiment bot, sits alongside `#gong-hate` | S54 (@eglyman, 2026-08-10) |
| Sep 2026 | VOTC with three surfaces, now consumed by Glass and the autonomous loop | S1 |

The research-plan side isn't one tool. In April the head of design said it lives "in Slack, slash
in Notion… every time the tool changes, we are like following it. So it's actually fairly chaotic"
(S61).

## Open questions

- Scale, freshness, and cost.
- How summaries and clusters are checked for accuracy.
- PII and access control.
- What "the Explorer" is.
- How contribution profit and value at risk are attached to each pain point.

## Through our lens (goal 004, R3)

| Axis | Ramp's answer |
|---|---|
| First move | Problem identification. "The first thing we invested in" (S17). A judgment move whose *inputs* got automated, which replaced a hired role |
| Deployment model | A shared, scheduled pipeline, plus a shared Slack agent. Results are pushed to people (podcasts) as well as pulled |
| Context approach | **Hybrid** in our [context-layer](../../../../context/wiki/context-layer.md) terms: a curated, derived layer (summaries, clusters, money weights) whose provenance points back into the systems of record |
| Traces | "View trace" on answers, and every item keeps its source |
| Controls | Traceability is the only visible one. PII handling and access control aren't public |
| PM moves | Problem identification (1) and in-market signals (7) |
| Delegation | **L2**: the AI synthesizes and drafts outreach, and the human decides which problem matters |

## What transfers to a regulated enterprise (R4)

**Transfers:**
- Synthesis with provenance from every item back to its source (H-012).
- Weighting pain by money (contribution profit, value at risk). It turns empathy inputs into
  something a business case can use.
- Personalized digests pushed to account owners. That's individual value, arriving as a byproduct
  (H-011).
- One shared insight service consumed by other agents: build once, use many times (H-009).

**Needs adapting:**
- *Customer data.* Calls, tickets, and chats hold customer PII and may be regulated
  communications. The work needs classification, minimization, access tiers, and retention (C7,
  Q-014).
- *External models.* Sending that content to external models needs third-party AI approval.
- *Complaint handling.* Regulated complaint handling has its own process. VOTC-like analysis can
  inform it, but can't replace it.
- *Model risk.* Summaries, clusters, and money weights all shape prioritization.

**Doesn't transfer as-is:**
- The "hate" framing.
- Drafting outreach emails to customers straight from an agent without communications review.
