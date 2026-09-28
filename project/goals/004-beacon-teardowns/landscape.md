# Beacon landscape, second pass (004-D1, 2026-09-28)

> Goal 004's second look across the whole field, at Geoff's request (2026-09-28): research the
> companies and tools that lead on agentic delivery and intent definition, then "flesh out the
> competitive research goal and prioritize where the next round of research should go." It follows
> the [first-pass scan](../../context/inbox/_processed/2026-09-27-beacon-scan.md) and the
> [Ramp teardown](teardowns/ramp/index.md).
>
> **Method.** Seven research passes ran in parallel on public sources:
> - outside takes on Ramp's Glass (added to the [Glass PRD](teardowns/ramp/prd-glass.md#outside-views-round-3))
> - PM-focused agents, and coding agents with intent-definition features
> - Stripe, Block, Coinbase, Shopify, and Atlassian
> - Meta, Uber, and Airbnb, plus a scan of other large tech and consumer companies
> - regulated organizations across several industries
> - Box, including its CEO's commentary
> - the public side of Lenny's newsletter, podcast, and Summit
>
> Each pass checked engineering blogs and the public posts of CEOs, CPOs, and CTOs (R8), labeled
> every claim, and scored each entity on one scorecard. Their notes, transcripts, and X harvests are
> kept locally in `context/inbox/_local/research-2026-09-28/`, not in this public repo.
>
> **Caveat.** Almost every number below is self-reported, and definitions vary. No outside party has
> verified any speed or quality figure.

## How to read the scorecard

Scores run from 0 to 3:
- **0:** nothing public.
- **1:** mentioned.
- **2:** described in some detail.
- **3:** detailed and first-party (docs, talks, screenshots, code).

The columns:
- **Intent:** how precisely a vague idea becomes a testable spec.
- **Delivery:** how mature the agentic delivery is.
- **Controls:** traces and controls.
- **Evidence:** how rich the primary material is.
- **Regulated:** how closely the setting resembles a large regulated enterprise. This is generic and
  cross-industry.
- **Teardown:** whether it's worth a deep teardown.

Labels in the sources: **1P** means the company or its employees; **vendor** means a supplier
writing about a customer; **2P** means an interview or article mediating first-party claims; **3P**
means independent.

## Five kinds of beacon

1. **Internal factories.** Companies building agentic delivery for themselves, such as Ramp, Uber,
   Coinbase, and Stripe.
2. **Regulated programs.** Organizations under heavy regulation, across industries, with public
   agentic-delivery programs.
3. **PM-facing agent products.** Vendors building agents for product work.
4. **Intent-definition tools and methods.** Coding agents and spec-driven methods that turn intent
   into specs.
5. **Commentators and hubs.** Not beacons themselves, but good sources of leads.

## The scorecard

### 1. Internal factories

