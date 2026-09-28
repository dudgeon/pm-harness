# Landscape scan: digest

> Digest of the [full scan](../../../context/inbox/_processed/2026-09-27-beacon-scan.md): 15
> beacons with sources, done 2026-09-27 by a background agent from public information. It's a first
> pass and unverified. The scan marks what companies *say* separately from what others have
> *observed*.
>
> **Update 2026-09-27.** For Ramp, this digest is superseded by the
> [Ramp teardown](../teardowns/ramp/index.md). The Glass article has been recovered, and several of
> the scan's claims about Ramp were corrected: Glass runs on the Claude Agent SDK; the Inspect
> post's date and quotes; the token-spend post; Ramp Research's status. The index's "Evidence and
> gaps" section lists the corrections.
>
> **Update 2026-09-28.** For prioritization, this digest is superseded by the
> [second-pass landscape](../landscape.md), which scores about 50 entities on one scorecard and
> ranks the next round in tiers.

## What Glass is

Glass is Ramp's **internal** AI suite, not a product. Ramp described it in an X article on
2026-04-09, and the CEO backed it on 2026-04-12. The article itself couldn't be fetched, so the
details below come from secondary summaries:

- one SSO sign-in that wires up every tool
- per-user memory, rebuilt every 24 hours from Slack, Notion, Linear, and Calendar
- 350+ markdown skills in "Dojo," versioned and reviewed like code
- "Sensei," which recommends skills
- scheduled automations

Ramp built it after individual AI adoption reached about 99% and "most people were stuck." Two
other internal agents sit alongside it:
- **Inspect**, a hosted coding agent that PMs also use. Ramp says it writes about 30% of merged
  PRs.
- **Ramp Research**, a data agent in Slack.

## Prioritized for deep teardowns

1. **Ramp** (Glass, Inspect, Research). Geoff's example, and the fullest public account of a
   company-wide shared harness.
2. **LinkedIn** (Full Stack Builder agents, CAPT). Agents for PM moves on top of a governed context
   layer: playbooks get InfoSec review, calls are logged, and learnings are written back. It
   reports 8,000+ daily users, PMs among them.
3. **Citi** (Arc). The regulated-bank case. Relevant as a heavily regulated example, but weakly sourced.
4. **AWS** (AI-DLC, Kiro). The most explicit method for getting from intent to spec to code, with
   logged human approvals and guidance for a regulated industry.
5. **Atlassian** (Rovo, Teamwork Graph). The context layer a regulated enterprise probably already
   has. It keeps source permissions and is open to outside agents through MCP.

## Patterns across beacons

- **Procedural context lives in versioned, reviewed files.** Ramp's Dojo, LinkedIn's CAPT, Tessl,
  AWS steering files, and Spec Kit's constitution all work this way.
- **SDD tooling is moving upstream into PM work.** In July 2026, Spec Kit added an
  idea-assessment process: intake, research, define, shape, decide. It ends in go,
  needs-clarification, or kill, and it runs without any code.
- **Most trace capture tracks only adoption and cost.** Anthropic is the one that publishes
  methods for measuring fluency and delegation from traces.

## Gaps

- The primary source for Glass (task @Geoff).
- No public case of a shared PM agent driving PM moves end to end in a regulated enterprise.
- Almost no outcome data on PM time.

## Where findings were filed

- Evidence on H-002, H-005, H-007, H-009, and H-011 (`decisions.md`).
- `from:004` tasks in goals 001, 003, 005, and 006.
- The context-layer patterns → [context-layer](../../../context/wiki/context-layer.md).
- The external delegation frameworks → [path](../../../context/wiki/path.md#delegation-levels).
- The outside breakdowns of shaping → [pm-moves](../../../context/wiki/pm-moves.md).
