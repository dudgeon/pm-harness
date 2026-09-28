# PRD (reconstructed): Glass, the AI coworker workspace and the PM's define tool

> Reconstructed from public sources for goal 004. **This is not Ramp's document.**
>
> **Labels:**
> - **said**: Ramp's own public account
> - **observed**: seen directly in a public artifact (a screenshot, a file on screen), or by a
>   third party
> - **inferred**: our reconstruction, not stated anywhere
>
> Source keys resolve in [sources](sources.md). See [index](index.md) for how the PRDs fit
> together, and [intent-shaping](intent-shaping.md) for where shaping actually happens at Ramp.
>
> **Version 2 (2026-09-27).** Rebuilt after a second research round. That round covered about
> fifteen talks and interviews, the screenshots inside the launch articles, job postings, and a
> frame-by-frame read of the product-shaping skill. See [What changed in v2](#what-changed-in-v2).
>
> This is the closest analog to a PM harness in Ramp's stack. Two parts:
> - **Part A:** Glass as a platform for every employee.
> - **Part B:** Glass as the PM's tool for the **define** step, where it produces "the next contract."

## At a glance

| | |
|---|---|
| What it is | "Project Glass," Ramp's internal AI workspace. A desktop app "built on Anthropic's Claude Agent SDK" (S14): "our internal equivalent to Claude Cowork" (S61), "still Claude Code under the hood" (S65). Its developers call it "provider agnostic" (S66) |
| Bottleneck it removes | "The models are good enough, the harness isn't" (S2). Non-engineers were stuck on terminals and MCP setup, and had no way to share what worked (S2, S16, S61) |
| Users | Every employee. Engineers call it "the home base for our non-technical folks" (S27). Its sponsor calls it "our non-engineer AI agent platform" (S74). Named heavy users include a procurement PM (S57), the VP Growth (S65), and the head of internal AI ("thousands of sessions," S16). Engineers work in Claude Code and Inspect instead (S27) |
| Surfaces | A desktop workspace. Scheduled and headless jobs run from the laptop. Slack assistants. App hosting through Ramplify. A connector to Inspect (S2, S16, S78) |
| Team | A data-platform engineer started it as a weekend project in late 2025 (S15, S66). A PM took it over a month later. A core three (PM, engineer, IT engineer) built it out (S15), and six people are credited (S2). It's a separate team from Inspect (S16). The lead left in June 2026, and the current owner isn't public (S39, S54) |
| Adoption | Weekly users went from 3 to 976 in four weeks, with "no company-wide launch announcement or top-down mandate" (S78). 700 daily users a month after launch (S14). "More than 1,000 people" (S66). "Adopted by 99% of employees" (S54, @diegozaks, 2026-06-04) |
| Skills | 15, then 350+ (April), then "800 or something" (May), in 12 function kits including Product and Design (S16, S2, S78) |
| Evidence | Three first-party articles (S2, S14, S15) and their screenshots (S78). A video about Glass (S16). About ten talks and interviews that mention it (S1, S27, S57, S59, S61, S65, S66). Job postings (S76). **High** confidence on features, **Med** on architecture, **Low** on outcomes. Nothing independent |

## What changed in v2

- **New features, from screenshots and interviews:**
  - Scout, the memory agent, and its approval queue (S78)
  - Dojo's 12 function kits, including **Product** and **Design** (S78)
  - Per-tool permission modes: Auto, Allow, or Ask (S78)
  - Team memory, a per-user voice file (S65), and per-project memory (S54)
  - Spend tracking per skill (S65); skills that install with a connector (S66)
  - A model picker (S66)
- **The adoption curve and the origin story** (S78, S66, S15).
- **Part B rebuilt from the product-shaping skill itself**, read frame by frame (S55) and checked
  against a public copy (S79). It also now has all three branches of the CPO's define slide (S1).
  Round 1 captured the slide before its third branch appeared.
- **A map of where Glass sits** among Ramp's other surfaces, and **a table of contradictions**
  between sources.
- **The hypothesis test** ("Glass is where most intent shaping happens") has its own page:
  [intent-shaping](intent-shaping.md). Short version: Glass is the designated front door for
  *define*. Most of the shaping loop, and all of its durable record, lives elsewhere.

---

## Part A: Glass as a platform

### Problem

- "At Ramp, we hit 99% adoption of AI tools across the company. And then we noticed something
  concerning: most people were stuck" (S2).
- Setups were "wildly different," and people had "no way to share what they'd learned." Ramp had
  "created urgency without providing enough infrastructure" (S2).
- The people running internal AI got "100 DMs … saying, 'I am stuck'" (S16). Salespeople were
  "15 hours into … building their own MCP server" (S16).
- "We didn't want people spending time learning Terminal, learning how to set up MCPs" (S61).
  "Learning command line was not a bet we needed the … thousands [of] non-engineers at Ramp to go
  after" (S16).
- Vendor tools weren't enough. "It needs to be really good at Ramp": secure access to Ramp's data,
  its knowledge, and its shared skills (S61). Ramp first decided "Cowork is fine." Then it found
  some things "harder to bolt on to a Cowork or a Codex than just doing it ourselves" (S16).

### Principles (said)

1. **"Don't limit anyone's upside."** Keep the complexity out of sight, but keep all of the power
   (S2).
2. **"One person's breakthrough should become everyone's baseline."** Shared skills, and "a floor
   that rises with every discovery" (S2).
3. **"The product *is* the enablement."** "No amount of workshops can match a targeted nudge while
   you're already doing the work" (S2).
4. **Be good at Ramp, not good in general.** "It doesn't need to be a good global designer, it
   just needs to be really good at designing Ramp" (S61). "Internal productivity is a moat… you do
   not hand your moat to a vendor" (S2).
5. **Don't centralize building.** "The best solution to a problem will likely come from the person
   that is solving that problem day-to-day" (S16).

The closing line of S2 sums up the first three: "We don't believe in lowering the ceiling. We
believe in raising the floor."

### Users and jobs (said, unless marked)

| User | Job | Source |
|---|---|---|
| Any employee | Get a connected, capable agent on day one, with no terminal and no config | S2, S14 |
| New hire | Pull the right data "within minutes of coming on" instead of "two hours of setup" | S59 |
| Sales rep | "Pull context from a Gong call, enrich it with Salesforce data, and draft a follow-up" | S2 |
| CX engineer | Package a Zendesk investigation as a skill, so "the entire support team levels up overnight" | S2 |
| Finance lead | Post yesterday's spend anomalies to Slack at 8am every day | S2 |
| Ops team | Build a Slack assistant that answers vendor-policy questions from Notion and Snowflake "in an afternoon" | S2 |
| Product manager | Go to Glass "first for everything": Slack search, data queries, customer insights, and finding the right customers to talk to | S57 |
| Growth leader | Run a morning job that reads every relevant channel, preps meeting docs, and brainstorms fixes checked against past experiments. Run data investigations in minutes instead of weeks | S65 |
| Head of design | Codify taste as a skill: iterate on the output and feed corrections back into the skill until it "builds a website that I don't have any nits with" | S61 |
| Expert or skill author | Publish a skill "without learning version control" | S15 |
| Builder of internal apps | Build in Glass, then deploy to Ramplify so the team can use it together | S16 |

### Features and requirements

IDs from v1 are kept. New requirements continue the numbering from GA32.

#### A1. Everything connects on day one

| ID | Requirement | Label | Source |
|---|---|---|---|
| GA1 | Configures itself on install; one Okta SSO sign-in; one-click setup for all of Ramp's tools | said | S2, S15 |
| GA2 | 30+ tools over MCP servers **configured centrally**. Connected in April screenshots: Slack, Notion, Figma, Linear, Datadog, Snowflake, Postgres, Granola, Salesforce, Gong, Hex, Google Workspace, Braintrust, Buildkite, incident tooling, and internal ones (Ramplify, Growth, Ramp Inspect, Servo, Ramp CLI) | said; observed | S14, S15, S59, S78 |
| GA3 | Home-grown tools come pre-connected (Ramp Research, Ramp Inspect, Ramp CLI), and internal CLIs come pre-bundled | said | S2, S15 |
| GA4 | Connects to each service once at launch and keeps it alive. Startup went "from 45 seconds to about 2" | said | S15 |
| GA5 | Self-healing integrations. "A non-technical user should never see a cryptic error" | said | S15 |
| GA6 | Shows each connection's status. Unreliable at launch ("those bubbles meant nothing"), with 50–100 "my Notion disconnected" messages a day | said | S16 |
| GA7 | Opens every session with scaffolding: how to think about the system, and "how to determine what you're connected to" | said | S16 |
| GA8 | Distributed across a managed fleet: auto-updates, certificates, token refresh. "We pushed it to everyone's computer, so they didn't even have to download it" | said | S15, S61 |
| GA32 | **Per-tool permission modes.** Each connector's tools are grouped as read-only, write/delete, or interactive, and each is set to Auto, Allow, or Ask. Sending a Slack message is set to Ask | observed | S78 |
| GA33 | **Knows the user's access rights** ("it understands your access privileges") | said | S59 |
| GA34 | **Connectors install skills.** Connecting Snowflake installs the Ramp Research skill bundle | said | S66 |

#### A2. Skills (Dojo) and recommendations (Sensei)

| ID | Requirement | Label | Source |
|---|---|---|---|
| GA9 | Skills are "markdown files that teach your agent exactly how to perform a specific task," shared through a marketplace called Dojo | said | S2 |
| GA10 | Publishing hides Git. Glass creates the branch, writes the file, opens the PR, and merges on approval. The author sees only "publish" and "published" | said | S15 |
| GA11 | Skills are "Git-backed, versioned, and reviewed like code" | said | S2, S15 |
| GA12 | **Sensei** recommends skills based on connected tools, role, and recent work | said | S2 |
| GA13 | Anyone can create a skill ("fire at will"). Curation happens at distribution, not creation | said | S16 |
| GA14 | Planned fixes for skill sprawl: skills for making good skills, duplicate detection at creation, and experts who "gold star" skills and own their upkeep | said (as direction) | S16 |
| GA15 | Skill owners learn how their skills perform without seeing private sessions. Not built as of May ("we don't monitor anything in Glass") | said (as a gap) | S16 |
| GA35 | **Kits by function.** Dojo groups skills into 12 kits: Essentials, Sales, Account Management, CX Leadership, Marketing, **Product**, **Design**, Data, Finance, Risk, People & Talent, Legal & Compliance. Each kit shows the user's progress (for example, "1/11") | observed | S78 |
| GA36 | **Gamified mastery.** Users rank up by skills "mastered" (Warrior, Sensei, Master) from a "Start Training" entry point | observed | S78 |
| GA37 | **Spend tracking per skill** ("how much are we spending on the skill?") | said | S65 |
| GA38 | **Skills are portable across harnesses.** Ramp Research is "a skill bundle that we make available in different harnesses… in Inspect… in Glass" | said | S66 |

The count grew from 15 skills to 350+ in April and "800 or something" in May. By May, one person's
slide-maker skill "competes with at least two to three others" (S16, S2).

#### A3. Memory

| ID | Requirement | Label | Source |
|---|---|---|---|
| GA16 | At first launch, build memory from the user's connections: people, active projects, and the relevant channels, documents, and tickets | said | S2 |
| GA17 | A synthesis pipeline runs every 24 hours over past sessions, Slack, Notion, and Calendar | said | S2, S15 |
| GA18 | **Write-once, read-many:** "The agent never modifies memory during a conversation" | said | S15 |
| GA19 | Memory v2 follows a guiding principle instead of fixed rules. Users review what it proposes, with an optional auto-accept | said | S16 |
| GA20 | Let users choose what to forget. Raised as a need; not built | said (as a gap) | S16 |
| GA39 | **Scout**, the memory agent, scans connected sources: past Claude sessions, Slack, Notion, Calendar, Linear | observed | S78 |
| GA40 | **An approval queue.** Proposed memories wait as "pending," with Approve and Dismiss buttons. They stay in a pending folder until approved | observed | S78 |
| GA41 | **Memory categories:** People, Active Work, Capabilities, Preferences, Organization. "Active Work" works as a register of the user's projects, inferred from their tools | observed; inferred | S78 |
| GA42 | **Team memory and a per-user voice file.** It learns how each user writes, building "context on you, context on the team" | said | S65 |
| GA43 | **Projects:** memory scoped to a project that persists across chat sessions | said | S54 (@shanebuchan, 2026-05-06) |

#### A4. Automations

| ID | Requirement | Label | Source |
|---|---|---|---|
| GA21 | Scheduled automations (daily, weekly, or custom cron) that post to Slack: "Glass turns your laptop into a server" | said | S2 |
| GA22 | Slack-native assistants that use the owner's full Glass setup: integrations, memory, and skills | said | S2 |
| GA23 | A headless mode for long tasks: start one, walk away, and "approve permission requests from your phone" | said | S2 |
| GA24 | Agents that act in Slack must not simply post as the user; the first version did. Ramp is formalizing which work runs on the web and which runs locally | said (as a lesson) | S16 |
| GA44 | Each automation has its channels and people, allowed tools, attached skills, instructions, and a run history | observed | S78 |
| GA45 | Shows the user's **Notion agents** alongside Glass's own assistants and automations | observed | S78 |

The Glass team ran its own product loop this way, with daily "Doc Maintenance" and "Glass Feature
requests" automations (S78).

#### A5. Workspace

| ID | Requirement | Label | Source |
|---|---|---|---|
| GA25 | Split panes and tabs, "like a code editor" | said | S2 |
| GA26 | Render markdown, HTML, CSVs, images, and code inline. Files the agent creates or edits open automatically | said | S2 |
| GA27 | The layout persists across sessions | said | S2 |
| GA28 | Personalization. One PM named her Glass "Herbert," and it now has a personality | said | S16 |
| GA29 | Direction: "every feature is a conversation." The UI becomes "a reference, not a requirement," and Glass can modify itself | said (as direction) | S15 |
| GA46 | **Model choice.** "You can select which model you want… Claude… Gemini or OpenAI." The composer shows the model (Opus 4.6 by default), an auto-accept toggle, and how much context is used | said; observed | S66, S78 |
| GA47 | Work alongside markdown files and simple PDFs, "similar to Cowork" | said | S16 |

#### A6. Build and deploy

| ID | Requirement | Label | Source |
|---|---|---|---|
| GA30 | Build apps in Glass and deploy them to **Ramplify**, the internal hosting service. Apps get URLs, sharing, Snowflake access, and model calls | said | S16 |
| GA31 | Be the interface where non-technical staff work with the coding agent | said | S27 |
| GA48 | Ramplify apps "plug into our core data and follow permissions." 1,500+ apps shipped in six weeks, from 800+ builders | said | S81, S72 |

### Architecture (known and inferred)

- **Runtime.** A desktop app on the Claude Agent SDK (S14), "Claude Code under the hood" (S65).
  Its developers call it provider agnostic, with Gemini and OpenAI models available (S66).
  Inferred: a Claude Code-style harness with a model picker that defaults to Claude. A local
  folder name in one screenshot suggests it began as a "Claude desktop" wrapper (S78).
- **Local by design.** "We don't monitor anything in Glass. We let everything run locally on
  people's computers" (S16). Local agents **take on the user's identity** in systems such as
  Snowflake. Ramp's data-platform lead wants "a stiffer guardrail" there (S66).
- **Connections.** MCP servers are configured centrally, authenticated through Okta SSO, and held
  open one connection per service (S15). Per-tool permission modes sit on top (GA32).
- **Skills.** Dojo is a Git repo of markdown skills, and Glass hides Git from authors (S15). The
  same format runs in Inspect, which loads skills from a repo's `.claude/skills/` folder (S20,
  S66).
