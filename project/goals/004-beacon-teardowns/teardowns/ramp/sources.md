# Ramp teardown: sources

Every claim in the teardown cites a key from this register. `S1 12:22` means source S1 at 12:22,
and "S1 slide 12:06" means the slide on screen at that time.

**Kinds of source:**
- **1P**: first-party (Ramp, or a Ramp employee)
- **Vendor**: a supplier's case study with Ramp quotes
- **2P**: secondary (a summary or report of first-party claims)
- **3P**: an independent observation
- **Artifact**: a public artifact that was observed directly

The teardown says "said" for anything resting on 1P, vendor, or 2P sources, and "observed" only for
3P sources or artifacts. Unless noted, sources were fetched on 2026-09-27, many through public
mirrors because the originals block crawlers (X via api.fxtwitter.com; some pages via r.jina.ai).
Full texts of the key articles and transcripts are kept locally, outside git, in
`project/context/inbox/_local/`.

## Primary: the talk

| Key | Source | Date | Kind | Notes |
|---|---|---|---|---|
| **S1** | Geoff Charles (Ramp CPO), "What product looks like when coding is solved," Lenny & Friends Summit. [YouTube](https://youtu.be/ZG8Mf3P9xzI) (Lenny's Podcast, with Stripe). Syndicated earlier as "The limiting factor—how to design an AI software factory for speed" | recorded 2026-09-10; uploaded 2026-09-25 | 1P | Auto-captions plus 1080p slide frames. [Digest](../../../../context/inbox/_processed/2026-09-27-ramp-cpo-talk.md). The figures 93%, 425, 85%, and 60% were spoken, not shown on a slide |

## Glass and Ramp's AI program

| Key | Source | Date | Kind | Notes |
|---|---|---|---|---|
| S2 | Seb Goddijn, X article, "We Built Every Employee at Ramp Their Own AI Coworker." [Post](https://x.com/sebgoddijn/status/2042285915435937816) | 2026-04-09 | 1P | **Recovered** on 2026-09-27 through the public fxtwitter API. The beacon scan had hit HTTP 402. Credits six builders |
| S3 | Eric Glyman (CEO), X post. [Link](https://x.com/eglyman/status/2043362828178841860) | 2026-04-12 | 1P | |
| S4 | Rich Holmes, Department of Product, "How to Build Powerful Internal AI Productivity Tools." [Link](https://departmentofproduct.substack.com/p/how-to-build-powerful-internal-ai) | 2026-04-13 | 2P | |
| S5 | KiKi (note.com), a summary of S2. [Link](https://note.com/_kihonushi/n/n7ae960fcbde5?hl=en) | 2026-04-14 | 2P | Superseded by S2 |
| S6 | Zac Smith, AI Catchup, "Ramp Glass Playbook." [Link](https://aicatchup.com/practices/internal-ai-workspaces-playbook) | 2026-04-15; updated 2026-08-30 | 2P | Source for "internal only, on no product page" |
| S12 | Simon Taylor, Fintech Brainfood, "Ramp Cracked Enterprise AI." [Link](https://www.fintechbrainfood.com/p/ramp-cracked-ai) | 2026-04-19 | 2P | Commentary |
| S13 | Hacker News item 47729761, linking to S2 | 2026-04 | 3P | Essentially no discussion |
| S14 | Geoff Charles, X article, "How to get your company AI pilled." [Post](https://x.com/geoffintech/status/2042002590758572377) | 2026-04-08 | 1P | Glass "built on Anthropic's Claude Agent SDK"; adoption metrics; L0–L3 proficiency; leaderboard; org model |
| S15 | Shane Buchan, X article, "How We Built Glass: Vibe Coding a Product Used by 700 People." [Post](https://x.com/shanebuchan/status/2044524727679566156) | 2026-04-15 | 1P | Architecture: MCP proxy, Git-backed Dojo, memory pipeline, dev practices |
| S16 | Ramp, "Ramptables Episode 2: Project Glass" (Ben Levick with Seb Goddijn). [YouTube](https://www.youtube.com/watch?v=di0rLBrBP8A) | 2026-05-21 | 1P | Captions. Origin, launch pain, Dojo at about 800 skills, memory v2, Ramplify, and the Notion product-Q&A agent ("85% … no human in the loop") |
| S32 | Notion, customer story, "Ramp runs on Notion." [Link](https://www.notion.com/customers/ramp) | metadata 2025-05-12, updated later | Vendor | 300+ Notion agents, including the "Product Q&A Oracle" and the "Sales Feedback Categorizer"; Ben Levick is "Head of Operations & Internal AI" |
| S33 | Notion blog, "How Ramp built an AI operating system for scalable work." [Link](https://www.notion.com/blog/how-ramp-built-an-ai-operating-system) | 2025-12-02 | Vendor | The knowledge-correction loop; weekly project updates generated from five sources |
| S35 | Ramp blog, "Eric Glyman on using AI to radically boost internal productivity." [Link](https://ramp.com/blog/ai-for-internal-productivity) | 2024-07-31 | 1P | An applied AI team embedded with other teams; "Toby," a call-summary agent |
| S39 | YakLabs "About" page ([link](https://yaklabs.ai/about)) and the X bios of Goddijn ("prev created Glass @tryramp") and Buchan ("prev. Ramp") | fetched 2026-09-27 | 1P | Glass's lead now co-founds YakLabs. The departure dates aren't public |
| S44 | Ara Kharazian (Ramp economist), "How much does it cost to be AI-pilled?" [Link](https://ramp.com/data/ai-index-june-2026) | 2026-06-10 | 1P (market data) | Pushes back on "spend a salary on tokens" |
| S50 | Ramp blog, "Introducing Ramp Applied AI Solutions" (Ori Daniel). [Link](https://ramp.com/blog/introducing-ramp-applied-ai-solutions) | 2026-06-10 | 1P | An external service built on Ramp's internal experience: "Ramp spent years building that capability for itself" |

## CPO interviews and posts

| Key | Source | Date | Kind | Notes |
|---|---|---|---|---|
| S17 | Peter Yang, *Behind the Craft*, "Inside Ramp, the $32B Company Where AI Agents Run Everything" (Geoff Charles). [YouTube](https://www.youtube.com/watch?v=RBqT2PHWdBg); [post](https://creatoreconomy.so/p/inside-ramp-the-32b-company-ai-agents-geoff-charles) | 2026-03-15 | 1P interview; the host's post is 2P | Demos of the VOC agent and the product-shaping skill; "ramp releases" bot; "double-digit percentage … automatically approved." The post is paywalled after the preview |
| S18 | Rex Salisbury, *Cambrian*, "How AI Rewrote Ramp's Product Playbook" (Geoff Charles). [YouTube](https://www.youtube.com/watch?v=IGyYfRZvO_s) | 2026-07-22 | 1P interview | 22 PMs out of 1,600 people; human and agent specs; "grandma testing"; VOC tied to contribution profit |
| S40 | Geoff Charles, X post, "At Ramp we ship a new major feature every day…" [Link](https://x.com/geoffintech/status/1996401943774626232) | 2025-12-04 | 1P | The release gate: early access whenever a team wants; review for GA; "Leadership has 48h to review or it ships" |
| S47 | Lenny's Newsletter, "How Ramp builds product" (2023-05-23), and Lenny's Podcast, "Velocity over everything" (2023-08-06), both with Geoff Charles | 2023 | 1P | The velocity culture; bottleneck thinking from before AI |
| S49 | Ramp blog, "How we build with velocity at Ramp." [Link](https://ramp.com/blog/how-we-build-product-at-ramp) | 2023-05-22 | 1P | "Every spec, design, decision, progress and status is published in project-specific Slack channels" |

## Inspect, Review Buddy, Testo, and engineering

| Key | Source | Date | Kind | Notes |
|---|---|---|---|---|
| S7 | Ramp Builders, "Why We Built Our Own Background Agent" (Zach Bruggeman, Jason Quense, Rahul Sengottuvelu). [Link](https://builders.ramp.com/post/why-we-built-our-background-agent). Also the launch posts on X that day by Bruggeman, Sengottuvelu, and Glyman | 2026-01-12 (on the page) | 1P | The beacon scan listed it as "undated" |
| S8 | InfoQ, "Ramp Builds Internal Coding Agent That Powers 30% of Engineering Pull Requests." [Link](https://www.infoq.com/news/2026/01/ramp-coding-agent-platform/) | 2026-01-23 | 2P | |
| S19 | Gergely Orosz, Pragmatic Engineer, "Why Ramp built its own in-house coding agent, Inspect." [Link](https://newsletter.pragmaticengineer.com/p/why-ramp-built-inspect) | 2026-08-25 | 2P (from interviews and charts Ramp provided) | Paid; **free preview only**. Team size, 200+ agents on Inspect, 75% of PRs, Review Buddy "built by a single engineer in a week," Testo "creates Playwright tests" |
| S20 | Inspect documentation site. [Link](https://inspect.engineering/documentation) | undated; fetched 2026-09-27 | 1P | Pulled from the public JS bundle. Review Buddy's reviewer panel and rules.yml; automations and proposal cards; scoped secrets |
| S21 | Public GitHub artifacts: PRs with Inspect and Review Buddy output (e.g., [pranjalv123/ASTRID #21](https://github.com/pranjalv123/ASTRID/pull/21)–#27; 67 PRs carrying the `ramp-inspect-session-links` marker), plus the metadata for the "Inspect by Ramp" GitHub App (owner `ramp-public`, created 2026-08-07) | 2026-08-07 to 09-14 | Artifact | Directly **observed**. They may reflect dev or canary deployments |
| S22 | Dylan Garcia (Ramp), X article, "Inspect at Scale." [Post](https://x.com/_dylanga/status/2067999346780524753) | 2026-06-19 | 1P | 76.5% of PRs; 750+ daily users; 10,000+ sessions a day; sessions traced end to end; "Review Buddy and Testo" |
| S23 | Modal case study, "How Ramp built a full context background coding agent on Modal" (2026-02-19), and the Modal video with Bruggeman and Sengottuvelu (2026-02-18) | 2026-02 | Vendor; 1P statements | |
| S24 | Linear customer story, "The coding agent behind 75% of Ramp's merged PRs" (undated, revised after 2026-05-27), and Linear's LinkedIn post, "60%+" (2026-04-27) | 2026-04/05 | Vendor | |
| S25 | Rahul Sengottuvelu (CTO), X thread on risk-tiered review (2026-06-17), and "57% of merged PRs" (2026-02-09) | 2026 | 1P | |
| S26 | Hamid Dadkhah (Head of Engineering), X post on the "software factory." [Post](https://x.com/hamidships/status/2082656041267822828) | 2026-07-29 | 1P | Framed as general advice |
| S27 | Anthropic (Claude channel), "How Ramp engineers work with AI agents at every step" (Austin Ray, Rahul Sengottuvelu). [YouTube](https://www.youtube.com/watch?v=i4odXOmgMLw) | 2026-08-06 | Vendor; 1P statements | The captions have no speaker labels |
| S28 | Ramp Builders, "How we built OCA, our AI on-call assistant." [Link](https://builders.ramp.com/post/how-we-built-oca-our-ai-on-call-assistant) | 2026-09-09 | 1P | |
| S29 | Ramp Labs, "Our 10,000-user app has one AI monitor for every 75 lines of code" (self-maintaining Ramp Sheets). [Link](https://ramplabs.substack.com/p/self-maintaining) | 2026-03-24 | 1P | |
| S30 | Ramp Builders, "Integrations That Write Themselves." [Link](https://builders.ramp.com/post/integrations-that-write-themselves) | 2026-08-14 | 1P | "You don't have to trust the code. You have to trust the artifacts." Also: "The workaround is the spec" (inferred meaning: the customer's current workaround defines what the integration must do) |
| S31 | Ramp Builders, "Online Learning for Cost-Efficient LLM Routing" (2026-07-20), and "You're Spending Too Much on AI. You're Also Using Too Little." (2026-06-17) | 2026-06/07 | 1P | LLM gateway; cost controls |
| S41 | Hacker News thread on S7 (item 46589842; 122 points, 27 comments) | 2026-01-12 to 16 | 3P | Includes a self-described Ramp engineer and skeptics |
| S42 | Open-source rebuilds of Inspect from its public write-up, e.g., [Open-Inspect](https://github.com/ColeMurray/background-agents) (~3.3k stars) | 2026-01 on | 3P | Replication, not observation of Ramp |
| S43 | Ramp Builders, "We proactively fixed ~100 security issues in 6 days with 0 humans." [Link](https://builders.ramp.com/post/100-vulnerabilities-patched-with-0-humans) | 2026-02-20 | 1P | |
| S45 | Ramp job post, "Software Engineer, Engineering Platform" (Ashby) | 2026-04-27 | 1P | "The Engineering Platform team helps 300+ Ramp engineers" |
| S46 | Zach Bruggeman, X post on "Orchestrate." [Post](https://x.com/zachbruggeman/status/2075598835100123419) | 2026-07-10 | 1P | |
| S48 | AI Engineer, speaker page for Rahul Sengottuvelu. [Link](https://ai.engineer/speakers/rahul-sengottuvelu) | undated | 2P | Says he became Ramp's CTO in June 2026. He was earlier "Head of Applied AI" (S23) |

## Data, insight, and ML platform

| Key | Source | Date | Kind | Notes |
|---|---|---|---|---|
| S9 | Ramp Builders, "Meet Ramp Research: Our Agentic Data Analyst." [Link](https://builders.ramp.com/post/meet-ramp-research) | 2025-09-18 (on the page) | 1P | |
| S10 | Ramp Builders, "Building a Unified Pipeline for AI Token Spend." [Link](https://builders.ramp.com/post/ai-token-spend-management) | about April 2026 | 1P | **About Ramp's customer-facing AI-spend product**, not internal tracking (correcting the beacon scan). Internal usage tracking is in S14 and S17 |
| S11 | Ben Levick (Head of Operations), "How to build your team to capitalize on AI." [Link](https://ramp.com/leading-indicators/how-to-build-your-team-to-capitalize-on-ai) | 2025-09-26 | 1P | |
| S34 | Prefect, "Building an ML Platform for the Agent Era with Prefect" (Ramp case study). [Link](https://www.prefect.io/blog/ramp-case-study) | 2026-04-23 | Vendor | Corroborates the Prefect workflows on the VOTC slide |

## Added in round 2 (2026-09-27, evening): X timelines and on-screen evidence

| Key | Source | Date | Kind | Notes |
|---|---|---|---|---|
| S51 | Teddy Riker (Ramp PM), X article, "Lessons from 5 Billion Tokens." [Post](https://x.com/teddy_riker/status/2039649121812840796) | 2026-04-02 | 1P | Specs have gone from document to HTML prototype to "working branches in our QA environment, with a PR"; writing is stress-tested against simulated stakeholders; "human verification bandwidth" is the binding constraint |
| S52 | Teddy Riker, X article, "Let the agents pay!" [Post](https://x.com/teddy_riker/status/2077358701506068688) | 2026-07-15 | 1P | Ramp's thinking on agentic commerce for customers. Useful here for its "economic autonomy" levels (provisioned consumption, directed execution, bounded delegation) and its oversight checklist |
| S53 | René Sultan (Ramp Labs), X article, "Building the missing layer between AI spend and ROI." [Post](https://x.com/RampLabs/status/2094871453879402747) | 2026-09-01 | 1P | Turns Inspect traces into "work items" (one objective, one outcome each). Builds a taxonomy of agentic work from the bottom up (30 categories from about 250,000 work items). Confirms that PMs collaborate in Inspect sessions and that 200+ agents run on Inspect |
| S54 | **X timelines** of Ramp leaders and builders, harvested 2026-09-27 via the public fxtwitter API. Covers posts since 2025-10-01 from @geoffintech, @eglyman, @karimatiyeh, @rahulgs (CTO), @hamidships (Head of Eng), @sebgoddijn, @shanebuchan, @zachbruggeman, @_dylanga, @bleviathan (Ben Levick), @diegozaks (design), @ian_dot_so, @teddy_riker, @tkkong, @philhchen, @austospumanto, @vral, @RampLabs, and @tryramp | 2025-10 to 2026-09 | 1P | Cited as `S54 (@handle, date)`. The full JSON is kept locally, and each cited post links from the text where it matters |
| S56 | Prior Claude research artifact, "From PM idea to code: Stripe, Ramp, and who comes closest to the full loop." [Filed copy](../../../../context/inbox/_processed/2026-09-20-pm-idea-to-code-stripe-ramp.md) | 2026-09-20 | 2P (an agent's synthesis) | Checked here against primary sources. Its account of the shaping skill matches the frames (S55). The Stripe section and the 11-company scorecard are leads for other teardowns |
| S55 | **On-screen material in S17** (the *Behind the Craft* interview), read from 1080p frames: the product-shaping `SKILL.md` (14:08–14:51), the Inspect Chrome extension on the live product (16:20–18:58), the VOTC agent in Slack with Braintrust traces (04:52–05:50), `#ask-ramp-research` (08:32–09:00), and an Inspect thread in `#project-ux` (19:34–19:48) | 2026-03-15 | observed (1P artifacts on screen) | The full skill transcription is kept locally. The teardown only summarizes it |

## Added in round 2b (2026-09-27, late): talks, interviews, and written sources on Glass (S57–S86)

Two research agents covered these. Where YouTube captions were blocked, the audio was transcribed
locally. Transcripts and notes stay local (third-party text; the repo is public). "Ramp speaker"
means a Ramp employee speaking for themselves on a public stage; "1P interview" means a Ramp
employee answering a host.

### Videos

| Key | Source | Date | Kind | Notes |
|---|---|---|---|---|
| S57 | Ramp, "Ramptables #1: Procurement Team." [YouTube](https://www.youtube.com/watch?v=jK9OyFe19o4) | 2026-04-30 | 1P | The procurement PM: "I go there [Glass] first for everything" (31:35). The engineering lead: "PM uses Claude to write up a product spec" (15:17). The designer starts in a prototype, not Figma, and fixes UI through Inspect (32:48–33:34) |
| S58 | Ramp, "Tokenmaxxing OK ✅ AI Hackathon" (27-second reel, no speech). [YouTube](https://www.youtube.com/watch?v=_WRdWQFY_u8) | 2026-04-23 | 1P (on screen) | Counters: 650 participants, 100 AI mentors, 305 submissions. Glass isn't named. One project answers "who owns [feature]?" from Slack project channels |
| S59 | ICONIQ at HumanX, Eric Glyman (CEO) with Kate Clark (WSJ). [YouTube](https://www.youtube.com/watch?v=6iYHrloGrvc) | 2026-04-27 | 1P interview | Glass is "a Ramp-oriented harness": Snowflake, "understands your access privileges," "30 plus pre-built integrations," setup from about two hours to minutes (08:33–08:46). Inspect's live session board as the adoption driver |
| S60 | Notion, Make with Notion 2025, Ben Levick, "Simplicity at Scale: Inside Ramp's AI Operating System." [YouTube](https://www.youtube.com/watch?v=U7870-WNai8) | 2025-10-02 | Ramp speaker at a vendor event | The pre-Glass baseline: every laptop preloaded with ChatGPT, Notion AI and Perplexity; Notion holds the roadmap, project databases and a sales-feedback database |
| S61 | Tommy Geoco, *State of Play*, "Design at the most AI-installed company" (Diego Zaks, head of design). [YouTube](https://www.youtube.com/watch?v=KPDXMtmkcgk) | 2026-04-28 | 1P interview | Glass is "our internal equivalent to Claude Cowork… a harness for Claude or any LLM" (31:58), pushed to every laptop, signed in via Okta. Governance of internal tools: "yeah, chaos" (35:08). Design built a web-design taste skill in Glass (56:21). Designers find research participants through **Inspect** (18:55); the research-plan assistant is "in Slack, slash in Notion… fairly chaotic" (19:13) |
| S62 | *Sneak Peek with Jay*, George Visan (staff product designer). [YouTube](https://www.youtube.com/watch?v=mH5qIPx47jw) | 2025-12-29 | 1P interview | Pre-Glass designer baseline: prototype first (Magic Patterns), then Figma; Inspect as "our very own version of Cursor in the browser." The bottleneck is "a central area that serves as a source of truth for the project" (52:04) |
| S63 | The Pragmatic Summit, "Ramp: Lessons from Building a New AI Product" (Nik Koblov, Veeral Patel, Will Koh, Ian Tracey). [YouTube](https://www.youtube.com/watch?v=NMs8C2_3M0w) | 2026-03-09 | Ramp speakers | A PM "vibe-coded about 20 tools" for the product agent; Omnichat, one agent with many skills; Inspect over 50% of merged PRs; product teams' "context documents" feed Inspect sessions (29:36) |
| S64 | Data Driven NYC, Alex Levinson (Ramp Labs), "How Ramp Built Self-Maintaining Software." [YouTube](https://www.youtube.com/watch?v=Fgzs4FBmRYw) | 2026-05-05 | Ramp speaker | Inspect as "a unit of SWE work that I can call through API." An experiment mines logs, feedback forms, LogRocket, Slack and Gong to find what users struggle with and "build it autonomously" (13:26) |
| S65 | Exit Five, George Bonassi (VP Growth). [YouTube](https://www.youtube.com/watch?v=r6UpmlKHN8k) | 2026-06-04 | 1P interview | Glass keeps team memory and a per-user voice file, tracks "how much are we spending on the skill," and runs scheduled jobs. "I use Glass for everything now… it's still Claude Code under the hood" (29:20–31:44) |
| S66 | Matia, *Crunching Data* live at Ramp NYC (Ian Macomber, VP Data; Ryan Delgado, data platform lead). [YouTube](https://www.youtube.com/watch?v=z4Ybde1SSsI); [written recap](https://www.matia.io/blog/crunching-data-live-ramp-ai-native-data-team) | recorded 2026-06; published 2026-08-06 | Ramp speakers at a vendor event | Glass's first PR came from a data-platform engineer in late 2025. It's "provider agnostic… Claude… Gemini or OpenAI" (30:34). Ramp Research is "a skill bundle… in Inspect… in Glass" (29:13) that installs itself when Snowflake is connected (46:49). Local agents assume the user's identity in Snowflake, and the speaker wants "a stiffer guardrail" (55:39) |
| S67 | Ramp, "Ramptables: How we built Ramp Stack for accounting firms." [YouTube](https://www.youtube.com/watch?v=3AulfosZ6Tc) | 2026-06-08 | 1P | Asked about Glass and other tools, the PM describes turning hundreds of design-partner calls into backlogs (25:58). He doesn't name the tool |
| S68 | Notion, customer video, "Inside Ramp's Custom Agent Operating System." [YouTube](https://www.youtube.com/watch?v=UxDmHwiWhG0) | 2026-02-24 | Vendor | 300+ Notion agents; sales feedback triaged to the roadmap in Notion |
| S69 | *Off Topic*, Diego Zaks. [YouTube](https://www.youtube.com/watch?v=qSvlB4a-QEs) | 2026-01-13 | 1P interview | Before Glass, a chain of research agents: one finds the right customers, one mines past calls, one drafts the research plan (29:00). "Designers writing code, writing specs; … PMs making prototypes" (31:17) |
| S70 | Stripe, *Cheeky Pint*, Eric Glyman with John Collison. [YouTube](https://www.youtube.com/watch?v=TRPCRIhrYac) | 2026-02-17 | 1P interview | Inspect in Slack for small product changes. No mention of Glass |
| S71 | Modal, "How Ramp built a background coding agent that writes over half of its pull requests" (Zach Bruggeman, Rahul Sengottuvelu). [YouTube](https://www.youtube.com/watch?v=ii9E5z8Gsrc) | 2026-02-18 | Vendor; 1P statements | The first excited Inspect users were "product managers and… designers"; no local setup required |

### Written

| Key | Source | Date | Kind | Notes |
|---|---|---|---|---|
| S72 | Ben Levick, LinkedIn article, "What Happens When You Tell a Thousand People to Build with AI." [Link](https://www.linkedin.com/pulse/what-happens-when-you-tell-thousand-people-build-ai-benjamin-levick-oorfe) | 2026-04-08 | 1P | Glass "brings all the features of a highly configured Claude Code to our whole team with no need to open the terminal"; "hundreds of domain-specific skills served by Dojo." 1,500+ apps on the internal hosting platform in six weeks from 800+ builders. The hub-and-spoke org |
| S73 | Ben Levick, LinkedIn article, "The AI Adoption Challenge is a Synchronization Challenge." [Link](https://www.linkedin.com/pulse/ai-adoption-challenge-synchronization-benjamin-levick-8z5le) | 2026-04-24 | 1P | The generations: knowledge-base RAG (2024), Ramp Research (2025), Inspect, then Glass, "a deeply connected AI workplace tool on top of Claude Code" |
| S74 | Ben Levick, LinkedIn activity, read from his public profile | captured 2026-09-27 (posts about 2026-02 to 06) | 1P | "Glass and Inspect – our non-engineer AI agent platform and our cloud based coding agent, respectively." Company post: "99.5% of Ramp uses an AI workspace… We call it 'Glass'" |
| S75 | Anthropic, "Centrally manage authorization for MCP connectors." [Link](https://claude.com/blog/enterprise-managed-auth) | 2026-06-18 (GA update 2026-08-24) | Vendor, quoting a Ramp staff IT engineer who worked on Glass | "Now they log in to Claude on day one already connected — 2,000 employees, provisioned through Okta." Access is consistent "across Claude chat, Claude Code, and Cowork." How this relates to Glass isn't said |
| S76 | Ramp job postings on Ashby (158 live), read through the public posting API | fetched 2026-09-27 (postings dated 2026-02 to 09) | 1P | Designer (2026-02-09): "Start in an LLM: Use tools like Claude to clarify intent, draft short PRDs." PM postings (2026-06 to 08) name Claude Code, Cursor and Bolt for prototyping. Only CX postings name Glass. No open Glass or internal-AI roles; a new "AI Solutions" team |
| S77 | Jay Sobel (Ramp engineer who started Glass), "A Smattering of AI Takes." [Link](https://jaysobel.substack.com/p/a-smattering-of-ai-takes) | 2026-08-29 | 1P | His own setup is now a vendor desktop app. Internal tools at Ramp show "blowout" outcomes beyond the vendor cluster. Calls engineers owning prompts and context "a leadership failure" |
| S78 | **Screenshots embedded in S2 and S15**, read visually | 2026-04-09, 2026-04-15 | observed (1P artifacts) | Weekly usage: 3 users (week of 03-12) to 976 users and 10,293 sessions (week of 04-02). The memory agent "Scout," with a pending queue (Approve/Dismiss) and categories People, Active Work, Capabilities, Preferences, Organization. Connections with per-tool Auto/Allow/Ask. Dojo kits: Essentials, Sales, Account Management, CX Leadership, Marketing, **Product**, **Design**, Data, Finance, Risk, People & Talent, Legal & Compliance. An agents panel listing the user's Notion agents and the Glass team's daily automations |
| S79 | A public, de-Ramp-ified copy of the product-shaping skill (third party). [GitHub](https://github.com/mmccarthyhearst/useful-skills) | 2026-03-15 | 3P | Used only to cross-check the frame transcription (S55). It matches, apart from genericized names and tools |
| S80 | Other X posts fetched one by one, cited as `S80 (@handle, date)`: @chapello (a Ramp PM), @ParthGujare_ (Ramp Revenue), @LeoMehr (AI services launch), @tryramp; third parties @tylerxdev and @jacob_posel | 2025-12 to 2026-09 | 1P unless marked | For example: a PM's personal setup is Claude Code with `/good-morning` skills and Notion (@chapello, 2026-03-27); "Ramp Revenue is our internal GTM Coworker used by >90% of all our GTM teams" (@ParthGujare_, 2026-07-24) |
| S81 | Deepline, recap of Keyan Sarrafzadeh's GTM AI NYC talk. [Link](https://deepline.com/blog/gtm-ai-nyc-keyan-ramp) | 2026-06-30 | 2P | Ramplify apps "plug into our core data and follow permissions"; a "growth MCP" in front of GTM systems |
| S82 | Paul Jun (Ramp brand), "Brand as software." [Link](https://pauljun.substack.com/p/brand-as-software) | 2026-09-11 | 1P | A Slack brand-production agent that turns a brief into decks and one-pagers |
| S83 | Design-tooling event: Caroline Horn's LinkedIn posts (Glass team designer) and SPC's "Design Tools Demo Night" (2026-07-14; [SPC July update](https://blog.southparkcommons.com/p/july-2026-update), 3P) | 2026-07 | 1P and 3P | Ramp presented "designer tooling… to help teams with better design judgment." **No recording found** |
| S84 | Ramp Builders, "Agentic identity: modeling agents to keep users in control." [Link](https://builders.ramp.com/post/agent-identity-introduction) | 2026-05-04 | 1P | For customers' agents (Ramp for Agents). Each agent has a key, attribution ("Approved by Sarah (via Codex)"), scope that never exceeds its human sponsor's, and expiry by default |
| S85 | Ramp Builders, "Agentic Risk Operations." [Link](https://builders.ramp.com/post/agentic-risk-operations) | 2026-06-30 | 1P | Risk operators edit agent skills themselves; new configurations run in shadow mode first; each agent has an exposure budget; "every autonomous risk decision is still made by an auditable model, governed under an approved policy" |
| S86 | Ramp Builders, "Stack Benchmarking." [Link](https://builders.ramp.com/post/stack-benchmarking) | 2026-06-03 | 1P | Skill ablation on a customer product: "Agent systems tend to accumulate too many skills, and those skills tend to get too long." Only two skills helped on average; most hurt. A slimmer bundle scored better |
## Added in round 3 (2026-09-28): outside views of Glass (S87–S94)

A research pass for informed outside takes on Glass. There is no deep independent teardown of Glass
anywhere public: the informed material comes from former Ramp builders, Ramp people writing about
nearby systems, a few analysts, and competitors. X posts by Ramp people already covered by S54 are
cited as `S54 (@handle, date)`.

| Key | Source | Date | Kind | Notes |
|---|---|---|---|---|
| S87 | **On-screen material in Shane Buchan's Glass Projects video.** [Post](https://x.com/shanebuchan/status/2052044794285666496) | 2026-05-06 | observed (1P artifact) | A project picker before the first prompt; "Default · Opus 4.7" in the composer; the agent drives Glass's own interface through an internal tool to open seven parallel sessions, each with its tool calls visible |
| S88 | Ian Macomber (Ramp VP Data), essay on the post-AI data stack. [Link](https://www.iandmacomber.com/blog/post-ai-data-stack) | 2026-08-30 | 1P | Ramp's research harness is evaluated across interfaces (including a "coworker", a coding agent, BI, and Slack) and across models, with a "consensus divergence rate" and a check that authorization outcomes match everywhere. That "coworker" means Glass is inferred |
| S89 | YakLabs and Kay, the new company and product of Glass's creator: [about](https://yaklabs.ai/about), [manifesto](https://yaklabs.ai/manifesto.html), [product](https://meetkay.ai), [docs](https://docs.meetkay.ai) | fetched 2026-09-28 (docs dated 2026-09-09) | former 1P | An invite-only macOS workspace, "a single pane of glass for all of your AI work": automatic model routing with open-weight models by default or your own keys; SKILL.md skills (it reads `.claude/skills/`); skill sources and plugins load only with a person's approval ("the agent can propose, but only a human can grant"); no MCP connectors yet; usage telemetry on by default. The manifesto calls top-down enterprise AI "bottlenecked by infosec" |
| S90 | Anthropic, "Cowork is now Claude." [Post](https://claude.com/blog/cowork-is-now-claude). Also the Cowork help center ([article](https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork)) and org plugin marketplaces ([post](https://claude.com/blog/cowork-plugins-across-enterprise)) | 2026-09-16 | Vendor | Cowork folded into Claude. Claude now offers cloud runs, schedules that run with no device online, projects with memory, org plugin marketplaces (including a "Required" state), OpenTelemetry events, a Compliance API, and identity-provider-managed connector auth. Enterprise plans keep Cowork as-is for now, with 30 days' notice of changes |
| S91 | OpenAI, ChatGPT workspace agents for Enterprise and Business (help center). [Link](https://help.openai.com/en/articles/20001143-chatgpt-workspace-agents-for-enterprise-and-business) | fetched 2026-09-28 | Vendor | Warns that shared agents using personal connections act "as the creator". That's the failure Ramp hit when Glass's Slack assistants posted as their owners (S16) |
| S92 | Outside commentary on Glass: Melody Koh (NextView) [post](https://x.com/melodykoh/status/2042216858892243173); Kyle (ForgeVista), "The AI-Pilled Operating Company" [post](https://x.com/selectstarkyle/status/2044995153174159489); Headways [post](https://headways.ai/blog/ramp-glass-lessons-enterprise-ai) | 2026-04-09 to 2026-04-17 | 3P | Most companies can't replicate Glass without Ramp's engineering; it's single-player, so "the collaboration surface remains an issue"; a company must own this layer but needn't build it; agent identity needs its own governance |
| S93 | Glass-like products: HQ ("Ramp glass for every business") [site](https://hqforwork.com), [docs](https://docs.hq.computer), [launch post](https://x.com/jacob_posel/status/2052108809439432736); Indent [site](https://indent.com), [docs](https://docs.indent.com) | 2026-05-06 to 2026-09-28 | Vendor | HQ: a file-based company memory with access control in files, synced skills, and skill-usage visibility over Claude Code and Codex. Indent: a hosted, shared coworker whose sessions are visible to the whole org by default, with memory scoped to person, org, repo, or automation |
| S94 | Event facts: Accel, "How to AI Pill Your Company" (2026-09-17); Floodgate NYC (2026-09-28); Fintech Nerdcon (2026-11-19/20); dbt Summit session by Jay Sobel covering Glass (2026-09-15 to 18) | 2026-09 | 3P (event pages) | Glass's creator and originator speaking. **No recordings found** as of 2026-09-28 |

## Event and reception

| Key | Source | Date | Kind | Notes |
|---|---|---|---|---|
| S36 | Event facts: the YouTube description ("Recorded live at Lenny and Friends Summit on September 10, 2026, in San Francisco"), [lennyssummit.com](https://www.lennyssummit.com/) (SVN West; presented by Stripe), and YouTube metadata (a Lenny's Podcast and Stripe collaboration; the "Lenny & Friends Summit 2026" playlist) | 2026-09 | 2P | "Claire" in the talk is Claire Vo, a speaker the same morning. "Ron" is unresolved |
| S37 | Darshen Patel (attendee), "Building Got Cheap. Judgment Didn't." [Link](https://darshen.substack.com/p/building-got-cheap-judgment-didnt) | 2026-09-18 | 3P | Warns against "mistaking throughput for progress" |
| S38 | YouTube comments on S1 | about 2026-09-26/27 | 3P | Some skeptical ("zero proof whatsoever"). Others ask how many engineers build the factory and what it costs |
