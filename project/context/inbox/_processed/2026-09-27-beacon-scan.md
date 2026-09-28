---
source: web scan (public sources), 2026-09-27, by a background agent; unverified first pass
tags: [beacons, landscape, teardown-seed]
---

# Beacon scan: public landscape, first pass (2026-09-27)

Broad and shallow, and it seeds the teardown workstream. It is not a teardown. All searches and
fetches ran on 2026-09-27.

- **Citations.** Bracketed numbers point to the source list at the end of each section. "Says"
  means it's the company's own claim. "Observed" means a third party saw or tested it.
- **Blocked pages.** Several pages blocked automated fetching: X, Forbes, CNBC, openai.com,
  Atlassian Community, and Medium. When a claim is read only from a search-engine snippet, the
  text says so. Dates marked "per search listing" come from search metadata, not from the page.

## Summary

**What Glass is.** Glass is Ramp's **internal** AI productivity suite. Ramp's framing is that it
gives "every employee at Ramp their own AI coworker." Ramp's Seb Goddijn and colleagues described
it publicly in an X article on 2026-04-09, and CEO Eric Glyman amplified it on 2026-04-12. It is
not a product. A third-party check on 2026-08-30 found it on no Ramp product, pricing, or
announcement page. Ramp's account could only be read through secondary summaries because X blocks
crawlers. By that account, Glass has these parts:

- **Pre-configured workspace.** One Okta SSO sign-in wires up every tool.
- **Per-user memory.** A 24-hour synthesis pipeline rebuilds it from Slack, Notion, Linear, and
  Calendar.
- **Dojo.** A marketplace of 350+ markdown skills that are "Git-backed, versioned, and reviewed
  like code."
- **Sensei.** A recommender that suggests skills based on role, connected tools, and recent
  activity.
- **Automations.** Scheduled or headless jobs that post to Slack.

Ramp's thesis is that "the models are good enough"; the harness is what's missing. Glass sits next
to two other internal agents:

- **Inspect**, a hosted background coding agent. PMs and designers use it too, and Ramp says it
  writes about 30% of merged PRs.
- **Ramp Research**, an agentic data analyst in Slack.

**Five I'd prioritize for a deep teardown:**

1. **Ramp (Glass, Inspect, Research).** It's the owner's example. It's also the fullest public
   account of a shared, company-wide harness with governed skills, memory that accretes, and
   automations, and PMs ship code through it. The teardown must capture the primary X article by
   hand.
2. **LinkedIn (Full Stack Builder agents and CAPT).** This is the closest enterprise-scale match to
   the thesis. It has agents for PM moves (trust, growth, research, analyst) and a governed context
   layer. Playbooks get InfoSec review, every call is logged, and agents are told to write
   learnings back into playbooks. It reports 8,000+ daily users, PMs among them.
3. **Citi (Arc).** This is the regulated-bank case: an agent platform run "within our risk
   framework." There's also a weakly sourced report that product development now runs
   requirements, risk review, and development at the same time, with four agents. Relevance is
   high and verification is low, which is why it's worth a teardown.
4. **AWS (AI-DLC and Kiro).** This is the most explicit method for turning intent into
   requirements and units of work, then into code. It logs human approvals, traces intent to code,
   and has published guidance for a regulated industry. It's a concrete model for the
   product-to-agent spec handoff.
5. **Atlassian (Rovo and Teamwork Graph).** This is the incumbent context layer a regulated
   enterprise most likely already has. The graph keeps source permissions and is open to outside
   agents through MCP and a CLI. Atlassian's own PMs use its PRD, theme, and customer agents.

Anthropic's trace-based measurement of fluency and autonomy (§13) is worth a close read as a
*method*, even though it isn't a company teardown.

**Surprises:**

- **SDD tools are moving upstream into PM work.** In July 2026, GitHub Spec Kit added an "idea
  assessment" process: intake, research, define, shape, decide. It ends in go,
  needs-clarification, or kill, and it runs "even in a project with no source code" (§8).
- **Tessl changed direction.** It moved from spec-as-source code generation to a "package manager
  for agent skills" in January 2026 (§10).
- **One context pattern keeps showing up.** Skills or playbooks are versioned files, reviewed like
  code, that agents load. Examples: Ramp's Dojo (§0), LinkedIn's CAPT (§1), Tessl (§10), AWS
  steering files (§9), and Spec Kit's constitution and bundles (§8).
- **Most trace capture only tracks adoption and cost.** Examples are the Atlassian, Glean, and
  Microsoft dashboards and Ramp's token-spend tracking. Only Anthropic publishes methods for
  measuring fluency or delegation from traces. There, experienced users auto-approve more (about
  20% of sessions rising to 40%+) yet also interrupt more (§13). LinkedIn is the only one that
  plans to feed traces back into context (§1).

---

## Beacons

### 0. Ramp: Glass, plus Inspect and Ramp Research

**Category:** (a), (b). **One line:** a spend-management fintech that built an internal,
company-wide AI harness plus internal agents, with PMs among the users.

- **Started with.** After reaching 99% AI-tool adoption, Ramp noticed "most people were stuck":
  terminal setup, npm installs, and MCP configs were too hard, and people had no way to share what
  they learned [1][2][4]. So Glass targets setup friction, not one task.
  - Examples Ramp gave: a finance lead gets a daily 8 AM spend-anomaly summary in Slack. An ops
    team built a Slack assistant in a day that answers vendor-policy questions from Notion and
    Snowflake. A CX skill reached 60+ reps overnight [4].
  - The earlier agents started narrower. Ramp Research answered data questions in Slack from early
    August 2025 [7]. Inspect started with code changes that "close the loop" by verifying their own
    work [6].