- **Memory.** Files in a hidden folder in the user's home directory, with a pending area for
  proposals (S78). A background pipeline writes them; the agent only reads them (S15).
- **Identity.** Glass signs in through Okta (S2, S15). Separately, Ramp provisions about 2,000
  employees into Claude's own apps with centrally managed connectors (S75). Whether Glass rides on
  that isn't public.
- **Supporting services.** Ramplify for hosting (S16), plus the internal CLIs and Ramp Research
  (S2, S15).
- **How the team builds Glass** (said, S15):
  - Built largely by "vibe coding," kept healthy by:
    - a **Defrag** skill that finds and fixes fragmentation
    - a shared design system
    - **doc validation** in the PR pipeline
    - pre-commit quality gates
  - The loop: someone describes a feature in Glass, Glass builds it, automated checks run, "a human
    reviews the diff," and it ships "in hours."

### Where Glass sits among Ramp's surfaces

| Surface | Who it's for | What it's for | Source |
|---|---|---|---|
| **Glass** | Non-technical staff first, plus PMs and GTM leaders | "Multiplayer business work": context, research, documents, analysis, automations. The CPO's define step | S16, S27, S57, S65, S1 |
| **Inspect** | "A Ramp builder, so product engineering design person" | Code, prototypes, and PRs. Also research sessions, such as finding customers to interview in Snowflake | S27, S61, S19 |
| **Claude Code** (local) | Engineers and power users | Everything. The March 2026 shaping skill ran here | S27, S55 |
| **Claude's apps** (chat, Code, Cowork) | About 2,000 employees, through enterprise auth | Not described | S75 |
| **Notion**, with 300+ Notion agents | Everyone | The record: roadmap, specs, research, feedback triage | S1, S32, S68 |
| **Slack agents** | Everyone | VOTC, Gadget, Inspect mentions, team bots | S1, S17 |
| **Ramp Revenue** | GTM teams (">90%") | Background GTM work: inboxes, prospecting, CRM updates | S80 (@ParthGujare_, 2026-07-24) |

