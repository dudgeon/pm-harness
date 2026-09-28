---
source: Geoff Charles (Ramp CPO), "What product looks like when coding is solved", a talk at the Lenny & Friends Summit (presented by Stripe). YouTube https://youtu.be/ZG8Mf3P9xzI, uploaded 2026-09-25, 19:31 long. Geoff passed it along in chat on 2026-09-27.
goal: 004
tags: [beacons, ramp, teardown, primary-source]
---

# Ramp CPO talk: "What product looks like when coding is solved" (digest)

> **Two Geoffs.** The speaker is **Geoff Charles**, Ramp's CPO. He isn't Geoff, who owns this project.
> This digest always calls the speaker "Charles".

## About this source

- **What it is.** A first-party conference talk by Ramp's CPO. Everything in it is what Ramp
  **says**; none of it is independently observed. All figures are self-reported.
- **How it was captured** (2026-09-27):
  - YouTube's auto-generated English captions: 574 segments, about 3,300 words.
  - Frames pulled from the 1080p video, to read the slides.
  - The full caption transcript and a raw slide log are kept **locally, outside git**, in
    `_local/` (self-ignored), because the repo is public and the talk is someone else's work.
    This digest keeps short quotes with timestamped links, so each one can be checked against the
    video.
- **Caption caveats.**
  - Product names were checked against the slides: VOTC, Glass, Inspect, Review Buddy, Testo, and
    Gadget.
  - The captions say "gadgets" (lowercase, plural) at 11:14, but the slide shows one agent named
    **Gadget**.
  - "Lemons" in the captions means the 24 Hours of LeMons race.
- **Spoken, not shown.** The broadcast never showed a slide for the 93%, 425-bug, 85%, or 60%
  figures, or for the three PM tracks. Those rest on speech alone.

## Thesis (00:06–03:44)

- **The racing analogy.** The driver accounts for about 15% of a race result. "The best drivers in
  the world can only perform up to the level of the system. Winning the race is about removing the
  bottlenecks around the driving" ([01:14](https://youtu.be/ZG8Mf3P9xzI?t=74)).