- **Deployment model.**
  - *Glass:* per-employee, pre-configured on install. One Okta SSO sign-in connects Gong,
    Salesforce, Slack, Notion, Linear, Zendesk, Snowflake, and internal tools (Ramp Research, Ramp
    Inspect, Ramp CLI) [3][4][5]. Secondary summaries describe it as running locally ("turns your
    laptop into a server"). They mention scheduled and headless jobs, Slack-native assistants, and
    a tiled multi-pane workspace [4]. The underlying model and harness are not disclosed
    (`unverified`).
  - *Inspect:* hosted sandboxes on Modal, with per-repo images rebuilt every 30 minutes, running
    the OpenCode agent. Users reach it through a Slack bot, a web UI (VS Code plus desktop
    streaming), or a Chrome extension [6].
  - *Ramp Research:* a Slack app, with a headless API planned [7].
- **Context approach.**
  - *Glass memory* "builds automatically" from authenticated connections. A synthesis and cleanup
    pipeline runs every 24 hours over Slack, Notion, Linear, Calendar, and past sessions [4][5].
    Connected systems are scoped to each employee's permissions [5].
  - *Dojo* holds 350+ skills, each a markdown file, "Git-backed, versioned, and reviewed like
    code." *Sensei* recommends skills from role, connected tools, and recent activity [4][5].
  - *Ramp Research* draws metadata from dbt, Looker, and Snowflake, plus domain-expert docs kept in
    a file system. It has no access to PII [7].
- **Traces and telemetry.**
  - *Glass:* not disclosed, beyond Sensei using "recent activity" [4].
  - *Inspect:* merged PRs are the key metric. Ramp also shows org-wide usage over time and a live
    "humans prompting" count [6].
  - *Research:* evals in the dbt project check intermediate steps, not just answers: expected tool
    calls, table references, and query shape [7].
  - *Company-wide:* Ramp tracks AI token spend by person, team, project, and model [8]. Its ops
    lead wrote in 2025 that "we meticulously tracked tool usage" [9].
- **PM-specific.** Ramp built Inspect so every builder, "engineers, product managers, designers,"
  could ship code. The post covers teaching PMs and designers to use it. About 30% of merged
  frontend and backend PRs are written by Inspect [6].
- **Said vs. observed.** Everything is Ramp's own account or a secondary summary of it. The Hacker
  News submission drew essentially no discussion [10]. I found no independent observation.
- **Regulated-enterprise relevance: Med.** This is the clearest public blueprint of a shared,
  governed harness that accretes context. But Glass's controls and compliance aspects aren't
  described publicly.
- **Confidence: Med.**
  - *High* for existence, internal-only status, and headline features. The sources agree and the
    CEO posted about it.
  - *Med* for architecture: local vs. hosted, and the memory pipeline. I couldn't fetch the
    primary X article (HTTP 402), so these details come from summaries.
- **Sources:**
  1. Seb Goddijn (Ramp), X post linking the article "We Built Every Employee at Ramp Their Own AI
     Coworker", 2026-04-09. https://x.com/sebgoddijn/status/2042285915435937816 (article:
     https://x.com/i/article/2042284478337269760, which returned HTTP 402)
  2. Eric Glyman (Ramp CEO), X post, 2026-04-12. https://x.com/eglyman/status/2043362828178841860
     (text read via search snippet)
  3. Rich Holmes, Department of Product, "How to Build Powerful Internal AI Productivity Tools",
     2026-04-13. https://departmentofproduct.substack.com/p/how-to-build-powerful-internal-ai
  4. KiKi (note.com), summary of Ramp's article, 2026-04-14.
     https://note.com/_kihonushi/n/n7ae960fcbde5?hl=en (secondary source; treat its details with
     care)
  5. Zac Smith, AI Catchup, "Ramp Glass Playbook", 2026-04-15, updated 2026-08-30 after
     re-checking that Glass appears on no Ramp product or pricing page.
     https://aicatchup.com/practices/internal-ai-workspaces-playbook
  6. Ramp Builders, "Why We Built Our Own Background Agent" (undated). Announced on X on 2026-01-12
     (https://x.com/rahulgs/status/2010734250203455862). Covered by InfoQ on 2026-01-23
     (https://infoq.com/news/2026/01/ramp-coding-agent-platform/).
     https://builders.ramp.com/post/why-we-built-our-background-agent
  7. Ramp Builders, "Meet Ramp Research: Our Agentic Data Analyst" (undated on the page; 2025-09-18
     according to [5]). https://builders.ramp.com/post/meet-ramp-research
  8. Ramp Builders, "Building a Unified Pipeline for AI Token Spend" (undated; April 2026 per search
     listing). https://builders.ramp.com/post/ai-token-spend-management
  9. Ben Levick (Ramp Head of Operations), "How to build your team to capitalize on AI",
     2025-09-26. https://ramp.com/leading-indicators/how-to-build-your-team-to-capitalize-on-ai
  10. Hacker News item 47729761, which links to [1]. https://news.ycombinator.com/item?id=47729761
  11. Commentary: Simon Taylor, Fintech Brainfood, "Ramp Cracked Enterprise AI", 2026-04-19.
      https://www.fintechbrainfood.com/p/ramp-cracked-ai

### 1. LinkedIn: Full Stack Builder agents and CAPT

**Category:** (a), (b). **One line:** LinkedIn replaced its APM track with "product builders." It
built custom agents for product-lifecycle moves and runs a governed, instrumented context layer
that engineers and PMs use.

- **Started with.**
  - The Full Stack Builder (FSB) program launched in 2024 [3]. LinkedIn replaced its APM program
    with an Associate Product Builder program that teaches coding, design, and PM together [1].
  - Per a transcript summary of the podcast, the agents built for PM moves include [2]:
    - a trust agent that finds security vulnerabilities
    - a growth agent that evaluates growth opportunities
    - a research agent trained on user personas
    - an analyst agent that queries the LinkedIn graph
    - maintenance and QA agents
  - CAPT, the context layer, started with "debugging, on-call support, and analysis" [4].
- **Deployment model.**
  - *CAPT* is a Python package that works both as a CLI (for config and auth) and as a local MCP
    server that IDE agents connect to. It "ships to every laptop and updates silently" [4]. The
    2026 talk says it updates hourly [5]. It adds context to existing coding agents rather than
    being a new agent [4].
  - *FSB agents* are custom-built. Cohen: "We haven't seen anybody be able to work off the shelf
    immediately on our code base." An orchestration layer can hide the specialist agents from
    users [2].
- **Context approach.**
  - *Curated, not bulk.* Cohen says giving an agent access to your drive "does a very poor job
    understanding importance." Teams spent weeks building a "golden sample of examples" [2].
  - *Playbooks.* Each has a name, a description, and instructions. Central playbooks cover
    cross-cutting work, and local playbooks are checked into each repo. Any domain expert can
    write one [4][5].
  - *Governance.* Every playbook and tool gets an InfoSec review. Human reviewers flag duplicates.
    Unused or unmaintained items are "aggressively" deprecated [5]. OAuth credentials are stored
    in the OS keychain [4].
  - *How context accretes.* The system prompt tells agents to summarize what they learned at the
    end of a session and update the playbook code. LinkedIn plans background agents that mine "PRs
    and agent sessions and telemetry" to create or update playbooks [5]. The January 2026 blog
    says curation is deliberate for now, with automated generation as future work [4].
  - *Scale.* A search-first tool-discovery pattern gets past the roughly 30-tool context limit [5].
- **Traces and telemetry.** Every call logs when it happened, which repo, whether it succeeded, and
  which tool or playbook ran. These feed dashboards on adoption and failure rates [4]. Per-item
  usage drives deprecation [5].
- **Results (says).**
  - *January 2026:* more than 1,000 engineers and 500+ playbooks. Triage time dropped about 70% and
    data analysis got about 3× faster [4].
  - *2026 talk:* 8,000+ daily users and 600+ playbooks. Users include engineers, PMs, designers,
    and TPMs. It reports a 20% productivity gain with no loss of reliability [5].
- **Said vs. observed.** All first-party: a blog, a talk, and a podcast. Tomer Cohen is described
  as LinkedIn's *former* CPO by July 2026 [6]. I found no independent observation.
- **Regulated-enterprise relevance: High.** It's a large, complex, privacy-sensitive enterprise.
  The context layer has InfoSec review, logging, and deprecation discipline, and PMs are named
  users. It's a live test of "accrete context through agent loops."
- **Confidence.**
  - *High* for CAPT, from a first-party blog and talk.
  - *Med* for the FSB agent roster, which comes from a third-party transcript summary; Lenny's
    transcript is paywalled.
- **Sources:**
  1. Lenny's Newsletter and Podcast, "Why LinkedIn is replacing PMs with AI-powered 'full-stack
     builders' | Tomer Cohen", 2025-12-04. https://www.lennysnewsletter.com/p/why-linkedin-is-replacing-pms
  2. Teahose transcript summary of [1] (secondary, undated).
     https://www.teahose.com/podcast/Lenny's/Why%20AI%20is%20eliminating%20traditional%20product%20management%20_%20Tomer%20Cohen%20(LinkedIn%20CPO)
  3. Mark Samuels, Computer Weekly, "Interview: Tomer Cohen, chief product officer, LinkedIn",
     2025-04-02. https://www.computerweekly.com/news/366621679/Interview-Tomer-Cohen-chief-product-officer-LinkedIn
  4. Ajay Prakash and Nikhilesh Payyavuala, LinkedIn Engineering, "Contextual agent playbooks and
     tools: how LinkedIn gave AI coding agents organizational context", 2026-01-27.
     https://www.linkedin.com/blog/engineering/ai/contextual-agent-playbooks-and-tools-how-linkedin-gave-ai-coding-agents-organizational-context
  5. Ajay Prakash, "Context Engineering at LinkedIn: How We Built an Organizational Context Layer
     for AI Agents with MCP", QCon AI Boston 2026; InfoQ page dated 2026-09-19.
     https://www.infoq.com/presentations/linkedin-context-engineering/
  6. Amy Hsuan, Miro blog, "The full-stack builder and the new shape of the product organization",
     2026-07-22. https://miro.com/blog/tomer-cohen-canvas-26/

### 2. Atlassian: Rovo agents and Teamwork Graph

**Category:** (a), (b). **One line:** Rovo agents, including PRD and discovery agents, run on a
"Teamwork Graph" that keeps source permissions and is now open to outside agents.

- **Started with.**
  - Atlassian's own PMs use Rovo agents to draft and review PRDs, prepare "customer 360" briefs
    before calls, and analyze themes across Jira work items.
  - Atlassian says over 90% of its PMs use AI weekly and nearly 70% use Rovo Chat and Agents
    weekly. I read this only in search snippets; the pages were blocked [1][2].
  - The out-of-the-box "Product Requirements Expert" agent generates and reviews PRDs and suggests
    user stories. It reads Confluence, Jira, and third-party sources, and it can write Confluence
    pages and comments [3].
- **Deployment model.** Rovo (Search, Chat, Agents, Studio) is embedded in Atlassian's cloud apps.
  Since Team '26, outside agents can also reach the Teamwork Graph through two routes [4][5]:
  - a Rovo MCP server
  - a CLI with 300+ read and write commands, aimed at agents such as Claude Code and Cursor
- **Context approach.**
  - The Teamwork Graph holds "over 150 billion objects and relationships" across Atlassian and
    connected SaaS apps. Data enters "with its access controls intact" [4].
  - Custom Forge connectors for proprietary systems are generally available [4].
  - Atlassian mentions "freshness signals across 3P platforms" and "decision trails" [4].
  - It claims grounding gives "44% more accurate results while using 48% fewer tokens" [4].
  - Co-founder Mike Cannon-Brookes frames the edge as "institutional knowledge," since "anyone can
    get 'smarts' by the token" [6].
- **Traces and telemetry.**
  - The graph has audit logs, OAuth, and granular scopes [4].
  - Rovo Studio is generally available with roles, approvals, versioning, and audit.
  - Admin dashboards track AI adoption and credit use.
  - Agents in Jira are generally available with "full audit logging" [5].
- **Scale (says).** 14 million Rovo-assisted actions in a month, and agentic automations up 7× in
  six months [5][6].
- **Said vs. observed.** All vendor claims. Nobody has independently checked the accuracy and token
  claim.
- **Regulated-enterprise relevance: High.** Jira and Confluence are often the system of record for
  requirements and delivery. A graph that keeps permissions and is exposed over MCP is a context
  layer to build on rather than replace.
- **Confidence.** *High* for the Team '26 announcements. *Med* for internal PM usage, which comes
  from snippets only.
- **Sources:**
  1. Sherif Mansour (Atlassian), "Four agents Atlassian's product managers use to improve their
     product discovery workflows", Medium, around 2025-07-03 (date per search summary; page
     returned 403).
     https://sherifmansour.medium.com/four-agents-atlassians-product-managers-use-to-improve-their-product-discovery-workflows-2201b99b68af
  2. Atlassian Community, "How the Atlassian product management team uses Rovo Agents" (undated;
     wouldn't render).
     https://community.atlassian.com/forums/Atlassian-AI-Rovo-articles/How-the-Atlassian-product-management-team-uses-Rovo-Agents/ba-p/3059291
  3. Atlassian, "Product Requirements Expert" agent page (undated).
     https://www.atlassian.com/software/rovo/use-cases/agent-product-requirements-expert
  4. Jamil Valliani (Head of Product, AI), "Atlassian Teamwork Graph: The context engine behind your
     AI—everywhere", 2026-05-06. https://www.atlassian.com/blog/company-news/teamwork-graph-team-26
  5. Duncan Riley, SiliconANGLE, "Atlassian opens Teamwork Graph and pushes Rovo into agentic
     execution at Team '26", 2026-05-06.
     https://siliconangle.com/2026/05/06/atlassian-opens-teamwork-graph-pushes-rovo-agentic-execution-team-26/
  6. Mike Cannon-Brookes, "Atlassian Team '26: Meet the AI-Native Organization", 2026-05-06.
     https://www.atlassian.com/blog/company-news/founder-update-team-26

### 3. Linear: Linear Agent, Triage Intelligence, and Intake

**Category:** (a). **One line:** an issue tracker that is building agents into PM operations:
triage, intake, drafting specs, and project updates.

- **Started with triage, then widened.**
  - *Triage Intelligence (2025-09-03)* suggests assignees, teams, projects, and labels. It flags
    duplicates and related issues and explains each suggestion [1]. An auto-apply option followed
    [2].
  - *Linear Agent (public beta, 2026-03-24)* handles PM workflows. It synthesizes workspace
    context, drafts specs and project updates, triages and organizes issues, and pulls themes from
    the backlog and customer feedback [3].
  - *Code Intelligence (2026-05-14)* adds code-aware tasks, including "designing technical
    specifications" [4].
  - *"Intake"* is marketed as "self-driving product operations." It turns Slack and Teams threads,
    Intercom and Zendesk tickets, and Gong calls into issues, then triages, de-duplicates, and
    routes them [5].
- **Deployment model.** Embedded in the system of record: the desktop app (Cmd/Ctrl+J), mobile,
  comments, Slack, and Microsoft Teams. Automations can fire when issues enter triage [3].
- **Context approach.**
  - The workspace itself is the context: roadmaps, projects, issues, customer requests, and
    activity threads. Code comes in through Code Intelligence [3][4].
  - Triage treats the existing backlog "as a data set," combining semantic search, ranking, and
    LLM reasoning. Teams can tune it with "Additional Guidance" written in plain language [1].
- **Traces and telemetry.** Hovering over a suggestion shows the model's reasoning and the
  alternatives [1]. I found no public detail on agent audit logs or governance [3].
- **Said vs. observed.** Vendor claims only.
- **Regulated-enterprise relevance: Med.** It's a clean example of putting agents where PM work
  already lives, starting with triage and intake. Governance detail is thin, and I didn't verify
  how widely Linear is used in regulated enterprises.
- **Confidence: High.** The sources are first-party changelogs.
- **Sources:**
  1. Yann-Edern Gillet and Matthijs Wolting, Linear, "How we built Triage Intelligence",
     2025-09-03. https://linear.app/now/how-we-built-triage-intelligence
  2. Linear changelog, "Auto-apply triage suggestions", 2025-09-19 (seen in search listing).
     https://linear.app/changelog/2025-09-19-auto-apply-triage-suggestions
  3. Linear changelog, "Introducing Linear Agent", 2026-03-24.
     https://linear.app/changelog/2026-03-24-introducing-linear-agent
  4. Linear changelog, "Code Intelligence", 2026-05-14 (seen in search snippet).
     https://linear.app/changelog/2026-05-14-code-intelligence
  5. Linear, "Linear Intake – Self-driving product operations" (undated product page).
     https://linear.app/intake

### 4. Citi: the Arc agent platform and agentic product development

**Category:** (a), (c). **One line:** a large global bank that launched an internal agent platform
"within our risk framework." It reportedly rebuilt product development so requirements, risk
review, and building happen at once, with agent help.

- **Started with.** Developers build agents for "specific, well-defined use cases." One example is
  preparing wealth-management client meetings: gathering portfolio data, analyzing market trends,
  and modeling scenarios [1]. Before Arc, more than 80% of the 180,000 colleagues with access
  already used Citi AI tools regularly [1][2].
- **Product-development claim (`unverified`).** This comes from one Forbes contributor article that
  I could read only through search snippets [5].
  - *The old process* was a relay of five stages, each two to six weeks long. Compliance, legal,
    and controls reviewed requirements one after another before engineering started.
  - *The new process* runs requirements, risk review, and development at the same time in a shared
    workspace, with four agents. One drafts specifications from market data and one produces
    design mockups; the others write code and flag risks.
  - *The bank claims* inception to launch is about 50–60% faster. The author notes these figures
    haven't been independently verified.
- **Deployment model.** An internal, firm-wide platform, which Citi calls "industrialized
  infrastructure," for building and running agents [1][2]. Citi says it "scales … from one user to
  hundreds of thousands" [4].
- **Context approach.** Not disclosed.
- **Governance and traces.** Citi says: "Every agent will be monitored, auditable and governed. We
  will know what agents are doing, how they are doing it and the value they deliver" [1]. It adds
  that "Controls are automated at the platform level" and "a human is always in the loop" [4].
- **Scale (says, via secondary source).** 40,000 developers use Arc for agentic coding, logging
  100,000+ agentic development hours a week. These are figures from the 2026-05-07 Investor Day,
  as reported [3].
- **Said vs. observed.** All bank claims. The only independent commentary I found notes that Citi
  sets its own validation criteria [5].
- **Regulated-enterprise relevance: High.** This is the closest public match to the target setting.
  If the parallel requirements, risk, and build model is real, it's a direct reference for
  automating PM moves under risk controls.
- **Confidence.** *Med* for Arc, which is first-party. *Low* for the product-development workflow,
  which rests on one contributor article I couldn't fetch.
- **Sources:**
  1. Anand Selvakesari and Tim Ryan, Citi, "Introducing AI Agents: the next phase of Citi's AI
     journey", 2026-04-30.
     https://www.citigroup.com/global/news/perspectives/2026/introducing-ai-agents-next-phase-citi-artificial-intelligence-journey
  2. Makenzie Holland, CIO Dive, "Citi launches Arc to scale AI agents across the business",
     2026-05-01. https://www.ciodive.com/news/citi-launches-arc-scale-ai-agents/819113/
  3. Dana Ellison, Forkast, "Citigroup's Arc Platform Is the Largest Measured Enterprise Agent
     Deployment Yet", 2026-08-28.
     https://forkast.news/citigroups-arc-platform-is-the-largest-measured-enterprise-agent-deployment-yet/
  4. Citi Perspectives, "A Competitive Differentiator" (David Griffiths interview), 2026-09-22.
     https://www.citigroup.com/global/news/perspectives/2026/competitive-differentiator-david-griffiths-building-worlds-most-ai-empowered-financial-institution
  5. Forbes (contributor), "At Citi, An AI Now Reviews Risk First. Washington Has No Guidance For
     That", 2026-09-24. Returned HTTP 403; content seen only in search snippets.
     https://www.forbes.com/sites/daraabasiita/2026/09/24/at-citi-an-ai-now-reviews-risk-first-washington-has-no-guidance-for-that/

### 5. Glean: Enterprise Graph, agent governance, and the Agent Development Lifecycle

**Category:** (b). **One line:** an enterprise search and assistant vendor that pitches its
permission-aware "Enterprise Graph" as the context layer for agents.

- **Started with.** Nothing PM-specific. It offers horizontal agents grounded in company context
  [1].
- **Deployment model.** A SaaS platform. Agents are managed centrally with sharing controls,
  permission checks, and guardrails [2]. An admin console acts as one control plane across Search,
  Assistant, Agents, Actions, and MCP servers. I read the docs only through search snippets [4].
- **Context approach.**
  - *Enterprise Graph* is "a secure, algorithmically built, continuously refreshed model" of
    people, teams, and projects. *Personal Graph* captures each employee's work habits, writing
    style, and memory [1].
  - *Permissions.* Glean copies each source system's ACLs when it crawls and checks them at query
    time [4]. "Agents check data permissions on every request" [2].
  - *Scope checks.* "Agent alignment models" check each action against the agent's intended scope
    [2].
  - How often "continuously refreshed" means isn't specified.
- **Traces and telemetry.**
  - The Agent Development Lifecycle (ADLC) runs in seven stages: Opportunity, Design, Performance,
    Context, Develop, Launch, and Monitor & Improve [3].
  - Debug and trace views show inputs, tool calls, and decisions [3].
  - An "Agent Insights" dashboard covers adoption, usage, feedback, and changes in behavior [3].
  - Admin audit logs can be exported to a SIEM, and write actions need human confirmation [4].
- **Said vs. observed.** Vendor claims.
- **Regulated-enterprise relevance: High.** Copying source permissions, keeping audit logs, and
  confirming writes all match regulated-enterprise needs. It's a candidate context layer to buy
  rather than build.
- **Confidence: High** for first-party claims. *Med* for the docs-level detail in [4].
- **Sources:**
  1. Arvind Jain (CEO), Glean, "Accelerating the journey to the superintelligent enterprise: New
     Enterprise Graph, Third-generation Assistant, and Agent superpowers", 2025-09-25.
     https://www.glean.com/blog/live-fall-25-main
  2. Glean, "Agent Governance" product page (undated). https://www.glean.com/product/agent-governance
  3. Arvind Jain, "Introducing the Agent Development Lifecycle (ADLC)", 2026-05-12.
     https://www.glean.com/blog/agent-dev-lifecycle-2026 (press release:
     https://www.businesswire.com/news/home/20260512379174/en/Glean-Introduces-the-Enterprise-Agent-Development-Lifecycle-Codifying-How-Enterprises-Build-Govern-and-Measure-AI-Agents)
  4. Glean docs, "About Glean Protect and Protect+" and "Core security principles" (undated; seen
     via search snippets). https://docs.glean.com/administration/protect/overview ;
     https://docs.glean.com/security/security-principles

### 6. Microsoft: Work IQ, Agent 365, and the "Frontier Firm"

**Category:** (b), (d). **One line:** the incumbent office suite. It turns Microsoft Graph data and
memory into a governed context layer (Work IQ), adds an agent control plane (Agent 365), and frames
it all with a "Frontier Firm" maturity model.

- **Started with.** M365 Copilot as an assistant. Internally, Microsoft cites prioritizing email,
  feeding meeting transcripts to its Researcher agent, and help with SharePoint content [4].
- **Deployment model.**
  - Embedded in M365 apps.
  - The Work IQ APIs (Chat, Context, Tools, Workspaces) serve custom and outside agents, including
    an MCP surface with "10 generic tools" [3].
  - Agent 365 is a control plane that spans Microsoft, open-source, and partner agents [2].
- **Context approach.**
  - Work IQ combines data (email, files, meetings, chats), memory (style, preferences, workflows),
    and inference [1].
  - It is "continuously processing" email, calendar, meetings, chats, files, people, collaboration
    patterns, and line-of-business systems. Context "stays within the Microsoft 365 tenant trust
    boundary" [3].
  - Inside Microsoft it inherits sensitivity labels, DLP, and permissions. One issue's "root cause
    was not Work IQ, but a missing sensitivity label," so the context layer exposes governance gaps
    [4].
- **Traces and telemetry.**
  - Agent 365 includes a registry with unique agent IDs and least-privilege policies [2].
  - It promises "unified observability … through telemetry, dashboards, and alerts," plus logging
    and e-discovery [2].
  - Agent actions are "auditable and discoverable," and admins get dashboards on AI credit use [3].
- **Delegation framing.** The Frontier Firm model has three phases [5]:
  1. AI as an assistant.
  2. Agents as "digital colleagues" working at human direction.
  3. Humans set direction for agents that run whole processes.

  It also introduces a "human-agent ratio" and the "agent boss," and rests on a survey of 31,000
  workers in 31 markets [5]. At Ignite, Microsoft described the goal as "human-led and
  agent-operated" [1].
- **Said vs. observed.** Vendor claims. The Work Trend Index is a vendor-run survey.
- **Regulated-enterprise relevance: High.** Most regulated enterprises already run M365, Entra, and
  Purview. A deployed PM agent will likely have to fit that governance layer: labels, DLP, and
  agent IDs.
- **Confidence: High.**
- **Sources:**
  1. Jared Spataro, "Microsoft Ignite 2025: Copilot and agents built to power the Frontier Firm",
     2025-11-18.
     https://www.microsoft.com/en-us/microsoft-365/blog/2025/11/18/microsoft-ignite-2025-copilot-and-agents-built-to-power-the-frontier-firm/
  2. Charles Lamanna, "Microsoft Agent 365: The control plane for AI agents", 2025-11-18 (the page
     now says it's generally available).
     https://www.microsoft.com/en-us/microsoft-365/blog/2025/11/18/microsoft-agent-365-the-control-plane-for-ai-agents/
  3. Charles Lamanna, "Announcing the new Work IQ APIs", 2026-06-02.
     https://www.microsoft.com/en-us/microsoft-365/blog/2026/06/02/announcing-the-new-work-iq-apis/
  4. David Hirning, Microsoft Inside Track, "Intelligence on tap: How Work IQ enables AI and agents
     at Microsoft", 2026-06-11.
     https://www.microsoft.com/insidetrack/blog/intelligence-on-tap-how-work-iq-enables-ai-and-agents-at-microsoft/
  5. Microsoft WorkLab, "2025: The Year the Frontier Firm Is Born" (Work Trend Index), 2025-04-23.
     https://www.microsoft.com/en-us/worklab/work-trend-index/2025-the-year-the-frontier-firm-is-born

### 7. OpenAI: Frontier

**Category:** (b). **One line:** OpenAI's enterprise platform, launched February 2026, for
onboarding "AI coworkers." It offers shared business context, agent identity and permissions, and
evaluation loops.

- **Started with.** Not disclosed in anything I could read.
- **Deployment model.** A hosted enterprise platform. It works with agents built by OpenAI, by
  enterprises themselves, and by third parties such as Google, Microsoft, and Anthropic [1].
- **Context approach.** "Shared business context" that connects siloed internal apps, ticketing
  tools, and data warehouses [1]. Analysts describe it as a "semantic layer" meant to give agents
  institutional knowledge [2].
- **Traces and telemetry.** Analysts describe "built-in evaluation loops and memory mechanisms"
  meant to make "agent quality observable and governable" [2].
- **Early users (reported).** State Farm, Intuit, Uber, Oracle, and Thermo Fisher [1].
- **Said vs. observed.** Futurum analysts note thin documentation at launch and no agent-specific
  security detail. They also question OpenAI's domain expertise compared with incumbents [2].
- **Regulated-enterprise relevance: Med.** It aims squarely at the "shared context plus onboarded
  agents" pattern and counts a regulated insurer among early users. Governance detail was thin at
  launch.
- **Confidence: Low–Med.** The first-party page and CNBC both returned 403, so this rests on search
  snippets and one analyst note.
- **Sources:**
  1. CNBC, "OpenAI launches new enterprise platform in bid to win more business customers",
     2026-02-05. Returned 403; read via search snippet.
     https://www.cnbc.com/2026/02/05/open-ai-frontier-enterprise-customers.html. Also OpenAI,
     "Introducing OpenAI Frontier", which also returned 403.
     https://openai.com/index/introducing-openai-frontier/
  2. Mitch Ashley et al., Futurum Group, "OpenAI Frontier: Close the Enterprise AI Opportunity
     Gap—or Widen It?", 2026-02-09.
     https://futurumgroup.com/insights/openai-frontier-close-the-enterprise-ai-opportunity-gap-or-widen-it/

### 8. GitHub: Spec Kit

**Category:** (c), plus (a) through a newer extension. **One line:** an open-source toolkit that
gives coding agents a spec-first process. Since July 2026 it also ships an idea-assessment process
for discovery and shaping.

- **Started with.** Feature development through specify, plan, tasks, and implement (September
  2025) [1]. It now offers three independent processes [2]:
  - *Spec-driven development:* write a "constitution" once per project, then run specify, plan,
    tasks, implement, and converge for each feature.
  - *Bug fixing.*
  - *Idea assessment.*
- **The PM-relevant part: idea assessment** [2][3].
  - It runs intake, research, define, shape, and decide, and ends in go, needs-clarification, or
    kill.
  - It works "even in a project with no source code."
  - A "go" can be handed to `/speckit-specify`. Artifacts live in `.specify/assessments/<slug>/`.
  - It was added in v0.13.0 (2026-07-17). First-party bundles arrived in v1.0.9 (2026-09-21).
- **Deployment model.** A local CLI plus templates and skills installed into the repo for the
  user's coding agent. Copilot, Claude Code, and Gemini CLI were named at launch [1][2].
- **Context approach.**
  - Artifacts are markdown files kept in the repo. A "constitution" sets project principles [1][2].
  - The plan phase carries compliance requirements, legacy integrations, and tech standards [1].
  - The launch post says "intent is the source of truth" [1].
  - "Bundles package a role-based setup" [2].
- **Traces and telemetry.** Nothing built in, beyond the artifacts in the repo.
- **Said vs. observed.** Böckeler of Thoughtworks found spec-kit's markdown "repetitive" and
  "tedious to review," and saw the agent sometimes ignore notes. She suspects that in practice it
  writes specs first and then drops them, rather than keeping them in sync with the code [4].
- **Adoption.** 139,111 GitHub stars. v1.0.0 shipped on 2026-08-21 and v1.0.12 on 2026-09-25 [3].
- **Regulated-enterprise relevance: Med.** Reviewable artifacts in the repo suit audit. The
  assessment flow is the clearest open-source version of the handoff from PM shaping to spec. But
  there's no governance or telemetry layer.
- **Confidence: High.**
- **Sources:**
  1. Den Delimarsky, GitHub Blog, "Spec-driven development with AI: Get started with a new open
     source toolkit", 2025-09-02.
     https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/
  2. github/spec-kit README (fetched 2026-09-27). https://github.com/github/spec-kit
  3. github/spec-kit releases and repo metadata (GitHub API, fetched 2026-09-27).
     https://github.com/github/spec-kit/releases
  4. Birgitta Böckeler, martinfowler.com, "Understanding Spec-Driven-Development: Kiro, spec-kit,
     and Tessl", 2025-10-15. https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html

### 9. AWS: Kiro and the AI-Driven Development Life Cycle (AI-DLC)

**Category:** (c), (a). **One line:** AWS offers Kiro, a spec-driven IDE, CLI, and autonomous
agent. It also publishes a method, AI-DLC, in which AI turns business intent into requirements and
units of work that the team validates.

- **Started with.**
  - *Kiro (preview 2025-07-14)* turns a prompt into requirements: user stories with acceptance
    criteria written in EARS. From those it produces a design, then tasks linked back to the
    requirements. It adds steering rules and hooks [1].
  - *AI-DLC (2025-07-31)* has three phases: Inception, Construction, and Operations [3].
    - In Inception, "Mob Elaboration" has AI turn business intent into requirements, stories, and
      units while the team validates the AI's questions and proposals.
    - Short "bolts" of hours or days replace sprints.
- **Deployment model.**
  - The Kiro IDE and CLI. Team plans run through IAM Identity Center. Custom agents come with
    pre-approved tool permissions [2].
  - The Kiro autonomous agent (re:Invent 2025) is a "shared resource that works alongside the
    entire team." It connects to repos, pipelines, Jira, GitHub, and Slack, and proposes PRs [5].
  - AI-DLC ships as open-source steering rules for Kiro and Amazon Q (awslabs/aidlc-workflows,
    2025-11-29; 4,862 stars when fetched) [4].
- **Context approach.**
  - Plans, requirements, and design artifacts are stored in the repo so work continues across
    sessions [3].
  - Steering files encode "security policies, architecture standards, approved dependency lists,
    regulatory guidelines such as the EU AI Act" [6].
  - The autonomous agent learns from PRs, reviews, tickets, and architectural decisions [5].
- **Traces and telemetry.**
  - The AI-DLC workflows log "every artifact, decision, and conversation" and "every human action
    and approval" [4].
  - The financial-services post claims "end-to-end traceability from business intent to production
    code" for audit and regulatory review [6].
  - At GA, Kiro added property-based tests derived from requirements, plus admin dashboards for
    subscriptions and cost [2].
- **Regulated case (vendor-reported).** A European financial institution went from one product
  owner and 12 developers shipping 15 features a sprint to one product owner and 3 developers
  shipping 35. PMs and business analysts take part in Mob Elaboration [6].
- **Said vs. observed.** Böckeler found Kiro spec-first and heavy for small changes: "like using a
  sledgehammer to crack a nut." A small bug became four user stories with 16 acceptance criteria
  [7].
- **Regulated-enterprise relevance: High.** It has guidance written for a regulated industry, human
  approval gates, and intent-to-code traceability. That maps directly onto "delivery through SDD
  needs well-defined specs."
- **Confidence: High** for what AWS says. Results claims are `unverified`.
- **Sources:**
  1. Nikhil Swaminathan and Deepak Singh, "Introducing Kiro", 2025-07-14.
     https://kiro.dev/blog/introducing-kiro/
  2. Nikhil Swaminathan and Dragos Ilinca, "Kiro is generally available", 2025-11-17.
     https://kiro.dev/blog/general-availability/
  3. Raja SP, AWS DevOps Blog, "AI-Driven Development Life Cycle: Reimagining Software
     Engineering", 2025-07-31. https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/
  4. Will Matos, Raj Jain, Siddhesh Jog, and Raja SP, AWS DevOps Blog, "Open-Sourcing Adaptive
     Workflows for AI-Driven Development Life Cycle (AI-DLC)", 2025-11-29.
     https://aws.amazon.com/blogs/devops/open-sourcing-adaptive-workflows-for-ai-driven-development-life-cycle-ai-dlc/
     ; repo: https://github.com/awslabs/aidlc-workflows
  5. About Amazon, "Amazon launches frontier AI agents that work autonomously like teammates"
     (re:Invent 2025; no exact date on the page).
     https://www.aboutamazon.com/news/aws/amazon-ai-frontier-agents-autonomous-kiro
  6. Silvia Prieto, Jean-Francois Landreau, and Richard Caven, AWS Industries Blog, "AI-Driven
     Development Lifecycle for Financial Services", 2026-05-26.
     https://aws.amazon.com/blogs/industries/ai-driven-development-lifecycle-for-financial-services/
  7. Böckeler, 2025-10-15 (same as §8 [4]).
     https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html

### 10. Tessl: from generating code from specs to managing agent skills

**Category:** (c), (b). **One line:** a startup that launched a spec framework and spec registry in
September 2025. By January 2026 it had repositioned as an "agent enablement platform" and package
manager for agent skills.

- **Started with.** A Spec Registry of 10,000+ usage specs for open-source libraries, meant to stop
  API hallucinations (open beta). Also the Tessl Framework (closed beta) [1].
- **Spec approach.** The spec is the source and code is generated from it:
  - `@generate` produces code from a spec.
  - `@describe` documents existing code.
  - Capabilities link to tests [1].
  - Generated code is marked "GENERATED FROM SPEC - DO NOT EDIT," according to an independent
    review [3].
- **2026 change of direction.** It now calls itself a "package manager for agent skills" [2]:
  - A registry of 2,000+ evaluated skills.
  - Review evals, plus task evals that compare an agent with and without the skill.
  - Versioning, with installs recorded in a `tessl.json` manifest.

  The homepage now reads "Agent Enablement Platform" [4].
- **Deployment model.** A CLI plus a registry. Per a search snippet, the Framework "plugs into
  existing agents via MCP" [1].
- **Context approach.** Context and skills are treated as versioned, evaluated packages with a
  lifecycle: build, evaluate, distribute, optimize [2].
- **Traces and telemetry.** It has evals. The launch post doesn't describe usage telemetry [2].
- **Said vs. observed.** Böckeler found Tessl the only tool of the three treating the spec as the
  source. She draws parallels to model-driven development, which suffered from "inflexibility and
  non-determinism" [3].
- **Regulated-enterprise relevance: Med.** Governing context as versioned, evaluated packages bears
  directly on "trustworthy context." Treating the spec as the source is still early.
- **Confidence: High** for the launches. Calling it a change of direction is my reading of [2] and
  [4].
- **Sources:**
  1. Simon Maple, Tessl, "Tessl launches spec-driven development tools for reliable AI coding
     agents", 2025-09-23. https://tessl.io/blog/tessl-launches-spec-driven-framework-and-registry
  2. Guy Podjarny, Tessl, "Announcing skills on Tessl: the package manager for agent skills",
     2026-01-29. https://tessl.io/blog/skills-are-software-and-they-need-a-lifecycle-introducing-skills-on-tessl
  3. Böckeler, 2025-10-15. https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html
  4. Tessl homepage title (search listing, 2026-09-27). https://tessl.io/

### 11. Stripe: Minions

**Category:** (c). **One line:** a payments company running unattended coding agents that go from a
Slack thread or ticket to a PR in one shot, with a human reviewing every PR.

- **Started with.** Well-scoped tasks [1]. They start from:
  - Slack threads.
  - Internal feature-flag, docs, and ticketing UIs.
  - Flaky-test tickets that CI creates automatically.
- **Deployment model.** Hosted, isolated "devboxes," the same kind engineers use, pre-warmed so one
  spins up in about 10 seconds. The core agent is a fork of Block's Goose, customized to mix agent
  loops with deterministic code [1]. InfoQ calls these mixtures "blueprints" [3].
- **Context approach.**
  - "Toolshed," a central internal MCP server, offers 400+ tools: docs, ticket details, build
    status, and Sourcegraph code search.
  - Rule files are shared with Cursor and Claude Code and applied by subdirectory.
  - Links in the task are fetched deterministically before the run [1].
- **Traces and telemetry.** A web UI shows "the decisions and actions the minion took" [1].
- **Human control.** An engineer must open the PR and ask another engineer to review it. Nothing
  merges automatically [1].
- **Scale (says).** 1,000+ merged PRs a week that are "completely minion-produced" [1]. InfoQ later
  reported 1,300+ (secondary) [3].
- **PM involvement.** None mentioned [1]. The handoff is a Slack thread or ticket, not a formal
  spec. That's a useful contrast with SDD.
- **Regulated-enterprise relevance: High.** The control model carries over: isolated environments,
  one central tool registry, and mandatory human review, all in a financial-infrastructure
  setting. It's weak on the PM side.
- **Confidence: High.**
- **Sources:**
  1. Alistair Gray, Stripe Dot Dev Blog, "Minions: Stripe's one-shot, end-to-end coding agents",
     2026-02-09. https://stripe.dev/blog/minions-stripes-one-shot-end-to-end-coding-agents
  2. Stripe Dot Dev Blog, "Minions … Part 2", around 2026-02-19 per the X announcement at
     https://x.com/stevekaliski/status/2024578928430764362 (not fetched).
     https://stripe.dev/blog/minions-stripes-one-shot-end-to-end-coding-agents-part-2
  3. InfoQ, "Stripe autonomous coding agents", March 2026 (seen via search snippet).
     https://infoq.com/news/2026/03/stripe-autonomous-coding-agents/

### 12. Zapier: the AI Fluency Rubric

**Category:** (d). **One line:** an automation company that made AI fluency a hiring bar (and a
performance expectation) using a published four-level rubric. It revised the rubric in March 2026.

- **Levels [1]:**
  - Unacceptable
  - Capable: "using AI on purpose"
  - Adoptive: AI is "a dependable part of how you work"
  - Transformative: "AI has fundamentally changed how you approach work"
- **V1 (May 2025).** Required of all new hires. CEO Wade Foster shared role-by-role examples [2][3].
- **V2 (2026-03-31).**
  - It assesses AI mindset, strategy, building, and, new in V2, accountability.
  - The minimum bar is now "AI embedded into their core work" and "repeatable systems, not one-off
    prompts."
  - It rates "slope," meaning trajectory, not just a snapshot.
  - It's used at four hiring touchpoints and in performance expectations. Managers must redesign
    team workflows [3][4].
- **PM reading (secondary).** A Transformative PM builds systems such as automated product
  workflows, parallel review agents, and "git-versioned institutional memory" [5].
- **Telemetry.** The rubric relies on judgment. I found no telemetry-based measurement [1][3].
- **Regulated-enterprise relevance: Med.** It's a ready vocabulary for levels of PM AI fluency. A
  harness would need to pair it with measures drawn from traces.
- **Confidence: High.**
- **Sources:**
  1. Zapier, "How to measure your AI fluency—and move to the next level" (undated).
     https://zapier.com/blog/ai-fluency/
  2. Wade Foster, X thread, "How do we measure AI fluency at Zapier? … role-by-role examples",
     2025-06-05. https://x.com/wadefoster/status/1930680089651425452
  3. Zapier, "Raising the AI fluency bar for every Zapier hire", 2026-03-31 (date per search listing
     and [4]). https://zapier.com/blog/raising-ai-fluency-bar-in-hiring/
  4. Wade Foster, X post announcing the new rubric ("Last May we open-sourced V1"), 2026-03-31.
     https://x.com/wadefoster/status/2038979630590509553
  5. Aakash Gupta, "How to Get a 'Transformative' AI Fluency Rating as a PM, with Wade Foster",
     2026-09-24. https://www.news.aakashg.com/p/zapier-ai-fluency-rubric-for-pms

### 13. Anthropic: the AI Fluency framework, the AI Fluency Index, and measuring agent autonomy

**Category:** (d). **One line:** a model developer that co-publishes a four-part framework for AI
fluency (the "4Ds"). It measures both fluency and how much autonomy people hand to agents by
analyzing real usage in a privacy-preserving way.

- **The framework.** Prof. Rick Dakan and Prof. Joseph Feller built the 4D AI Fluency Framework
  with Anthropic [1][2].
  - The four competencies are Delegation, Description, Discernment, and Diligence.
  - It defines fluency across three modes: automation, augmentation, and agency.
  - It's licensed CC BY-NC-SA.
- **Measuring fluency from traces.** The AI Fluency Index (2026-02-23) studied 9,830 multi-turn
  Claude.ai conversations from one week in January 2026 [3].
  - 11 of the framework's 24 behaviors can be observed in conversations. Binary classifiers
    detected them through privacy-preserving analysis.
  - 85.7% of conversations showed iteration.
  - When the output was a polished artifact, users were less likely to spot missing context
    (−5.2 percentage points) or check facts (−3.7pp).
- **Measuring delegation from traces.** "Measuring AI agent autonomy in practice" (2026-02-18)
  analyzed Claude Code and API traffic [4].
  - *Turn duration.* The 99.9th percentile grew from under 25 minutes to over 45 between October
    2025 and January 2026.
  - *Auto-approval.* New users let Claude run with no manual approval about 20% of the time.
    Experienced users did so over 40% of the time.
  - *Interruptions.* Experienced users interrupt more. On complex tasks, Claude asks for
    clarification more than twice as often as humans interrupt it.
  - *Safeguards.* 80% of tool calls come from agents with at least one safeguard, and about 73%
    appear to have a human in the loop.
  - *Irreversible actions:* 0.8%.
  - *Recommendations.* Anthropic recommends monitoring after deployment. It warns that requiring a
    human to approve every action will "create friction without necessarily producing safety
    benefits."
- **Anthropic's own staff.** More than half of Anthropic's engineers say they can fully delegate
  only 0–20% of their work. From February to August 2025, Claude Code's consecutive tool calls rose
  116% (9.8 to 21.2) while human turns fell 33% (6.2 to 4.1) [5].
- **Regulated-enterprise relevance: High.** These are the most concrete public methods for
  "persist traces to understand and influence fluency and delegation," and the metric ideas can be
  reused directly.
- **Confidence: High** for the first-party research. Caveat: the vendor is measuring use of its
  own product.
- **Sources:**
  1. AI Fluency Framework site (Dakan and Feller; undated, 2025 materials).
     https://aifluencyframework.org/
  2. Anthropic Academy, "AI Fluency: Framework & Foundations" course (undated).
     https://anthropic.skilljar.com/ai-fluency-framework-foundations
  3. Kristen Swanson, Drew Bent, Zoe Ludwig, Rick Dakan, and Joe Feller, "Anthropic Education
     Report: The AI Fluency Index", 2026-02-23. https://www.anthropic.com/research/AI-fluency-index
     (redirects to https://academy.claude.com/tutorials/the-ai-fluency-index)
  4. Anthropic, "Measuring AI agent autonomy in practice", 2026-02-18.
     https://www.anthropic.com/research/measuring-agent-autonomy
  5. Anthropic, "How AI is transforming work at Anthropic", 2025-12-02.
     https://www.anthropic.com/news/how-ai-is-transforming-work-at-anthropic

### 14. Feng, McDonald, and Zhang: "Levels of Autonomy for AI Agents"

**Category:** (d). **One line:** an academic framework that defines five levels of agent autonomy
by the role the user plays. It treats autonomy as a design choice, separate from capability.

- **Levels [1]:**
  - L1 operator: the user directs every action.
  - L2 collaborator: user and agent plan and act together.
  - L3 consultant: the agent leads and consults the user on expertise and preferences.
  - L4 approver: the agent involves the user only for approval in specified risk scenarios.
  - L5 observer: the user can only monitor.
- **Key ideas.** Autonomy is "a deliberate design choice," independent of capability and
  environment. The paper proposes "AI autonomy certificates" to govern agents in single- and
  multi-agent systems, and sketches early ways to evaluate an agent's autonomy level [1].
- **Regulated-enterprise relevance: Med.** It gives a governance vocabulary for "decreasing human
  steering," step by step. A certificate per PM move is an auditable idea. There's no deployment
  evidence yet.
- **Confidence: High.**
- **Sources:**
  1. K. J. Kevin Feng, David W. McDonald, and Amy X. Zhang, arXiv:2506.12469 (v1 2025-06-14, v2
     2025-07-28). https://arxiv.org/abs/2506.12469
  2. Knight First Amendment Institute web publication (undated on the fetched page).
     https://knightcolumbia.org/content/levels-of-autonomy-for-ai-agents-1

---

## Gaps

- **Glass's primary source is out of reach.** The X article returned HTTP 402. I found no Ramp
  engineering-blog post, talk, or docs about Glass. Nothing public covers:
  - the model or harness underneath
  - how work splits between local and hosted
  - the security and permission model, beyond per-employee scoping
  - telemetry and cost
  - how skills are reviewed in practice
  - how PMs use it

  I found no independent observation; the HN thread drew essentially no discussion.
- **No public case of a shared, persistent PM agent driving PM moves end to end in a regulated
  enterprise.** The closest are Citi (weakly sourced) and LinkedIn (a tech company).
- **Almost no outcome data on PM moves.** Beyond Atlassian's internal usage figures, Ramp's Inspect
  PR share, and LinkedIn's triage-time figure, I found no numbers on how agents shift PM time.
- **Citi.** I couldn't access the Forbes piece or find a Citi first-party description of the
  spec-drafting or risk agents. The Investor Day figures come only from secondary coverage.
- **LinkedIn's FSB agents.** No first-party write-up. The Lenny's transcript is paywalled, and the
  agent list comes from a third-party summary.
- **Atlassian.** The Medium and Community posts on internal PM agent use were blocked (403, or
  pages that need JavaScript).
- **OpenAI Frontier.** Both the first-party page and CNBC were blocked (403).
- **Measuring fluency and delegation.** Vendors (Atlassian, Glean, Microsoft Agent 365) offer
  dashboards for adoption, usage, and cost. Only Anthropic publishes methods for measuring fluency
  or delegation from traces. I found no one publishing delegation levels specific to PM work, and
  no Ramp or LinkedIn fluency rubric. Ramp's 2025 ops article describes tracking usage but not
  proficiency levels.
- **Microsoft's "human-agent ratio".** No public data on measuring it in practice.
- **Noted but not profiled** (candidates for a later pass):
  - *Productboard Spark*, an agent built specifically for PMs with "organizational memory." Public
    beta per the CEO's 2026-01-27 post
    (https://www.productboard.com/blog/introducing-spark-ai-product-management-agent/); unveiled
    2025-10-02
    (https://www.globenewswire.com/news-release/2025/10/02/3160656/0/en/Productboard-Unveils-Productboard-Spark-Specialized-AI-to-Supercharge-Product-Managers.html).
  - *Morgan Stanley's DevGen.AI*, which turns legacy code into plain-English specs and claims
    280,000 hours saved. Secondary only: Slashdot, citing the WSJ, 2025-06-04
    (https://developers.slashdot.org/story/25/06/04/1233253/morgan-stanley-says-its-ai-tool-processed-9-million-lines-of-legacy-code-this-year-and-saved-280000-developer-hours).
  - *Not checked:* Goldman Sachs and JPMorgan agent programs (I saw only secondary coverage),
    Shopify's 2025 AI memo, Notion custom agents, Amplitude agents, ChatPRD, and the BMAD method.