---

## Part B: Glass for the PM's define step

### Problem

Generic AI tools open with "What do you want to build?", which isn't the best starting point
(S1 06:15–06:20). A PM used to have to bother an engineer with "Is this possible? Will this break
something? What am I missing?" (S1 07:07). And engineering wants neither a long spec nor a
prototype on its own (S1 07:32).

Before Glass, a Ramp designer named the gap directly: "a central area that serves as a source of
truth for the project has become a blocker" (S62, December 2025).

### The three sub-jobs and their inputs (said, S1 slide, 06:40–07:32)

| Sub-job | Inputs Glass pulls in |
|---|---|
| **Nail the job to be done** | Goals and north-star metric; user research (the VOTC agent); data (Snowflake, Hex) |
| **Define the requirements** | Product strategy (Notion); the product spec template, kept as a **SKILL.md**; the existing codebase (through Inspect) |
| **Build the prototype** | Guiding product principles; the existing design system (Figma) |

On the slide, the data and the codebase feed into Glass, and Glass feeds all three sub-jobs.

### The shaping method: the product-shaping skill (observed, March 2026)

The spec template on the slide is a skill. The only such skill shown in public is
**product-shaping**, a Claude skill written by a Ramp PM and shown on screen in S17 (S55). The
transcription is kept locally, outside git. What follows is a summary.

