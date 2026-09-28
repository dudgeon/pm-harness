# Where does intent shaping happen at Ramp? Testing a hypothesis

> Part of the [Ramp teardown](index.md). Labels and source keys as in [sources](sources.md).
>
> **The hypothesis (Geoff, 2026-09-27):** "Glass is where the majority of intent shaping happens."
>
> "Intent shaping" here covers framing the problem, gathering evidence, writing the spec, and
> building the prototype that stands in for the spec. These are moves 1–3 in our
> [pm-moves](../../../../context/wiki/pm-moves.md) loop, plus the handoff to delivery.
>
> Tested in two rounds on 2026-09-27: X timelines and on-screen evidence, then about fifteen talks
> and interviews, job postings, and screenshots. See [the Glass PRD](prd-glass.md) for the product
> itself.

## Verdict

**Partly supported. Glass is Ramp's designated front door for the *define* step. But most of the
shaping loop, and all of its durable output, lives elsewhere.**

**For the hypothesis:**
- **The CPO's September slide puts all three define sub-jobs in Glass:**
  - nail the job to be done
  - define the requirements, with the spec template kept as a SKILL.md
  - build the prototype

  (S1 06:37–07:32)
- **Dojo has a Product kit and a Design kit**, so PM and design skills ship through Glass (S78).
- **Some PMs and leaders start there.**
  - A procurement PM goes to Glass "first for everything": Slack search, queries, customer
    insights, and finding customers to talk to (S57).
  - The VP Growth uses "Glass for everything" (S65).
- **Everyone has it**, and it's pre-wired to shaping's inputs (S54, S78):
  - Notion, Linear, Figma, Granola
  - Gong, Salesforce
  - Snowflake, Hex
  - Inspect

**Against it:**
- **Discovery happens before Glass.** VOTC is a separate Slack agent and dashboard, running on
  GPT-5 and Gemini (S1 04:58–05:54).
- **The shaping method is a portable skill, not an app feature.**
  - The one skill shown in public ran in Claude Code and Cursor (S55).
  - The same skill bundles run in both Glass and Inspect (S66).
- **Research recruiting runs through Inspect** (S61). Research-plan assistants are "in Slack,
  slash in Notion… fairly chaotic" (S61). By June, design had its own shaping agents outside
  Glass: a research-plan partner that also coaches interviewers, per-designer Slack bots that build
  v1 prototypes from meeting notes, and a prototype playground anyone can fork (S54, @diegozaks,
  2026-06-05).
- **Prototypes are built in Inspect.**
  - That's where specs are turning into "working branches" (S51).
  - That's where PMs collaborate (S53).
- **The record lives in Notion and Linear** (S1 11:31). Glass runs locally and keeps nothing
  centrally (S16), so the brief can't live there.
- **Ramp's own descriptions of PM work rarely mention Glass.**
  - Job postings for PMs and designers name Claude, Claude Code, Cursor, and Figma. Only CX
    postings name Glass (S76).
  - An engineering lead says the PM "uses Claude to write up a product spec" (S57).
  - Engineers call Glass the home of "non-technical folks" (S27).

**Direction of travel: mixed.**
- Between March and September, the CPO's framing moved define into Glass (S17 → S1).
- But Inspect is also reaching for the context: "The brief. The designs. The code. The copy. The
  research" (S54, @zachbruggeman, 2026-04-30). Its public docs don't show that yet (S20).
- Ramp now provisions 2,000 employees into Claude's own apps (S75).
- Glass's lead left in June (S54).

**Better framing for our project:** intent shaping at Ramp is a relay across surfaces, and skills
carry the method from one to the next:
1. discovery in VOTC
2. framing and research in Glass or Claude Code
3. the prototype in Inspect
4. the record in Notion

Glass is the front door, not the room where the brief lives. None of this is quantified in
public.

## Evidence, by date

