# PRD (reconstructed): Inspect, the background coding agent and agent platform

> Reconstructed from public sources for goal 004. **This is not Ramp's document.**
>
> **Labels:**
> - **said**: Ramp's own public account
> - **observed**: a third party saw it
> - **inferred**: our reconstruction, not stated anywhere
>
> Source keys resolve in [sources](sources.md). See [index](index.md) for how the PRDs fit together.
>
> This is the best-documented part of Ramp's factory. A detailed first-party post exists, plus
> vendor case studies, a public docs site, and public GitHub artifacts. The PRD focuses on what
> matters for PM moves: non-engineers building, prototypes, controls, and traces.

## At a glance

| | |
|---|---|
| Step in Ramp's loop | **Build**. "The first bottleneck was coding" (S1 07:57) |
| What it is | A hosted background coding agent. Every session gets a fully provisioned sandbox with Ramp's stack. It has grown into the platform that most of Ramp's other agents run on: "more than 200 agents" (S19) |
| Users | "Every builder at Ramp": engineers, PMs, designers, operators, account managers, salespeople (S17, S23). 98.6% of people in Engineering, Product, Design, and Data have used it (S22) |
| Surfaces | Slack, web app, Chrome extension, web VS Code, PR threads, Linear, an MCP server, a public API, automations, and other agents (S7, S20, S24) |
| Team | About 5.5 people (four engineers, a director, a part-time PM), plus 150+ contributors across Ramp (S19) |
| Latest numbers (said) | "1M sessions," "75% of our PRs," "1,000 PRs from non-engineers" in the last month (S1 08:29; slide) |
| First public mention | 2026-01-12 (S7) |
| Evidence | First-party posts and docs, vendor case studies, a paywalled Pragmatic Engineer piece (preview only), and public GitHub artifacts that were **observed** (S21). **High** confidence on architecture and features. **Med** on metrics, whose definitions vary between sources |

## Problem

- **Local agents limited everyone.** Ramp could run only "one or two sessions on local machines."
  Designers needed better frontend tooling, and engineers needed remote dev environments
  (S19, reporting what Ramp said).
- **The founding idea is to close the loop on verification.** "Inspect writes the code like any
  other coding agent, but closes the loop on verifying its work by having all the context and
  tools needed to prove it, as a Ramp engineer would" (S7).
- **Why build rather than buy.** Owning it lets Ramp build something "significantly more powerful
  than an off-the-shelf tool … it only has to work on your code" (S7). Also: "we wanted to have a
  strong harness, and we wanted to make sure that our coding agent really understood our
  codebase" (S1 07:57).
- **The reviewer is part of the target.** Agents "only do about 50% of the work… there's also a lot
  of work on the reviewer." The goal is that reviewers "just … take a glance … and click the green
  button" (S23).

## Users and jobs

| User | Job | Source |
|---|---|---|
| Engineer | Run many sessions in parallel from Slack, the web, or the phone, and get PRs back with evidence | S7, S22 |
| PM | Ship small features. Turn a spec into "the real product, back-end, front-end," as a PR to hand to engineering | S17, S23 |
| Designer | Make UI tweaks directly. Take "a dashboard rework most of the way there from a Figma file, then hand the session to an engineer" | S23, S24 |
| CPO, prototyping | Use the Chrome extension on the live product to build PM-sized changes. His own sessions include "Credit limit utilization display" and "Add Bill Pay tab count badges" | S55 (observed) |
| Designer, researching | Find research participants: "I will go ask Ramp Inspect… [it] has access to Snowflake… can actually find any customer that fits my profiles" | S61 |
| PM, shipping | "Another 5 PR's merged by this 'non-technical' product manager via Ramp Inspect" | S80 (@chapello, 2026-01-26) |
| Operator, AM, or salesperson | Fix small product issues raised in Slack ("@Inspect fix this") | S17, S19 |
| Other agents | Hand off implementation: OCA, the integration factory, Review Buddy, the autonomous loop | S28, S30, S20 |

## Goals and success measures

- **Merged PRs are "the most important metric."** A live "humans prompting" count is tracked too
  (S7).
- **Preferred measure** (Head of Engineering): "fewest human touches per safely merged PR" (S26).
- **Metrics over time** (said; definitions vary, so read this as a spread, not one series):