- **Where it ran.**
  - In Cursor and Claude Code on a laptop, against a local copy of the codebase and a local folder
    of call transcripts.
  - It writes its research and the spec draft to local files.
  - The CPO's copy was a downloaded file ("skill (3).md"). Inferred: skills passed from person to
    person before Dojo existed.
  - "Other PMs actually have their own skills" (S17).
- **The agent's role.** "A thinking partner, not a scribe." It pushes for simplicity: a design that
  takes more than two sentences to explain is too complex. It recommends and defends a position
  instead of listing options. Every requirement has to earn its place with evidence, and nothing is
  added "for completeness."
- **Phase 1, Frame.**
  - Seven questions: the customer's job to be done; why now; what success looks like in six months;
    the first customer; the appetite (big bet or small); the bottom-line business impact; and what
    the feature unlocks beyond itself, such as GTM leverage.
  - The agent pushes on "Why are we building this?" It doesn't move on until the problem fits in
    one sentence and the PM agrees.
  - The PM then picks research streams from a menu: competitors; the codebase; an internal wiki of
    about 300 articles; Gong and Salesforce evidence; external API docs; meeting transcripts;
    domain learning. The agent recommends more.
  - They agree on search keywords first, because customers, sales, and engineers describe the same
    problem differently.
- **Phase 2, Research.**
  - "AI does 80% of the work." All streams run at once as parallel Opus subagents, with 6–10 for
    competitors alone.
  - **Every stream writes a file**, so later sessions can reuse it:
    - one per competitor, plus a best-practices synthesis
    - Gong, Salesforce, and Zendesk evidence
    - transcript evidence (closed questions and prior decisions)
    - a system audit of what already exists
  - Customer evidence comes through the `data-analyst` skill and SQL templates.
  - The evidence bar: **quantified, attributed, and honest about causality.** "Deals where X came
    up" aren't "deals we lost because of X."