| Date | Evidence | What it says about where shaping happens | Kind | Source |
|---|---|---|---|---|
| ~Jun 2025 | Seb Goddijn taught a PM team "how to use claude code for ~everything~" | PMs started shaping in Claude Code, before Glass existed | 1P | S54 (@teddy_riker, 2026-04-15) |
| 2025-10-02 | Every laptop comes with ChatGPT, Notion AI, and Perplexity. Notion holds the roadmap, project databases, and a sales-feedback database | Before Glass, shaping's raw material lived in Notion | 1P | S60 |
| 2025-12-29 | A staff designer prototypes first, hands off in Figma, and uses Inspect as "our very own version of Cursor in the browser." The bottleneck is "a central area that serves as a source of truth for the project" | The brief had no home before Glass; the prototype already had one | 1P | S62 |
| 2026-01-12 | Head of design: Inspect is "transformative for every single designer… I'm using this… to build full prototypes of real products" | Prototyping moves into Inspect | 1P | S54 (@diegozaks) |
| 2026-01-13 | A chain of research agents: one finds the right customers, one mines past calls, one drafts a research plan | Research tooling existed before Glass, spread across tools | 1P | S69 |
| 2026-01-26 | A PM: "another 5 PR's merged by this 'non-technical' product manager via Ramp Inspect" | PMs ship through Inspect | 1P | S80 (@chapello) |
| 2026-02-09 | Designer job posting: "Start in an LLM: Use tools like Claude to clarify intent, draft short PRDs." Then Cursor and Claude Code, then Figma | Ramp tells candidates that shaping starts in Claude | 1P | S76 |
| Feb–Mar 2026 | **The product-shaping skill on screen.** A PM-written `SKILL.md` open in Cursor, using Claude Code tools, a local clone of the codebase, and local transcripts. It writes `spec-draft.md` locally, then hands off to other skills to prototype and to make a deck | **Framing, research, and spec happen in a local Claude Code session driven by a skill.** Not in Glass, which hadn't launched | observed (on screen) | S55 |
| Feb–Mar 2026 | **The CPO prototypes in the product.** The Inspect Chrome extension runs on Ramp's live Bills page, with his own PM sessions listed | Prototyping happens in Inspect, on the real product | observed (on screen) | S55 |
| 2026-03-09 | Product teams' "context documents" feed Inspect sessions. A PM "vibe-coded about 20 tools" | Shaping artifacts flow into Inspect | 1P | S63 |
| 2026-03-15 | "Claude has full access to our Notion… we have skills in Claude that is like your product spec skill… we don't really talk about the spec itself… We talk about the actual product" | The spec is a waypoint; context comes from Notion | 1P | S17 |
| 2026-03-27 | A PM's "critical skills in my Claude Code setup," such as `/good-morning`, refresh a to-do list in Notion | Some PMs' personal harness is Claude Code plus Notion | 1P | S80 (@chapello) |
| 2026-04-02 | "Today, my specs are working branches in our QA environment, with a PR ready for engineering and design to collaborate on" | **The spec becomes a branch** (an Inspect session and PR) | 1P | S51 |
| 2026-04-09 | Glass launches, for people "stuck in a chat window… teaching everyone how to use the terminal wasn't going to scale." Weekly users went from 3 to 976 in four weeks, with no mandate | Glass exists for the non-terminal majority, and it spread on its own | 1P; observed | S54 (@sebgoddijn); S2; S78 |
| 2026-04-15 | Dojo shows 12 function kits, including **Product** and **Design** | PM and design skills are distributed through Glass | observed | S78 |
| 2026-04-28 | Head of design: shaping starts on paper, "and then I go to Claude." Designers find research participants by asking **Inspect**. The research-plan assistant is "in Slack, slash in Notion… fairly chaotic." Design built a taste skill in Glass | Shaping is spread across tools and moves when the tools change | 1P | S61 |
| 2026-04-30 | Procurement PM: "we go to Glass… I go there first for everything." Her engineering lead: "PM uses Claude to write up a product spec." The designer starts in a prototype and fixes UI through Inspect | For this PM, Glass is the front door for context and research. The spec and the prototype happen elsewhere, or are described that way | 1P | S57 |
| 2026-04-30 | "We want Inspect to hold all the context: The brief. The designs. The code. The copy. The research" | Inspect's stated direction is to absorb shaping artifacts | 1P | S54 (@zachbruggeman) |
| 2026-05-06 | Glass "Projects" keeps memory per project across chat sessions | Glass supports long-running shaping work | 1P | S54 (@shanebuchan) |
| 2026-05-21 | Glass is for "multiplayer business work," and Inspect for "multiplayer coding sessions." "We don't monitor anything in Glass… locally." Early users included PMs | The split: research and documents in Glass, code and prototypes in Inspect. Nothing is kept centrally in Glass | 1P | S16 |
| 2026-06-04 | VP Growth: "I use Glass for everything now… still Claude Code under the hood" | For GTM leaders, Glass is the main surface | 1P | S65 |
| 2026-06-04 | "Every single Product designer… running multiple agents… spinning up prototypes, shipping code… Glass… is adopted by 99% of employees" | Designers prototype through agents; Glass is universal | 1P | S54 (@diegozaks) |
| Jun 2026 | Ramp Research is "a skill bundle… in Inspect… in Glass." Glass is "provider agnostic" | The method is portable across harnesses | 1P | S66 |
| 2026-06-05 | Head of design lists design's agents: a research-plan partner that coaches interviewers, per-designer Slack bots that build v1 prototypes from meeting notes, a forkable prototype playground, and Inspect for changes through code review | More of the shaping loop lives outside Glass | 1P | S54 (@diegozaks) |
| 2026-06-08 | Glass's lead leaves Ramp | Continuity risk for Glass | 1P | S54 (@sebgoddijn); S39 |
| 2026-06-18 | Ramp's employees "log in to Claude on day one already connected — 2,000 employees" | Claude's own apps are a company-wide surface too | Vendor | S75 |
| 2026-06-19 | Inspect is "as close as we can to 'just works' on any knowledge work tasks at ramp - eng, product, data, support, sales, uxr" | Inspect's scope reaches product work and user research | 1P | S54 (@rahulgs) |
| Jun–Aug 2026 | PM postings ask for prototyping in "Claude Code, Cursor" or "Cursor, Bolt, Claude Code." Only CX postings name Glass | Ramp describes PM shaping in vendor tools | 1P | S76 |
| 2026-07-22 | Specs need "the human version and then the agent version that is much more robust" | The spec contract has two readers | 1P | S18 |
| 2026-08-06 | "Glass is the home base for our non-technical folks… where they interact with the coding agent on a daily basis" | Engineers see Glass as a front end for non-technical staff | 1P | S27 |
| 2026-08-29 | "The next generation of Inspect is under way" | Investment is concentrating on Inspect | 1P | S54 (@_dylanga) |
| 2026-09-01 | "Engineers, designers, and product managers collaborate in Inspect sessions," and 200+ internal agents run on it | PMs work inside Inspect | 1P | S53 |
| 2026-09-10 | The define step is Glass, with three branches: the job to be done (goals, VOTC, Snowflake, Hex), the requirements (Notion strategy, the spec template as a SKILL.md, the codebase through Inspect), and the prototype (product principles, the Figma design system) | The CPO's official framing puts define in Glass | 1P | S1 |