| As of | Metric | Value | Source |
|---|---|---|---|
| Week before 2026-01-12 | Share of merged frontend and backend PRs | about 30% | S7, S8 |
| 2026-01-26 | Share of PRs merged to the backend and frontend repos, last week | 41.9% | S54 (@rahulgs) |
| 2026-02-09 | Share of merged PRs, last 24 hours | 57% | S25 |
| Feb 2026 | Share of merged PRs | "over half" | S23 |
| 2026-04-08 | Non-engineers' share of human-initiated PRs | "12% … thousands per month" | S14 |
| 2026-04-27 | Share of merged PRs | "60%+" | S24 |
| Apr 2026 | Share of PRs merged "last week" | "over 60%" | S59 |
| 2026-04-30 | Share of merged PRs | "~70%" | S54 (@zachbruggeman) |
| 2026-06-19 | Share of all PRs merged at Ramp, past 6 months | 76.5% | S22 |
| 2026-06-19 | Usage | 750+ daily users; 10,000+ sessions a day; 800k sessions total | S22 |
| Jul 2026 | Cumulative sessions | passed 1M | S19 |
| Aug 2026 | Share of merged PRs | "three of every four" | S24, S19 |
| Aug 2026 | Session sources | "More Inspect sessions are coming from automations than humans" | S27 |
| 2026-09-10 | Talk headline | 1M sessions; 75% of PRs; 1,000 PRs from non-engineers "over the last month" | S1 |

## Requirements

### Functional

| ID | Requirement | Label | Source |
|---|---|---|---|
| I1 | Start fast in a fully provisioned sandbox with Ramp's stack ("Vite, Postgres, Temporal, the works"), a VS Code server, a web terminal, and a browser | said | S7, S23 |
| I2 | Verify its own work: tests, telemetry, feature flags, and "before and after" screenshots attached to PRs | said | S7 |
| I3 | Deploy a preview that a PM can use: "it deployed a preview, authenticated as a fixture user, validated desktop and mobile behavior, and attached visual evidence to the PR" | said | S1 08:29; S26 |
| I4 | Accept prompts from many places: Slack (and screenshots), the web, the Chrome extension (sending the DOM and React tree for visual edits), PR threads, Linear issues, voice, the MCP server, and the public API | said | S7, S20, S24 |
| I5 | Route Slack prompts to the right repo with a fast classifier that can also answer "unknown" | said | S7 |
| I6 | Run parallel work: child sessions, subagents, and "Orchestrate" across repositories from one Slack mention | said | S7, S20, S46 |
| I7 | **Multiplayer and public by default.** "Every session is multiplayer"; sessions are "public and open to collaboration." Using a private connector makes a session private | said | S7, S19, S20 |
| I8 | Automations: triggers from schedules, GitHub pushes, GitHub status checks, and Datadog monitors. They can post **proposals** to Slack with Accept and Reject buttons (`post_automation_proposal`) | said | S20 |
| I9 | Skills that encode "how we ship at Ramp," plus an MCP for the design system and per-repo AGENTS.md guidance | said | S7, S20, S22 |
| I10 | Show **per-session cost** in the UI | said (slide) | S1 slide 08:38 |
| I11 | Support all frontier models. The default is chosen for cost; since June 2026 it has been "GPT-5.5 on medium reasoning," and users can override it | said | S7, S22 |
| I12 | Serve as a platform: sandboxes, agent harness, integrations, LLM gateway, API, and an automations marketplace, all shared by 200+ internal agents | said (reported) | S19 |
| I13 | **Ask for a shaped request at the session boundary.** The docs' guidance: state the outcome and who benefits; include errors, screenshots, links, or "acceptance criteria that define success"; name hard constraints; keep one outcome per session. Inferred: this is where acceptance criteria live at Ramp, not in the spec | said | S20 |
| I14 | **Show live sessions company-wide.** "What did people ask? What code was generated?" The CEO credits this visibility, more than the agent itself, for adoption | said | S59 |
| I15 | Scope context by Team or Project: link repositories, Slack channels, and instructions so sessions get the right context. There's no page for a shared brief, designs, or research | said | S20 |
| I16 | Custom agents: a system prompt, model, repo access, and skills, with versioned prompts and a handle. The docs' own example is a `@project-manager` status agent | said | S20 |
| I17 | Research-only sessions that end with "No changes made," such as "Locate enterprise or strategic customers" | observed (screenshot in S19) | S19 |

### Controls and human in the loop

| ID | Requirement | Label | Source |
|---|---|---|---|
| IC1 | **Open PRs as the user, not as the app.** Doing it as the app "would allow for any user to approve their own changes. You do not want to knowingly create a vector for unreviewed code" | said | S7 |
| IC2 | Attribute each prompt that changes code to the person who wrote it | said | S7 |
| IC3 | **Least privilege.** "Give the model what it needs, but nothing more." The security team set network-access policies and keys. "A central team defines what agents can access and do" | said | S27, S24 |
| IC4 | Scope secrets by phase (build, runtime, network egress), and keep credentials to non-production resources | said | S20 |
| IC5 | Debug against a "sanitized read-only prod DB replica," not live production | said (reported) | S19 |
| IC6 | Humans still review and merge (see [Review Buddy](prd-review-buddy.md)) | said | S23, S20 |
| IC7 | Control costs with defaults rather than per-person budgets: cheaper models and the "flex" tier for automations, and "banning automations from using frontier models." In May 2026 this cut daily spend by "roughly 35%" | said | S22, S31 |

### Architecture (said, S7, S22, S23, S31, unless marked)