- **Phase 3, Shape.**
  - Conversational, not template-driven.
  - The agent asks questions that force design decisions and brings in competitors' patterns.
  - It tracks **requirements in R-notation (R0, R1…), each grounded in evidence.**
  - It mines transcripts for **closed questions**, so settled decisions don't get reopened, and it
    tracks open questions.
  - If two or three shapes emerge, it compares them: the key idea, what it reuses, the trade-off,
    and a recommendation.
- **Output.** `spec-draft.md`, readable in two minutes, with at most 20 lines of context. It has
  seven sections:
  1. Context
  2. Principles
  3. Design ("what, not how")
  4. Alternatives
  5. Open Questions
  6. Closed Questions (with sources)
  7. Validation Plan: what would change our minds, and the single most valuable next step
- **Done when:**
  - the problem is one sentence
  - the design is **specific enough to prototype**
  - open questions have a path to resolution
  - the validation plan names one next step
- **What comes next** is separate skills:
  - prototypes: `cloudflare-pages`, `sakura-parallel-prototype`
  - a pitch deck: `slide-create`, then `slide-design`
  - domain learning
  - helpers used along the way: `data-analyst`, `writing-voice`, `domain-learning`, and an
    internal wiki skill

**What it leaves out:**
- acceptance criteria
- non-functional requirements
- a risk or compliance pass
- any sign-off ("we do not have committees and we do not have sign-offs," S17)