## What would settle it (not public)

- Session counts by role and tool: how many PM sessions start in Glass, Claude Code, or Inspect.
- Where spec drafts are stored: local files, Glass Projects, Notion, or Inspect sessions.
- What's in Dojo's Product kit, whether the product-shaping skill is in it, and how often it runs
  in Glass.
- Whether Glass is converging with Claude's own apps (S75).

Tracked as open questions in the [Glass PRD](prd-glass.md#open-questions).

## What this means for us

1. **Put the shaping method in portable skills, not in one app.**
   - Ramp's shaping skill ran in Claude Code, and the same kind of skill bundle runs in Glass and
     in Inspect (S55, S66). That's H-009 in miniature: the runtime changes and the method
     survives.
   - It also fits our "stop 2" (standardized shaping skills in each PM's own Claude Code), which
     Ramp itself went through ([path](../../../../context/wiki/path.md)).
2. **A front door pre-wired to context gets used without a mandate.**
   - Glass went from 3 to 976 weekly users in four weeks with no launch announcement (S78). That's
     evidence for earned adoption (DEC-008) and for H-011.
   - But Glass's first job was removing setup friction, not a PM move. PM skills arrived later, as
     a kit.
3. **The spec contract (Q-008) gets a discipline and a gap.**
   - The discipline, from the skill:
     - a one-sentence framing gate
     - an evidence bar (quantified, attributed, honest about causality)
     - requirement IDs tied to evidence
     - closed questions with sources
     - research saved as files
   - The gap: it stops at "specific enough to prototype." At Ramp, acceptance criteria show up
     later, at the Inspect session boundary. Its docs ask each session for "acceptance criteria
     that define success" (S20). A regulated setting needs them in the spec itself.
   - The tools have moved past Ramp here. The second-pass survey (2026-09-28) found that most
     spec-driven tools now require acceptance criteria before build: EARS statements in Kiro,
     Given/When/Then in Spec Kit, and a "decision complete" plan with tests in Codex. That makes
     Ramp's exit bar the outlier ([landscape](../../landscape.md)).
4. **Keep the brief, the evidence, and the prototype together in one governed, shared place.**
   - Ramp hasn't done this yet:
     - A designer calls the missing "source of truth for the project" a blocker (S62).
     - Research tooling is "fairly chaotic" (S61).
     - Inspect's plan to hold "the brief… the research" isn't in its docs (S20).
   - That gap is our opening (H-002, H-012). A private desktop app can't fill it.