- **Pit stops.** They went from 67 seconds in the 1950s to 1.8 seconds today. The gain didn't come
  from mechanics working harder; teams found the bottlenecks and iterated through specialized
  functions, better technology, and more practice. In F1, about 90% of a car's parts change every
  year. "What if 90% of your code changed every year? Because that is the bar"
  ([01:48](https://youtu.be/ZG8Mf3P9xzI?t=108)).
- **The clock.** For product, "the clock starts when there's pain and it leaves when the customer
  has a product that solves it. AI simply removes the bottleneck, but moves it"
  ([02:23](https://youtu.be/ZG8Mf3P9xzI?t=143)). The winning team finds the next bottleneck
  fastest.
- **The bottleneck is now the PM.** Engineers have automated much of their own work: "Be as lazy as
  engineers." Now "the bottleneck has now shifted to us." More things need defining, coordinating,
  shipping, testing, and releasing, "and so we need to invest in our own factory. The speed of this
  loop determines the outcome of the race" ([03:30](https://youtu.be/ZG8Mf3P9xzI?t=210)).
- **Slide (03:44).** A loop of IDENTIFY → DEFINE → BUILD → COORDINATE → IMPROVE, titled "The
  1.80-second software factory."

## 1. Identify (04:04–05:46): the customer-insight agent ("Voice of the Customer")

- **The problem.** Pain is scattered across Gong, Zendesk, LogRocket, surveys, and angry emails to
  executives. "Context lives all over the place. Too many silos, too many opinions." Scale defeats
  plain LLM use: "a 1 million token window, that's less than 0.5% of Gong transcripts at Ramp"
  ([04:04](https://youtu.be/ZG8Mf3P9xzI?t=244)).
- **The first version.** A Slack channel that posts customer complaints every day (on screen:
  `#gong-hate`). It "got out of hand really quickly," so they "had to redesign from scratch"
  ([04:40](https://youtu.be/ZG8Mf3P9xzI?t=280)).
- **The rebuild.** A "customer insight agent" that pulls from every source, using "traditional ETL
  and pipelines," vector search, and clustering. It knows the product, the teams, and the features,
  and anyone in the organization can use it ([04:40](https://youtu.be/ZG8Mf3P9xzI?t=280)).
- **Slide: the pipeline (05:00).**
  1. *Gather:* "Feedback arrives from sales calls, support tickets, product sessions, incidents, and
     more." (Logos: Gong, Zendesk, Datadog.)
  2. *Remember:* Snowflake stores the prepared feedback and its source, and a semantic index
     (turbopuffer) finds similar conversations.
  3. *Organize:* UMAP + HDBSCAN clustering groups comments "into clear themes and product areas."
  4. *Deliver:* Prefect runs the workflow on a schedule, and "the Explorer" and Slack deliver it.

  The models are GPT-5 and Gemini. "AI reads each item into a consistent summary, then groups
  related feedback. When someone asks a question, it finds the relevant group and checks the
  source."
- **Distribution.** They tried several surfaces: a Slack agent, an HTML dashboard, and a daily "hate
  podcast" ([05:13](https://youtu.be/ZG8Mf3P9xzI?t=313)).
- **Slide: three surfaces (05:36).** Branded "Voice of the Customer," with knowledge areas for
  customer feedback, product offerings, team structures, documentation, product features, and
  trends and insights.
  - *VOTC Agent (Slack).* A PM asks how admins phrase complaints about credit limits. The answer has
    a **"View trace"** link and draws on verbatim language from "Gong calls, Zendesk tickets, and
    Omni chats."
  - *Podcast.* "Customer Love, Customer Hate — The Verbatim Cut (~12.5 min)," a "two-host breakdown
    of last quarter's customer feedback, tailored to you as the account owner."
  - *Customer Insights Dashboard.* Filters by source, product area, cluster size, and time frame. It
    lists "leading customer themes" with counts (e.g., 77 clusters from 643 observations for one
    product area) and has a "Generate analysis" button.
- **The point.** Get the data to people fast. "That doesn't mean don't talk to customers, it means
  you actually identify exactly which customers to talk to. Because the data is traceable"
  ([05:46](https://youtu.be/ZG8Mf3P9xzI?t=346)).

## 2. Define (05:46–07:57): Glass

- **The wrong starting point.** Generic AI tools open by asking "What do you want to build?" (the
  slide at 06:14 shows a grid of them). "Is that really the best starting point?" "The goal with AI
  is to connect it to your systems" ([06:18](https://youtu.be/ZG8Mf3P9xzI?t=378)).
- **Glass.** "We built our own AI agent called Glass, and we gave it all the context it needs to do
  the work." It connects to Snowflake data and to user research, so it can "nail exactly the job to
  be done," with both qualitative and quantitative specificity
  ([06:18](https://youtu.be/ZG8Mf3P9xzI?t=378)).
- **AI as tech lead.** Glass understands product strategy, "how we define product specs," and the
  codebase. So instead of asking an engineer "Is this possible? Would this break something? What
  am I missing?", a PM asks AI: "now AI is your tech lead"
  ([06:51](https://youtu.be/ZG8Mf3P9xzI?t=411)).
- **Prototypes.** Glass knows the product principles, the design system, and the codebase, so PMs
  can "define and build a prototype that actually works within your product"
  ([06:51](https://youtu.be/ZG8Mf3P9xzI?t=411)).
- **"The next contract."** Engineering doesn't want a prototype alone or a long spec alone. It wants
  "the combination of qualitative and quantitative data to convince them that this is a problem,
  the actual requirements that they can use for their coding agents, and a prototype that they can
  actually get inspired by. That is the next contract"
  ([07:24](https://youtu.be/ZG8Mf3P9xzI?t=444)).
- **Slide: Glass's inputs (06:40–07:32).**
  - *Nail the job to be done:* goals and the north star metric; user research (the VOTC agent); data
    (Snowflake, Hex).
  - *Define the requirements:* product strategy (Notion); a product spec template stored as a
    **SKILL.md**; the existing codebase (via Inspect).

## 3. Build (07:57–10:40): Inspect, Review Buddy, Testo

- **The next bottleneck.** "When we focus on one bottleneck, the next one appears. The first
  bottleneck was coding" ([07:57](https://youtu.be/ZG8Mf3P9xzI?t=477)).
- **Inspect.** Ramp built its own coding agent "because we wanted to have a strong harness" that
  "really understood our codebase." It works in Slack and is "fully provisioned." It "can run under
  5 seconds" (probably its startup time; the talk doesn't say). It returns "a deployed preview" that
  the PM can use ([07:57](https://youtu.be/ZG8Mf3P9xzI?t=477)).
  - *Results.* "Anyone at Ramp can now code": 1M sessions, 75% of PRs built by Inspect, and 1,000
    PRs "over the last month" from non-engineers. The period is spoken, not on the slide
    ([08:29](https://youtu.be/ZG8Mf3P9xzI?t=509)).
  - *A caveat.* Coding agents work best with "a strong architecture and a strong codebase," and that
    widens how much of the company can use AI ([08:29](https://youtu.be/ZG8Mf3P9xzI?t=509)).
  - *Slide (08:38).*
    - An Inspect Slack thread ends in "PR merged," with buttons for *Open preview*, *View session*,
      *Archive*, and *Start child session*.
    - The web UI shows a session's plan, "Worked for 21 seconds," and a **per-session cost**
      ($6.94).
    - The sidebar lists "Testo."
- **Review Buddy.** Once code volume grows, review becomes the bottleneck. Review Buddy understands
  the codebase, the quality checks, and the security concerns. It "finds the right human reviewer
  to loop in." It also reads "all the prompts that led you to build that code, so it can actually
  audit how you used AI in the first place"; review is "grounded in visible context"
  ([09:01](https://youtu.be/ZG8Mf3P9xzI?t=541)).
  - *Results.* "93% of our PRs are now automatically handled by Review Buddy," so senior engineers
    spend their time on the 7% that raise questions of correctness or risk
    ([09:35](https://youtu.be/ZG8Mf3P9xzI?t=575)). The talk doesn't define "automatically
    handled."
  - *Slide (09:12).* A GitHub comment from `ramp-reviewbuddy-2-of-2[bot]` describes a
    race-condition bug and is tagged "Found by: Codex, Logic." It promises to "respond and resolve
    this comment once the issue is addressed," then proposes a fix when the author asks.
- **Testo.** Testing is the next bottleneck, and it used to be PM work: spinning up QA
  environments, tweaking fixtures, clicking through screens
  ([09:35](https://youtu.be/ZG8Mf3P9xzI?t=575)).
  - *What it does.* Testo is "a browser-based QA agent." It "spins up the product in 100 different
    combinations based on the actual production data that we have access to" and "runs in the
    product like a user." It takes natural-language instructions such as "pay an invoice, but
    amortize it." It returns blocking feedback (bugs) plus design and quality feedback, including
    breaks from the design system ([10:08](https://youtu.be/ZG8Mf3P9xzI?t=608)).
  - *Results.* "Testo in the last 30 days has caught 425 bugs," and fixes go back through the loop
    ([10:40](https://youtu.be/ZG8Mf3P9xzI?t=640)).
  - *Slide (10:18).* A results table with columns for vertical and role, live setting, QA
    screenshot, Preview screenshot, and result. The rows cover admin and regular users at
    accounting firms and at financial institutions, each with a pass/fail verdict.

## 4. Coordinate (10:40–12:56): Gadget

- **The next bottleneck is human attention.** PMs drown in notifications. Too much process slows
  builders down; too little leaves everyone confused ([10:40](https://youtu.be/ZG8Mf3P9xzI?t=640)).
- **"Every question is an API."** Gadget "understands the intent of these questions and connects it
  to the formal record": the roadmap, specs, and customer calls in Notion, plus Slack, Linear, and
  tickets ([11:14](https://youtu.be/ZG8Mf3P9xzI?t=674)).
- **Legibility.** "The agent needs to be able to understand and read the organization. And the
  organization needs to be legible to your agents" ([11:49](https://youtu.be/ZG8Mf3P9xzI?t=709)).
- **Status.** Gadget answers "Are we on track?" with evidence, and knows who owns the next steps.
  It also updates the roadmap, posts status updates, and "pings people who are late on their
  deliverables" ([11:49](https://youtu.be/ZG8Mf3P9xzI?t=709)).
- **Go-to-market questions.** It answers sales questions: what a feature is, how to sell it,
  whether it's "available in Brazil," the use case, and the price. What it can't answer, it routes
  to the right person ([12:22](https://youtu.be/ZG8Mf3P9xzI?t=742)).
- **Launch content.** It drafts help-center articles, blog posts, and customer emails
  ([12:22](https://youtu.be/ZG8Mf3P9xzI?t=742)).
- **Results.** "85% of questions that are being asked to PMs now are fully answered with AI." The
  rest "are answered and fed back into the system" ([12:56](https://youtu.be/ZG8Mf3P9xzI?t=776)).
- **Slide (12:06).** "Chaotic inbound" feeds into Gadget, which "coordinates context" in three
  steps: PARSE ("What is being asked?"), ROUTE ("Who owns the answer?"), and RECORD ("What
  changed?"). Output goes to `#project-ops` and to Linear: tasks and owners, status and roadmap,
  launch timing.

## 5. Improve (12:56–14:33): autonomous small loops

- **The trap.** PMs gravitate to small, reactive, visible wins, "the dopamine hit," and that is "a
  huge mistake." "You need to automate your way out of these small loops"
  ([13:28](https://youtu.be/ZG8Mf3P9xzI?t=808)).
- **The loop.** "For most small things, an AI fully runs the loop." It routes to the team, matches
  against the Linear backlog, dedupes, counts, ranks, and plans. It then asks a human in Slack
  whether it's ready to code. It writes the code, runs tests and CI/CD, and updates the knowledge
  base at launch ([13:28](https://youtu.be/ZG8Mf3P9xzI?t=808)). "Humans are in the loop only just
  barely" ([14:01](https://youtu.be/ZG8Mf3P9xzI?t=841)).
- **Results.** "60% of UX issues" that customers, salespeople, or Ramp itself spot "are fixed within
  24 hours" ([14:01](https://youtu.be/ZG8Mf3P9xzI?t=841)).
- **Slide (13:56).** "Autonomous agent owns the whole loop. One signal stays attached to its
  context, decisions, code, and outcome." The eight steps, with the system each uses:

  | # | Step | What happens | System |
  |---|---|---|---|
  | 01 | Route | right team | |
  | 02 | Dedupe | match Linear | Linear |
  | 03 | Prioritize | rank the work | VOTC + Snowflake |
  | 04 | Investigate | repro + plan | Inspect |
  | 05 | Approve | one click | Slack |
  | 06 | Build | write the code | Inspect |
  | 07 | Verify | test + CI/CD | GitHub |
  | 08 | Update | knowledge base | Notion |

## Three questions (14:33–17:55)

- **"How do we know we're moving faster?"** Velocity is hard to quantify. The answer is to hire
  "a driver that knows what speed looks like," put them in charge, and let them challenge you
  ([14:33](https://youtu.be/ZG8Mf3P9xzI?t=873), [15:06](https://youtu.be/ZG8Mf3P9xzI?t=906)).
- **Budget.** Resources are limited, "in terms of engineers or simply with tokens." Audi's 2006
  fuel-efficiency strategy is the example: "constraints force you to choose a dimension in which
  you can be world-class. So embrace your constraints, but not your bottlenecks." Find the one
  bottleneck that could 10x the company "and just start there"
  ([15:39](https://youtu.be/ZG8Mf3P9xzI?t=939), [16:12](https://youtu.be/ZG8Mf3P9xzI?t=972)).
- **The future role of product.** PMs being "out of the loop for a lot of things that engineers can
  drive" is a good thing. Charles sees three tracks
  ([16:45](https://youtu.be/ZG8Mf3P9xzI?t=1005), [17:19](https://youtu.be/ZG8Mf3P9xzI?t=1039)):
  1. **The technical track.** "The PM that's building the actual factory," who removes drag and
     ships "the product that helps you build the product for the customer or helps AI do so."
     Charles says Ramp isn't investing in this "nearly enough."
  2. **The tastemaker, or "the driver."** The one "holding the steering wheel and doing things that
     AI cannot do and holding the bar for what great product, great taste looks like."
  3. **The GM.** PMs expand into marketing, sales, growth, and operations: "PMs will become GMs and
     they will own the actual business outcome."

## Takeaways (17:55–19:31)

- **Slide (17:58).**
  1. "Speed is all about removing bottlenecks."
  2. "Bottlenecks shift as you eliminate them."
  3. "Invest in the factory, and the product will follow."
- **Copy us.** "Everything you've seen here is outdated. Just like F1, teams will copy each other. I
  want you to copy us" ([18:28](https://youtu.be/ZG8Mf3P9xzI?t=1108)).

## Numbers (all self-reported)

| Metric | Value | Period | Time | On a slide? |
|---|---|---|---|---|
| Gong transcripts vs. an LLM window | a 1M-token window holds <0.5% of Ramp's Gong transcripts | — | 04:04 | no |
| Inspect sessions | 1M | cumulative, presumably | 08:29 | yes |
| Share of PRs built by Inspect | 75% | not stated | 08:29 | yes |
| PRs from non-engineers | 1,000 | "over the last month" (spoken only) | 08:29 | yes (no period shown) |
| Inspect speed | "under 5 seconds" (probably startup) | — | 08:29 | no |
| PRs "automatically handled" by Review Buddy | 93% (humans take the other 7%) | not stated | 09:35 | no |
| Testo configurations per run | 100 | — | 10:08 | no |
| Bugs caught by Testo | 425 | last 30 days | 10:40 | no |
| Questions to PMs fully answered by AI | 85% | not stated | 12:56 | no |
| UX issues fixed within 24 hours | 60% | not stated | 14:01 | no |

## Where this was filed

See the Ramp teardown in [goal 004](../../../goals/004-beacon-teardowns/teardowns/ramp/index.md)
and the entry in the [wiki log](../../wiki/log.md).