Its output is a local file, not a record in Notion.

### Requirements

| ID | Requirement | Label | Source |
|---|---|---|---|
| GB1 | Ground the job to be done in both qualitative (VOTC) and quantitative (Snowflake, Hex) evidence: "specificity with both qualitative and quantitative data" | said | S1 06:37; slide |
| GB2 | Know product strategy, "how we define product specs," product principles, the design system, and the codebase | said | S1 06:59–07:19 |
| GB3 | **AI as tech lead:** answer questions about feasibility, risk of breakage, and gaps | said | S1 07:07 |
| GB4 | Build a **prototype that works inside the real product**, as real code | said | S1 07:19; S17 |
| GB5 | Produce **"the next contract"**: the case that the problem is real, "the actual requirements that they can use for their coding agents," and a prototype | said | S1 07:32 |
| GB6 | Write the spec in **two versions**: a one-pager for humans and a "much more robust" agent version | said | S18 |
| GB7 | Shape through conversation as a thinking partner, with recommendations and trade-offs, drawing on every other project's context in Notion | said; observed | S17, S55 |
| GB8 | Research in parallel before shaping, and have **every stream write a reusable file** | observed | S55 |
| GB9 | Output a two-minute spec in seven sections: Context, Principles, Design, Alternatives, Open Questions, Closed Questions, Validation Plan | observed | S55 |
| GB10 | One strong, shared shaping skill. In March, several PMs had their own | said (as a gap) | S17 |
| GB11 | Hand the prototype's PR to engineering. Automated review routes it by complexity | said | S17 |
| GB12 | **A framing gate:** don't research until the problem is one sentence and the PM agrees | observed | S55 |
| GB13 | The PM chooses the research streams and the agent proposes more. Keywords are agreed first | observed | S55 |
| GB14 | **An evidence bar:** quantified, attributed, honest about causality | observed | S55 |
| GB15 | **Requirements carry IDs and evidence** (R-notation). Ungrounded ones get challenged | observed | S55 |
| GB16 | **Closed questions** come from transcripts, each with its source, so settled decisions stay settled | observed | S55 |
| GB17 | Exit at "specific enough to prototype," with one named next step for validation | observed | S55 |
| GB18 | Prototype next, increasingly as parallel variants ("3–4 iterations of that same PR, each one with a different approach") | said; observed | S51, S55 |
| GB19 | Reach the codebase through the Inspect connector to answer the tech-lead questions | inferred | S1 slide; S78 |

### How it works (reconstructed flow)

1. **Identify** (outside Glass). The VOTC agent, a separate Slack agent and dashboard running on
   GPT-5 and Gemini, surfaces a problem and the customers behind it (S1 04:58–05:54).
2. **Frame** in Glass or Claude Code with the shaping skill: seven questions and the
   one-sentence gate (GB12). Inferred: Dojo's Product kit is its likely home now (S78, S1).
3. **Research** in parallel into evidence files, using Ramp Research inside Glass for data
   (GA38).
4. **Shape** into the two-minute spec, the agent spec, and the validation plan (GB6, GB9).
5. **Prototype** in Inspect, either with the Chrome extension on the live product or in a session
   with a deploy preview (S1 08:11; S55). Standalone apps go to Ramplify. Variants run in parallel
   (GB18).
6. **Hand off** the "next contract" (GB5). The record lands in Notion (specs, roadmap) and Linear
   (backlog), where Gadget answers questions against it (S1 11:31). For small items, the prototype
   PR *is* the change (S17).

### How the define step moved between tools