| Beacon | Intent | Delivery | Controls | Evidence | Regulated | Teardown | What stands out | Key sources |
|---|---|---|---|---|---|---|---|---|
| **Ramp** | 2 | 3 | 2 | 3 | 2 | done | Our template. Shaping is a relay: VOTC, then Glass or Claude Code with a shaping skill, then Inspect, then Notion | [Ramp teardown](teardowns/ramp/index.md) |
| **Coinbase** | 3 | 3 | 3 | 3 | 3 | 3 | "The plan is the contract": a skill drafts a plan with acceptance criteria and the evidence the agent must return; simulator fleets verify it "against your spec"; when a check fails, the team fixes the plan, not the code. Every change gets a risk grade from A0 (copy) to A5 (its highest-risk code); humans test the top tier and review "councils" of agents handle the rest. From early 2026, PRs recorded the prompt, the rules, and the share of AI-written code, and that data was used "to eval prompt efficacy and defect rate." Model governance and internal audit sit inside its compliance agents | [Talk](https://www.youtube.com/watch?v=Ei-p3wnWMac) (2026-07-16, 1P); [Interviewing engineers](https://www.coinbase.com/blog/interviewing-engineers-in-the-ai-era-lessons-from-a-year-of-rebuilding) (2026-07-13, 1P); [PR lineage](https://x.com/chintanturakhia/status/2017269826499096894) (2026-01-30, 1P); [compliance agents](https://x.com/dorvonlevi/status/2054992565267554325) (2026-05-14, 1P) |
| **Uber** | 2 | 3 | 3 | 3 | 3 | 3 | The most complete first-party record from idea to maintenance. A **PRD Evaluator** used by "dozens of PMs" sets review depth by risk, separates "critical requirements" from "optimizations," and returns write-ready fixes. An idea-to-PR flow goes from Slack through research, requirements, and two Figma variants to a draft PR checked against the designs; Uber calls it a "sneak peek." **ADR**, open-sourced, captures prompt, reasoning, tool call, and outcome across agent clients, 50k+ sessions a day. Its lesson: at "50+ actions per session, human oversight becomes a rubber stamp." Tokens carry an actor-chain identity. "Agentic Pods" pair engineers with domain experts | [PRD Evaluator](https://www.uber.com/us/en/blog/first-pass-prd/) (2026-05-12, 1P); [agent identity](https://www.uber.com/us/en/blog/solving-the-agent-identity-crisis/) (2026-05-21, 1P); [ADR](https://x.com/praveenTweets/status/2083631934765449435) (2026-08-01, 1P) and [code](https://github.com/uber/ADR); [efficiency](https://www.uber.com/us/en/blog/efficient-software-factory/) (2026-08-27, 1P); AI Engineer World's Fair talk (2026-06-30, 1P) |
| **Stripe** | 2 | 3 | 2 | 3 | 3 | 3 | **Minions**: one-shot unattended agents, about 30% of PRs in one week (2P). Blueprints with deterministic steps, and Toolshed (~500 tools). **Kai with Agent Studio** is the closest analog to Glass, with domain-owned skills. **Harbor** handles prototypes. One team publishes a spec-first loop: the agent drafts a "Rule Contract" with valid and invalid examples, the team reviews it as an issue, then the agent builds | [Minions, part 1](https://stripe.dev/blog/minions-stripes-one-shot-end-to-end-coding-agents) (2026-02-09, 1P); [part 2](https://stripe.dev/blog/minions-stripes-one-shot-end-to-end-coding-agents-part-2) (2026-02-19, 1P); [Kai](https://stripe.dev/blog/meet-stripes-knowledge-ai-platform) (1P); [Harbor](https://stripe.dev/blog/harbor-stripes-ai-assisted-prototyping-tool) (2026-09-14, 1P); a16z interview (2026-08-17, 2P) |
| **Cloudflare** | 2 | 2 | 3 | 3 | 3 | 3 | **Standards as governed context.** Standards are written like RFCs, with MUST and SHOULD statements, named owners, stable IDs, and a lifecycle from approved to enforced. An AI reviewer enforces them on every merge request. A spec reviewer checks designs before build (~600 so far). Product, security, compliance, and trust-and-safety teams now add their own. **WriteGuard** adds per-tool risk tiers, agent sessions stamped into comments, and one audit log | [Codex](https://blog.cloudflare.com/engineering-standards-enforcement/) (2026-08-04, 1P); [WriteGuard](https://blog.cloudflare.com/mcp-portal-writeguard-private-beta) (2026-08-05, 1P) |
| **Shopify** | 2 | 3 | 3 | 3 | 2 | 2 | Context builds up from public agent sessions. River co-authors about 1 in 8 merged PRs. Its merge rate rose from 36% to 77% because people wrote down what it lacked, not because models changed. **Helix**: "the reference is the spec," with small checkpoints behind four gates. On security: "A workflow prompt isn't a control plane" | Tobi Lütke on X (2026-05-09, 1P); "Under the River" (2026-05-28, 1P); River security remediation (2026-09-02, 1P); Helix (2026-09-21, 1P) |
| **Block** | 2 | 2 | 3 | 3 | 2 | 2 | Identity and the decision record. **Buzz** gives each agent its own key and keeps a signed history in which "the reason survives." It also has a user-identity-delegation model. **Moneybot** turns each bug into an eval with an AI grader, which works as an executable acceptance test | Buzz (2026-07-21, 1P); identity delegation (2026-07-06, 1P); Moneybot (2026-08-28, 1P); Builderbot (2026-06-17, 1P) |
| **Meta** | 1 | 2 | 2 | 2 | 3 | 2 (narrow) | The **Organizational Second Brain**, in a compliance domain. Expert corrections become reviewed diffs to its knowledge files, and each one joins a regression suite. It's the closest public match to an agent that asks experts and remembers. The wider operating model is known mostly from leaks, and usage leaderboards were rolled back | [Second Brain](https://engineering.fb.com/2026/09/02/ml-applications/organizational-second-brain-ai-learns-from-experts/) (2026-09-02, 1P) |
| **Box** | 1 | 2 | 2 | 2 | 2 | 2 (light) | A documented internal AI operating model: "big bets" chosen from about 100 ideas, AI managers in each function, internal forward-deployed engineers, and 25-user pilots. The record is Box itself. Retrieval is gated by article metadata, and a weekly gap review feeds human-reviewed fixes. Box kept code review despite "a little bit of a discount on the productivity." For its own agents, it defines intent through evals rather than specs | [AI-first series](https://blog.box.com/ai-first-part-1) (2025-12-04 onward, 1P); [IT assistant loop](https://blog.box.com/building-closed-loop-knowledge-system-ai-powered-it-support-box) (2026-07-02, 1P); [Training Data podcast](https://www.youtube.com/watch?v=NE4CLThMPGU) (2026-09-15, 2P) |
| **LinkedIn** | 2 | 2 | 2 | 2 | 2 | 2 | Specs pass through critique agents for each craft (trust, growth, research, analyst). Maintenance and QA agents do "close to 50%" of builds. "Just reasoning over your entire knowledge base does not work," so it curates golden examples. The APM program became an Associate Product Builder program | Tomer Cohen (CPO) on Lenny's Podcast (2025-12-04, 1P interview; public video) |
| **Atlassian** (as its own user) | 3 | 2 | 2 | 3 | 3 | 2 | The most PM-centric framework. Start with prototypes, not PRDs, and define evals before the sprint (12,000 internal prototypes). Whether PMs commit code depends on the codebase's risk: yes in an isolated repo, no on its oldest, government-certified product. An **AI Fluency Index** rates six capabilities at five levels, "not a ladder." On measurement: "we haven't figured it out" | ["The future of product craft"](https://www.atlassian.com/blog/how-we-build/the-future-of-product-craft) (2026-05-29, 1P); Tamar Yehoshua at the Lenny & Friends Summit (2026-09-10, 1P talk) |
| **Spotify** | 1 | 3 | 2 | 3 | 1 | 2 | +76% PRs; 2.5M fleet PRs. The bottleneck moves "from coding to decision-making" | [Spotify engineering](https://engineering.atspotify.com/2026/6/code-with-claude-coding-is-no-longer-the-constraint) (2026-06, 1P) |
| **DoorDash** | 2 | 3 | 2 | 2 | 2 | 2 | YAML playbooks act as task contracts: tools, permissions, validation, and safety boundaries. 130k tasks a month | [InfoQ](https://www.infoq.com/news/2026/08/doordash-flux-cloud-agent/) (2026-08-31, 2P) |
| **Notion** | 2 | 2 | 1 | 2 | 1 | 2 | A `/brainstorm` skill interviews the maker before prototyping. Spec files in the repo are the source of truth, and the spec's history is the changelog. **Lore** is a shared memory of decisions and facts that expire | [Lore](https://www.notion.com/blog/building-shared-memory-for-ai-agents-in-notion) (2026-08-18, 1P); How I AI episode (2026-05-11, 2P) |
| **Anthropic** (product org) | 2 | 3 | 2 | 2 | 1 | watch | One-page PRDs for ambiguous work; a product definition is often "five evals." 30–40 PMs, nearly all former engineers or shipping code | Cat Wu on Lenny's Podcast (2026-04-23, 1P interview); more Summit talks not yet released |
| **Salesforce** | 1 | 2 | 1 | 2 | 2 | 2 | +79% PRs merged per developer. On PM and designer roles: "We don't have clear answers yet" | [Salesforce](https://www.salesforce.com/news/stories/how-engineering-became-agentic/) (2026-05-27, 1P) |
| **Amazon** (own practice) | 2 | 2 | 2 | 2 | 3 | 2 | The method (AI-DLC) and the tool (Kiro) are rich, but Amazon's own internal practice is known mostly from press | [Kiro Crew](https://kiro.dev/blog/introducing-kiro-crew/) (2026-09-18, 1P) |
| **Airbnb** | 1 | 2 | 1 | 2 | 1 | 1 | About 60% of code is AI-written (Q1 call). "Concept to launch up to 60% faster" (CTO). Little first-party detail for 2026 | CTO on X (2026-08-07, 1P); Insight Miner (2026-09-15, 1P) |
| Others scanned | 0–1 | 1–2 | 0–2 | 0–1 | 0–2 | 0–1 | Google, Microsoft and GitHub (internal), Vercel, Figma, Intuit, Netflix, Instacart, and Pinterest: executive figures at most, and little on intent | Detail kept in the local notes |

### 2. Regulated programs (across industries)

Coinbase (above) is the strongest regulated example.

| Beacon | Intent | Delivery | Controls | Evidence | Regulated | Teardown | What stands out | Key sources |
|---|---|---|---|---|---|---|---|---|
| **Singapore GovTech** (government) | 2 | 2 | 3 | 3 | 3 | 3 | Treats specs as the audited artifact: "Who wrote the specification? Who approved the agent's interpretation of it?" Autonomy is tiered by how critical the system is. A sandboxed review agent checks every merge request against code-classification policy. There's an agent registry | CTO's blog: [1](https://sausheong.com/from-vibe-coding-to-agentic-engineering-1ca3ca72b5ac), [2](https://sausheong.com/agentic-engineering-in-the-wild-ceabfb46a685) (2026-02-27 and 2026-03-20, 1P) |
| **Commonwealth Bank** (finance) | 2 | 2–3 | 2 | 2–3 | 3 | 2–3 | A five-level maturity model aimed at "AI generated product and engineering specs, code, and tests." **Project Coral** is a policy-constrained multi-agent delivery system; its main post is blocked for our tools | [Maturity model](https://medium.com/commbank-technology/the-evolution-of-ai-software-engineering-75a8a5a02c14) (2025-08-21, 1P); [Project Coral](https://medium.com/commbank-technology/project-coral-how-were-orchestrating-ai-agents-for-development-at-scale-e0e11b9f0e2a) (2026-05, 1P, blocked) |
| **Monzo** (finance) | 2 | 2 | 3 | 3 | 2 | 2–3 | A delivery agent runs in a sandbox behind one egress proxy, and a human merges. An operations agent is held to 100 expert-approved conversations, a "golden set" that works as its behaviour spec | [Agent Chip](https://monzo.com/blog/building-agent-chip) (2026-08-13, 1P); [Ops Agent](https://monzo.com/blog/engineering-the-future-of-customer-operations-the-monzo-ops-agent) (2026-06-04, 1P) |
| **Lloyds** (finance) | 0–1 | 1 | 3 | 2 | 3 | 2 | A governed agent lifecycle: a registry that records each agent's owner and the controls it passed, a non-human identity per agent, and a scanner that pulls stray agent code into governance | [Envoy](https://medium.com/ai-at-lloyds-banking-group/envoy-moving-ai-agents-from-concept-to-scaled-production-and-beyond-5ba18abecc54) (2026-07, 1P) |
| **UK government** (Home Office, Ministry of Justice, GDS) | 0 | 1–2 | 3 | 3 | 3 | 2 | Standards to borrow: AI-assisted commits and PRs must be marked and traceable; a named accountable person; human approval before production | [Home Office standard](https://engineering.homeoffice.gov.uk/standards/use-ai) (2026-03-20, 1P); [MoJ framework](https://mojdigital.blog.gov.uk/2025/12/17/introducing-the-ministry-of-justice-engineering-ai-governance-framework/) (2025-12-17, 1P) |
| **Citi** (finance) | 1 | 2 | 2 | 2 | 3 | verify | The widely repeated "100,000 hours a week" is attributed in the investor-day transcript to AI-assisted code review, not agentic development. A claim that risk and control review now runs alongside requirements drafting has only one source, and we couldn't read it | Investor Day transcript (2026-05-07, 1P); Forbes (2026-09-24, 3P, unread) |
| JPMorgan, BNY (finance) | 1 | 1–2 | 2 | 2 | 3 | 1 | Useful quotes on agent permissions set by domain, and on agents as "digital employees" with their own identity and a human manager. No process detail | Fortune (2026-04-29, 2P); bny.com (2025-10-20, 1P) |
| Insurance, health and life sciences, telecom, energy | 0 | 0–1 | 0 | 0–1 | 3 | 0 | No first-party accounts of agentic delivery found. Nothing public on validating agent-written code for regulated medical or manufacturing software | Detail kept in the local notes |
| RBC (via Factory) | 0 | 1 | 1 | 1 | 3 | lead | Named by a vendor as a customer of its agentic development platform. Needs the bank's own sources | Factory announcement (2026-09-15, vendor) |

### 3. PM-facing agent products

| Product | Intent | Delivery | Controls | Evidence | Regulated | Teardown | What stands out | Key sources |
|---|---|---|---|---|---|---|---|---|
| **Productboard Spark** | 2 | 2 | 2 | 2 | 2 | 3 | Specs linked to customer evidence, codebase analysis, and a governed two-way channel to coding agents over MCP: agents read, edit, comment on, and set the status of specs; every write is versioned; admins gate which roles can connect | [GA post](https://www.productboard.com/blog/introducing-spark-agentic-product-system/) (2026-06-22, 1P); [beta post](https://www.productboard.com/blog/introducing-spark-ai-product-management-agent/) (2026-01-27, 1P) |
| **Linear** | 2 | 3 | 2 | 3 | 2 | 2 | Intent, issues, agents, and review all happen inside the system of record. Its CEO says 77% of enterprise customers have installed a coding agent (2026-03-25) | Changelog (2026-09-24, 1P); CEO on X (2026, 1P) |
| **Atlassian** (Rovo, Jira Product Discovery, Rovo Dev) | 2 | 2 | 3 | 2 | 3 | 2 | PRD agents, specs kept in Jira work items, and reviews "based on specs." Teamwork Graph keeps source permissions. Jira Planner claims to "turn intent into agent-ready specs" | ["Rovo Dev in Jira as my spec-driven executor"](https://www.atlassian.com/blog/development/rovo-dev-in-jira-as-my-spec-driven-executor) (2026-05, 1P) |
| **Anthropic's PM plugin** | 2 | host | 3 | 3 | 3 | 2 | A write-spec skill with P0–P2 requirements, Given/When/Then acceptance criteria, and open questions tagged by who should answer them (engineering, design, legal, data). The questions aren't routed to anyone | Knowledge-work plugins (2026-01-30, 1P) |
| **ChatPRD** | 2 | 1 | 1 | 2 | 1 | 2 | Frank about reconciling evidence, specs, and what shipped. Its founder found that naive clustering "fragmented real product evidence badly" | Founder on X (2026-06-24, 1P) |
| Feedback and research agents (Dovetail, Enterpret, BuildBetter, Amplitude, Mixpanel, Pendo) | 1 | — | 1–2 | 2 | 1 | 1 | They ground PM agents in feedback data and show sources. None keys telemetry on requirement IDs | Detail kept in the local notes |
| Glass-like coworkers (Kay, Indent, HQ) | 0–1 | 1–2 | 2 | 2 | 1–2 | 2 | Kay, from Glass's creator, requires a person's approval before any skill or plugin loads. Indent is hosted, with sessions visible to the whole org. HQ is a file-based company memory | [Glass PRD, outside views](teardowns/ramp/prd-glass.md#outside-views-round-3) |

### 4. Intent-definition tools and methods

| Tool or method | Intent | Delivery | Controls | Evidence | Regulated | Teardown | What stands out | Key sources |
|---|---|---|---|---|---|---|---|---|
| **AWS AI-DLC 2.x** (method and open-source engine) | 3 | 2 | 3 | 3 | 3 | 3 | Runs inside Claude Code and six other agents. Question files include a "Not yet defined" option. Every claim carries a source tag ("Acceptance does not turn an assumption into fact"). A stakeholder map records who decides. It has a compliance agent. Requirement IDs are "permanent traceability keys." A 105-event audit trail. A learnings ritual that checks lessons against org rules before saving them | [aidlc-workflows](https://github.com/awslabs/aidlc-workflows) (v2.10.0, 2026-09-24, 1P) |
| **AWS Kiro** (spec mode) | 3 | 3 | 3 | 3 | 3 | 3 | EARS requirements are converted to formal logic and checked for ambiguity, conflicts, and gaps by a solver, which asks two-option questions. Answers rewrite the requirements. Property-based tests link back to requirements: the only shipping requirement-to-test trace we found | [Requirements analysis](https://kiro.dev/docs/specs/analyze-requirements/) (1P); [correctness](https://kiro.dev/docs/specs/correctness/) (1P) |
| **GitHub Spec Kit** | 3 | 2 | 1 | 3 | 2 | 3 | The de facto open pattern. `/clarify` asks up to five questions and logs dated answers in the spec. `/converge` checks the code against requirement IDs. An idea assessment ends in go, needs-clarification, or kill, and closely mirrors Ramp's shaping skill | [spec-kit](https://github.com/github/spec-kit) (v1.0.12, 2026-09-25, 1P) |
| **BMAD v6** | 3 | 2 | 2 | 3 | 2 | 2 | A typed, append-only decision log. Open items that don't block are deferred with an owner and a revisit condition. Release gates: PASS, CONCERNS, FAIL, WAIVED | [BMAD-METHOD](https://github.com/bmad-code-org/BMAD-METHOD) (v6.12.0, 2026-09-04, 1P) |
| **OpenAI Codex** (plan mode) | 2 | 3 | 2 | 3 | 2 | 2 | A plan must be "decision complete," including tests and acceptance criteria. Unanswered questions become recorded assumptions | Codex open-source plan template (2026, 1P) |
| **Claude Code** (plan mode) | 2 | 3 | 3 | 3 | 3 | 2 | Plan mode and structured clarifying questions. It also hosts AI-DLC, Spec Kit, and BMAD | Claude Code docs (2026-09, 1P) |
| **Cursor** | 2 | 3 | 1 | 2 | 1 | 1 | Plan mode. A planner agent plus a held-out test suite as the contract for agent work | [Plan mode](https://cursor.com/blog/plan-mode) (1P) |
| **Devin** | 2 | 3 | 2 | 2 | 2 | 2 | Session Insights flags "scope ambiguity" in past sessions and returns improved prompts: traces improving intent | Devin docs (2026, 1P) |
| Factory, Augment Intent, CodeRabbit Issue Planner, OpenSpec | 2 | 1–3 | 1–2 | 2–3 | 1–2 | 1–2 | Autonomy caps set at approval (Factory), living specs checked by a verifier (Augment), planning in the issue with preserved versions (CodeRabbit), and a planning repo that agents read (OpenSpec) | Detail kept in the local notes |

### 5. Commentators and hubs

- **Box's CEO** posts several times a day. His anonymized field reports are the best public pulse on
  how regulated enterprises adopt agents: agent identity, token budgets per team, embedded engineers,
  few firms with workflow evals. **Track his posts monthly for leads.**
- **Lenny's ecosystem.**
  - Public: the Summit talks, How I AI, and the latest 50 podcast transcripts.
  - Paid: the newsletter archive and the Community Wisdom digests of the members-only Slack. That
    Slack is the only window on practitioners rather than executives.
  - The official transcript dataset is licensed for personal, non-commercial use, so check terms
    before relying on it (see goal 004's tasks).
- **Analysts** worth reading on Glass-like layers: ForgeVista ("must own, needn't build") and
  Fintech Brainfood. See the [Glass PRD](teardowns/ramp/prd-glass.md#outside-views-round-3).

## What the landscape says

1. **Intent is the new bottleneck, by the leaders' own account.** Coinbase: the next bottleneck is
   "the what and the why." Atlassian: "the cost of building the wrong thing is about to
   skyrocket." Spotify: the bottleneck moves "from coding to decision-making."
2. **The intent-definition pattern has converged across tools:**
   - a read-only plan step before build
   - clarifying questions asked one at a time, as multiple choice with a recommended answer, after
     the agent has explored first
   - answers logged, with dates, in the spec itself; unanswered questions recorded as assumptions
   - stable requirement IDs used as trace keys
   - machine-checkable acceptance criteria (EARS, or Given/When/Then)
   - verification against the spec, not just the tests

   Ramp's shaping skill, which stops at "specific enough to prototype" with no acceptance criteria,
   is now the outlier.
3. **Two schools on how precise to be before build.**
   - Settle first, then dispatch: Stripe settles intent in a human thread; Coinbase writes a
     contract.
   - Small checkpoints instead of big documents: Shopify's Helix and Atlassian's prototypes and
     evals.

   Either way, the precise part is the **test** (acceptance examples, simulator checks, evals), not
   the prose.
4. **Intent quality is checked at the document, not at the handoff.** Uber's PRD Evaluator,
   Cloudflare's spec reviewer, and Meta's Second Brain all review written intent. None is publicly
   wired to the build agents. Feature intent still reaches the build as a prototype or a Figma file.
5. **Evals are becoming the spec for AI features:**
   - Box's product agents
   - Block's Moneybot
   - Atlassian's "define 'good' before the sprint"
   - Anthropic's "five evals"
   - golden sets at Monzo and Coinbase
6. **The PM role is being reshaped, not removed:**
   - Coinbase's "one person teams"
   - Uber's Agentic Pods, with engineers doing discovery alongside domain experts
   - Atlassian tying PM code access to the codebase's risk
   - LinkedIn's Associate Product Builders
   - Box's CEO expects PMs to survive as customer-facing specialists
   - Salesforce admits it doesn't know yet
7. **Controls are converging:**
   - review tiered by risk
   - humans keep the irreversible step (merge, deploy)
   - agent work runs apart from production data
   - agents get their own identity, delegated by a named human
   - guarantees are enforced in code, not prompts
   - reviews by several agents on different models
   - each request traces through the session to the PR and the decision
   - skills have owners and are measured
   - AI-assisted changes are marked

   Regulated organizations add autonomy tiered by how critical a system is, and agent registries.
8. **Traces are starting to improve quality:**
   - Uber's finding on approval fatigue
   - Coinbase's PR lineage feeding evaluations of prompts
   - Devin's Session Insights
   - Meta's expert corrections becoming knowledge diffs
   - Ramp's trace-based evaluation of its research harness
9. **Mandates backfire.**
   - Meta and Amazon rolled back usage leaderboards (press reports).
   - Uber found that sharing wins beat directives.
   - Box uses its per-person token list to find practices worth teaching, not to rank people.

   This supports C6.
10. **The vendor floor rose fast.** Since 2026-09-16, Claude offers most of Glass's shell as a
    vendor product: cloud runs, org plugin marketplaces, OpenTelemetry, and a Compliance API.
    Glass's creator is building a model-agnostic successor. What stays valuable is the context, not
    the shell (H-009).

## Gaps nobody fills yet (where the harness could stand out)

1. **Asking named experts, and remembering the answer along with who gave it.** Every clarify step
   asks whoever is at the keyboard.
   - Anthropic's PM plugin tags questions by who should answer, but doesn't route them.
   - AI-DLC records who decides, but still asks the session user.
   - Meta's Second Brain, in a compliance domain, is the closest.
2. **Legal and compliance requirements from the control owners, into specs and tests.** Across
   about 25 regulated organizations, nobody publicly shows this.
   - Cloudflare's standards and AI-DLC's compliance agent are partial answers.
   - Regulated firms handle risk through review tiers, not the spec.
3. **Tracing requirements through tests into production.** Kiro's trace stops at the repo.
   Measurable success criteria are never checked after launch.
4. **Keeping evidence and the spec linked.** Productboard and Ramp link them when the spec is
   written. Nobody revalidates a requirement when new evidence contradicts it.
5. **Intent shaped by several people over time, with decision rights.** Clarify steps are
   one-person chats, and approvals are clicks by whoever runs the session. Nobody models who may
   approve which kind of requirement.
6. **Independent evaluation.** Every intent feature's claims are measured by its own vendor.

These gaps are recorded as H-014.

## Where the next round should go

**How we ranked:**
- Does it fill one of the gaps above, or inform the spec contract (Q-008)?
- How relevant is it to a regulated enterprise (generic)?
- How rich and recent is the primary material?
- What does it add beyond Ramp?

### Tier 1: full teardowns (a vision plus PRDs), in this order

1. **Coinbase.** The most complete chain from intent to verification, in a regulated setting, with
   dense recent material. Candidate PRDs:
   - Forge
   - Sail and its risk tiers
   - Tracer Bullet, with the plan-drafting skill and agent verification
   - Mux
   - design-system tooling for agents
   - the enterprise agent platform, with its compliance agents under model governance
2. **Uber.** It covers every PM move, including a PM-facing spec reviewer and the best public data on
   traces and approval fatigue. Candidate PRDs:
   - the research-to-PR flow
   - the PRD Evaluator
   - Minion
   - code review and the code inbox
   - the skills marketplace and context graph
   - maintenance loops
   - ADR and agent identity
   - Agentic Pods
3. **AWS AI-DLC 2.x with Kiro.** The fullest open design for grounded, auditable intent, and the
   only requirement-to-test trace. It runs inside Claude Code, so we can read the code and trial it
   directly.

### Tier 2: focused teardowns (a few PRDs, or a controls note)

4. **Cloudflare.** Standards as governed, owner-maintained context, enforced before and after build.
5. **Stripe.** Minions and blueprints, and Kai with Agent Studio as the Glass comparison. Also its
   one team's spec-first loop.
6. **Singapore GovTech.** Specs as the audited artifact, and autonomy tiered by criticality.
7. **Productboard Spark.** The spec lives in the PM record and talks to coding agents over a
   governed channel.
8. **Meta, narrowly.** The Organizational Second Brain, with its risk-scoring and privacy controls as
   support.
9. **GitHub Spec Kit.** A hands-on trial in goal 001 rather than a paper teardown.

### Tier 3: one-page profiles

- Shopify (context from public sessions; Helix gates)
- Block (agent identity and the decision record)
- Atlassian (the PM craft framework; PM code access tied to codebase risk; the Fluency Index)
- LinkedIn (per-craft critique agents)
- Monzo (behaviour specs from golden sets; the delivery sandbox)
- Lloyds (agent registry and non-human identity)
- UK government standards (marking AI-assisted changes; named accountability)
- Box (the operating model and its context loop)
- BMAD v6 (the decision log)
- Linear
- Notion (Lore; repo specs)
- Commonwealth Bank, if the Project Coral post can be captured
- DoorDash (task contracts)
- Spotify

### Watch list

- **Verify only:** Citi's claims.
- **Leads:**
  - JPMorgan and BNY
  - RBC, via Factory
  - Airbnb
  - Salesforce
  - Amazon's own practice
  - Anthropic's and OpenAI's product orgs (their Summit talks are still unreleased)
  - ChatPRD
  - Vercel (claims generated apps replaced its internal SaaS, including PM tools)
  - Cursor's planner and test-suite contract
- **Monthly:** Box's CEO, the Summit playlist, the Kiro, AI-DLC, and Spec Kit changelogs, and talks
  by Glass's creator.

### What changed from the first pass

- **AWS** stays in the top tier, now as AI-DLC 2.x with Kiro.
- **Coinbase** and **Uber** join the top tier.
- **LinkedIn** and **Atlassian** drop from full teardowns to profiles. LinkedIn's record is
  interview-only. Atlassian's internal record reads as vendor material, though its PM framework
  feeds goal 003.
- **Citi** drops to verify-only. Its headline figure didn't hold up, and its product-development
  claim has only one source.

## What would unblock the next round

- **Manual captures.** These pages are blocked for our tools (bot checks). Geoff could save them
  from a normal browser:
  - Coinbase's posts on its support teammate, Figma-to-code, "AI across the stack," and its
    developer tools
  - Commonwealth Bank's Project Coral post
  - the Forbes piece on Citi's agents
  - DoorDash's Flux post
  - an Atlassian product leader's post on Medium
- **Access to Lenny's paid archive and community Slack.** Check the terms first (see goal 004's
  tasks). What to read first once access arrives (titles are public):
  - **Community Wisdom** digests of the Slack. These are the only view of practitioners rather than
    executives:
    - managing PRD versions as features evolve (2026-02-21)
    - "Building without clear PM requirements" (2026-08-29)
    - "Driving AI adoption when habits are the bottleneck" (2026-09-05)
    - speeding up discovery in a big org (2026-09-26)
    - "Sharing Claude Code skills across the org" (2026-04-18)
    - "AI agents and data integrity" (2026-06-06)
  - **Slack searches:** Ramp or Glass, PM agent, harness, specs for agents, acceptance criteria,
    regulated settings, AI fluency, token leaderboards, Rovo, full-stack builder.
  - **Paid posts:**
    - "How top PMs increase their leverage with AI" (2026-06-30)
    - "How tech workers are feeling in 2026" (2026-07-07)
    - "Not all AI agents are created equal" (2026-04-14)
    - "Advanced evals" (2026-09-22)
    - "25 proven tactics to accelerate AI adoption" (2025-08-05)
- **Recordings not yet public:**
  - Summit talks by Anthropic, OpenAI, Linear, and Stripe speakers
  - a Ramp engineer's dbt Summit talk on Glass
  - talks by Glass's creator