- **Sandboxes on Modal.**
  - Per-repo images are rebuilt every 30 minutes and snapshotted.
  - Warm pools, and sandboxes that start warming while the user types.
  - Time to interactive went from about 6.5s to about 2s with "Sandboxes V2" (June 2026).
  - The talk says "under 5 seconds."
- **Harness.** OpenCode runs as a server inside the sandbox. Other Ramp agents use Claude Code or
  Codex (S28).
- **State and streaming.** Each session gets its own SQLite database in a Cloudflare Durable
  Object.
- **LLM gateway.** It "processes trillions of tokens per day." Its Thompson-sampling routing saved
  30% on Inspect's traffic, and the same work was productized as Ramp Router (S31).
- **Data.** "800k sessions, 30M tool calls, and 100M message parts" sit in a sanitized session data
  lake, and every session is traced end to end (S22).
- **Signs of external productization** (observed, S21): a public docs site, a public GitHub App
  ("Inspect by Ramp," created 2026-08-07), and Inspect PRs in employees' personal public repos.
  Inferred: Ramp may offer Inspect outside Ramp. That's unconfirmed.

## How it evolved

- **v1 (Sep 2025):** a Chrome extension for designers' visual edits. Adoption was low (S19). By
  December a designer was using Inspect as "our very own version of Cursor in the browser" (S62),
  and its lead pitched the extension as "great for PM starting on something" (S54,
  @zachbruggeman, 2025-12-29).
- **v2, the background agent (Nov 2025, internal):** "The first version only took me a few days"
  (S23).
- **Public post (2026-01-12):** about 30% of PRs (S7).
- **Feb–Aug 2026:** Linear, automations, Orchestrate, Sandboxes V2, and cost controls arrive; 75% of
  PRs (S22, S24, S19).
- **More than 80% of Inspect is written with Inspect** (S23, S19).
- **Direction:** "We want Inspect to hold all the context: The brief. The designs. The code. The
  copy. The research" (S54, @zachbruggeman, 2026-04-30). "The next generation of Inspect is under
  way" (S54, @_dylanga, 2026-08-29).

## Open questions

- **Metric definitions.** "Built by," "created with," and "raised by" Inspect aren't defined.
  Some sources count all repos and include automation PRs.
- **Non-engineer PRs.** "Thousands per month" (April, S14) versus "a thousand … over the last
  month" (September, S1). That could be a decline, a narrower definition, or rounding.
- **Deployed previews.** Is a preview a per-PR deployment, or the kept-alive sandbox?
- **Production and PII access** beyond the sanitized replica.
- **The context hub.** Will Inspect really hold the brief, designs, and research? The public docs
  (S20) show only Teams and Projects that scope repositories and channels. This bears on where the
  brief lives ([intent-shaping](intent-shaping.md)).

## Through our lens (goal 004, R3)

| Axis | Ramp's answer |
|---|---|
| First move | Coding: "the first bottleneck." It came before any PM-facing agent except the data and insight agents |
| Deployment model | **Shared and hosted** (cloud sandboxes). It started as a local tool and moved to the cloud because local runs limited parallelism |
| Context approach | Codebase, skills, AGENTS.md, design-system MCP, and integrations (Sentry, Datadog, LaunchDarkly, Linear, Slack). Per-repo defaults trim context deliberately |
| Traces | **Every session is traced end to end and kept in a data lake**, plus public sessions and attribution per prompt. This is the most complete trace capture in Ramp's stack, and the opposite of Glass |
| Controls | PRs open as the user; least privilege; scoped secrets; a sanitized replica; human review; cost defaults |
| PM moves | Delivery (4), plus PMs prototyping (2, 3) and small fixes from in-market signals (7). This is where "anyone at Ramp can now code" (H-008) |
| Delegation | **L3** for most PRs (AI builds, a human approves the merge). Higher for automations with proposals (see the autonomous loop) |

## What transfers to a regulated enterprise (R4)

**Transfers:**
- **Hosted, isolated sandboxes** with least privilege, scoped secrets, and sanitized data.
- **PRs under the person's own identity**, which keeps segregation of duties intact. This is Ramp's
  own control rationale, and it lines up with a regulated enterprise's.
- **Attribution per prompt, plus end-to-end session traces.** That's evidence for who asked for
  what and how the agent did it (H-012). It's also the raw material for measuring delegation (H-005).
- **Merged PRs and "human touches per safely merged PR"** as candidate delivery measures (Q-010).

**Needs adapting:**
- *Public-by-default sessions.* They clash with need-to-know access to classified code or data.
  Default to team visibility, with public by opt-in.
- *Non-engineers shipping to production.* Change management may require training, restricted
  repos, or an engineer co-signing.
- *Choosing models by cost across all providers.* Model-risk governance and approvals for third-party
  AI narrow the options (C7).

**Doesn't transfer as-is:**
- A PR share near 75% without SDD-grade specs. Ramp's codebase, platform team, and tolerance for
  risk are specific to Ramp. Under DEC-010 the enterprise gets there through specs, not through
  "@Inspect fix this."