| When | Where define work happened | Source |
|---|---|---|
| Oct 2025 | Notion (roadmap, research, sales feedback), ChatGPT, and Ramp Research in Slack | S60 |
| Dec 2025 | Designers prototype first (Magic Patterns), hand off in Figma, and use Inspect for code changes | S62 |
| Jan 2026 | A chain of research agents finds customers, mines past calls, and drafts research plans | S69 |
| Feb–Mar 2026 | The shaping skill runs in Claude Code and Cursor, and several PMs have their own. One PM's personal harness is Claude Code plus Notion | S17, S55, S80 (@chapello, 2026-03-27) |
| Apr 2026 | Glass launches with a Product kit in Dojo. A procurement PM goes to Glass "first for everything." Her engineering lead says "PM uses Claude to write up a product spec" | S78, S57 |
| Apr 2026 | A PM's "specs are working branches in our QA environment, with a PR ready" | S51 |
| Jun–Aug 2026 | PM and design job postings name Claude, Claude Code, Cursor, and Figma, not Glass | S76 |
| Sep 2026 | The CPO's slide puts all three define sub-jobs in Glass | S1 |

Inferred: the method stayed the same (a skill). Its host moved from personal Claude Code setups
toward Glass, and the prototype moved into Inspect.

---

## How Glass evolved

| When | What | Source |
|---|---|---|
| 2023 | Knowledge is consolidated into Notion | S16 |
| 2024–2025 | Knowledge-base RAG, then Ramp Research, then Inspect. Each "generation" retired the one before | S73 |
| Q3 2025 | Notion custom agents, such as the product Q&A agent | S16, S32 |
| Late 2025 | A data-platform engineer puts Claude Code in a desktop app as a weekend project (the first PR) | S15, S66 |
| Winter 2025–26 | The "Opus 4.5" inflection. Finance staff move into the terminal, and the "I am stuck" DMs start | S16 |
| Early 2026 | A PM picks it up, and it has about 20 daily users within weeks: "Glass had users before it had a team." Claude Cowork appears, and Ramp builds its own anyway | S15, S16 |
| Mar 12 – Apr 8, 2026 | Weekly users go from 3 to 976, and weekly sessions from 458 to 10,293 | S78 |
| 2026-04-08/09 | Public launch posts. 700 daily users; 350+ skills | S14, S2 |
| 2026-04-15 | Dojo shows 12 function kits, including Product and Design. Scout handles memory | S78 |
| 2026-05-06 | Projects, with per-project memory | S54 |
| 2026-05-21 | About 800 skills; memory v2; Ramplify as a first-class feature; a hackathon's worth of apps | S16 |
| 2026-06-04 | "Adopted by 99% of employees" | S54 (@diegozaks) |
| 2026-06-08 | Glass's lead leaves Ramp | S54 (@sebgoddijn), S39 |
| 2026-06-18 | Anthropic says Ramp's employees "log in to Claude on day one already connected — 2,000 employees" | S75 |
| Jun 2026 | "Provider agnostic"; "more than 1,000 people" more productive | S66 |
| 2026-08-06 | "The home base for our non-technical folks" | S27 |
| 2026-09-10 | The CPO presents Glass as the agent for define | S1 |
| 2026-09-27 | No open Glass or internal-AI roles. Glass's originator works in a vendor desktop app | S76, S77 |

## Contradictions and tensions

| Topic | One source says | Another says | Likely reading |
|---|---|---|---|
| Monitoring | "We don't monitor anything in Glass" (S16) | Spend per skill is tracked (S65), and there's a company-wide token tracker and leaderboards (S14, S17) | Aggregate metering, not session content. Unconfirmed |
| Model | Claude Agent SDK (S14); "still Claude Code under the hood" (S65) | "Provider agnostic… Gemini or OpenAI" (S66); "a harness for Claude or any LLM" (S61) | A Claude-based harness with a model picker (inferred) |
| Identity | Okta sign-in to Glass (S2, S15) | 2,000 employees log in to Claude's apps with managed connectors (S75) | Either Glass rides on Claude's enterprise auth, or the two run side by side. Bears on Q-016 |
| Build team and time | "A team of four built it in under three months" (S14) | "About a month" (S54, @shanebuchan); a core three (S15); six credited (S2) | Different start points |
| Hackathon | 700 participants (S72, S14) | 650 participants and 305 submissions (S58); "300 submissions" (S18); "something like 150 apps" (S16) | Kickoff vs final counts; submissions vs apps |
| Adoption | 700 daily users (S14) | 976 weekly (S78); "more than 1,000" (S66); "99% of employees" (S54) | Different dates and definitions |
| Integrations | "13+" (S15) | "30+" (S14, S59) | Different dates |
| Skill governance | "Fire at will" (S16); internal tools are "yeah, chaos" (S61) | Skills are "reviewed like code" (S2, S15) | Review happens on publishing to Dojo, not at creation |
| Positioning | "AI productivity suite," "AI workspace" (S2, S54) | "Home base for our non-technical folks" (S27); "non-engineer AI agent platform" (S74) | Drifting toward non-engineers |

## Open questions

- Who has owned Glass since June 2026, and is it still growing?
- Is Glass converging with Claude's own apps (enterprise auth, Cowork), or staying separate (S75)?
  This bears on Q-016.
- What's in Dojo's Product and Design kits? Is the product-shaping skill one of them?
- What share of PM define work happens in Glass, in Claude Code, and in Inspect?
- How does a define session hand off to Inspect: through the connector, a session link, or a PR?
- Glass keeps sessions local and unmonitored, yet spend per skill is tracked. What exactly is
  collected?
- What does it cost per user?

## Through our lens (goal 004, R3)

| Axis | Ramp's answer |
|---|---|
| First move | Removing setup friction for everyone, **not** a PM move. PM moves came later, as a Product kit and the define framing |
| Deployment model | **Local and per-person**, pushed to every managed laptop. **Procedural context is shared** (Dojo), **connectors are configured centrally**, and shared apps live on Ramplify |
| Context approach | Federated reads over MCP. Per-user memory behind a **human approval queue**, plus team and per-project memory. Shared skills, some installed by connectors |
| Traces | **None captured centrally, by design.** Spend per skill is metered. Skill owners get no feedback on quality (S16) |
| Controls | SSO and each person's own permissions; per-tool Auto/Allow/Ask; skills reviewed like code when published; phone approvals for headless runs; memory the user approves. Gap: local agents inherit the user's identity (S66) |
| PM moves ([pm-moves](../../../../context/wiki/pm-moves.md)) | Framing and shaping intent into a spec (3), solution identification through prototypes (2), and the handoff to delivery (Q-008) |
| Delegation ([levels](../../../../context/wiki/path.md#delegation-levels)) | **L2**: the agent researches, drafts, and prototypes; the PM frames, chooses, and decides |

**The key observation.** Glass sits at the hybrid stop in our
[path](../../../../context/wiki/path.md) notes: local on topology, shared on skills. Ramp made it
the front door for define. But the method (skills) is portable, and the artifacts (spec,
prototype, record) live in Notion and Inspect. So for our design, "which app" matters less than
"which skills, which context, which record."

It breaks from H-009 in two places:
- **Declarative memory stays per-user.**
- **No traces are captured centrally.** Ramp's own team names the cost: nobody knows which skills
  work (S16).

The evidence for H-009's portability claim got stronger: the same skill bundle runs in Glass and
in Inspect (S66).

## What transfers to a regulated enterprise (R4)

**Transfers:**
- Centrally configured connectors behind enterprise SSO, with each person's own permissions.
  **Per-tool Auto/Allow/Ask modes** make a sensible default control surface.
- Skills kept in Git, reviewed like code, with Git hidden from authors. **Kits by function** (a
  Product kit) as the unit of distribution. Connectors that install their own skills.
- Memory that the agent writes once, the user approves, and anyone can inspect.
- "The product is the enablement." It serves earned adoption (C6) better than training does.
- The shaping skill's discipline: a one-sentence framing gate, an evidence bar, requirement IDs
  tied to evidence, closed questions with sources, and research saved as files. All of it feeds
  the spec contract (Q-008).
- The spec template kept as a skill, and a spec in two versions (for humans and for agents).
- The underlying stack (a Claude-based agent SDK) is the kind of tooling the enterprise already
  sanctions ([path](../../../../context/wiki/path.md)).

**Needs adapting:**
- *Acceptance criteria and controls.* The skill stops at "specific enough to prototype," with no
  acceptance criteria, risk pass, or sign-off. A regulated spec contract needs all three (Q-008,
  Q-014).
- *Memory synthesis.* Mining each user's Slack, Calendar, and documents raises questions of
  records, privacy, and surveillance (Q-013, C7).
- *Local execution.* It may conflict with data-residency and DLP controls. Local agents also
  **inherit the user's identity**, which Ramp's own data lead flags.
- *Skill creation.* "Fire at will" creation needs a review tier for regulated content.
- *Acting in chat.* Agents that act in chat need their own identity, not the user's.
- *Where the brief lands.* The shaped brief is a local file. It needs to land in a governed record.

**Doesn't transfer:**
- Ramp's surrounding policies: "kill token limits and access restrictions … no tiered access based
  on role," mandated usage, and leaderboards visible to everyone (S14). Also governance of internal
  tools as "chaos" (S61). These clash with least privilege, data classification, and earned
  adoption (C6, C7).
