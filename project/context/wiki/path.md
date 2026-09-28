# The path: stops, dimensions, and path dependence

> Working notes on the three path axes (Q-006, Q-001, Q-007).

## The stops Geoff named

These come from the [thesis note](../inbox/_processed/2026-09-27-thesis-and-direction.md):

1. PMs casually using a chat assistant (e.g., Gemini), or using no AI at all
2. PMs using standardized shaping skills in their own Claude Code instance
3. A shared, deployed agent
4. Further stops as steering decreases
5. A fully synthetic PM (a working assumption, DEC-009)

**Where the enterprise is today** (described generically, per C5): PMs have sanctioned access to a
chat assistant, Claude Code / Claude Enterprise, and an internal LLM platform (Geoff, 2026-09-27).
So stop 2 needs no new tooling. Some teams are also piloting SDD.

**An outside example.** Ramp reached about 99% individual AI-tool adoption, then found that "most
people were stuck" on setup, with no way to share what they learned. Its answer was a shared
internal harness, Glass, with shared skills and memory
([beacon scan](../inbox/_processed/2026-09-27-beacon-scan.md), §0). That's roughly a move from stop 2
to stop 3. It's weak evidence for H-002, since it's self-reported.

Primary sources (2026-09-27) sharpen this.
- **Glass is local and per-person**: a desktop app on the Claude Agent SDK, with connectors
  configured centrally and skills shared through Git. That makes it closer to the hybrid below than
  to stop 3.
- **Ramp's shared, deployed agents are separate services** on one formal record: Inspect, VOTC,
  Gadget.

Round 2 (2026-09-27) adds Ramp's own path for PM shaping:
1. **Stop 2 first.** In March 2026, PMs ran shaping skills in their own Claude Code. The skill
   passed from person to person as a file, and several PMs had their own.
2. **Then the hybrid.** By September, the CPO placed define in Glass, with skills distributed
   through Dojo kits.

The method survived the move. Skills run in Glass, Inspect, and Claude Code alike (H-009). Ramp
also now provisions Claude's own apps company-wide, so the host may move again
([intent-shaping](../../goals/004-beacon-teardowns/teardowns/ramp/intent-shaping.md)).

See the [Ramp teardown](../../goals/004-beacon-teardowns/teardowns/ramp/index.md) and Q-016.

## Three dimensions under the stops (agent synthesis)

Each stop bundles three things that can move independently. They match the three path axes Geoff
named:

| Dimension | From → to | Path axis |
|---|---|---|
| Delegation, per move | the human does it → an agent does it | which tasks to start with (Q-006) |
| Deployment topology | individual and local → shared and deployed | the v1 deployment model (Q-001) |
| Context | tacit, in SMEs' heads → governed, credible, agent-accessible | the context ecosystem (Q-007) |

A stop is a position on all three dimensions, and the path can differ from one move to another.

The dimensions constrain each other:
- **Context and trust limit delegation.** An agent can't drive a move without the context the move
  needs. Trust comes from a track record, and traces make that record visible (H-005).
- **Topology limits context.** Context only builds up in one place if something is shared.

For example: standardized skills in each PM's own Claude Code, writing to a shared, governed
context store, with traces sent to a central place. That setup is local on topology but shared on
context. It isn't one of the named stops, but it might be a good v1 (H-009).

## Delegation levels

A draft scale. This is an agent proposal, to be checked against external frameworks.

| Level | Who does the move | The human's role |
|---|---|---|
| L0 | the human, with no AI | does it |
| L1 | the human, with AI help on request | does it |
| L2 | AI drafts, the human edits | editor |
| L3 | AI does it, the human approves | approver |
| L4 | AI does it, the human spot-checks | monitor |
| L5 | AI does it | accountable, not involved |

External references to compare against, found by the
[beacon scan](../inbox/_processed/2026-09-27-beacon-scan.md) (§12–14):
- **Feng, McDonald, and Zhang, "Levels of Autonomy for AI Agents"**
  ([arXiv:2506.12469](https://arxiv.org/abs/2506.12469), 2025).
  - Defines five levels by the user's role: operator, collaborator, consultant, approver, observer.
  - Treats autonomy as a design choice, separate from capability.
  - Proposes "autonomy certificates." A certificate per move could suit an audited setting.
- **Anthropic, "Measuring AI agent autonomy in practice"**
  ([2026-02-18](https://www.anthropic.com/research/measuring-agent-autonomy)).
  - Measures delegation from traces: auto-approval (about 20% of the time for new users, over 40%
    for experienced ones), interruptions, and turn duration.
  - Warns that requiring approval for every action creates "friction without necessarily producing
    safety benefits." That matters for C7.
- **AI-fluency frameworks.** Anthropic's 4D framework, whose first D is Delegation, and Zapier's AI
  Fluency Rubric.
- **SAE's driving-automation levels**, as an analogy.

## What sticks on each axis (agent synthesis, H-009)

- **Tasks.** The first moves decide:
  - which context builds up first
  - who adopts early
  - the story people tell about whether to trust it

  Failures in high-stakes moves are hard to recover from, and wins in trivial moves won't earn
  distribution (C6).
- **Deployment.** Runtimes are fairly easy to swap. What sticks is where context gets written and
  whether traces are captured. The deployment model also decides the approval path: in a regulated
  enterprise, a local tool and a deployed service go through very different reviews (C7).
- **Context.** The schema, the provenance model, and the ownership model are all hard to change
  after the fact.

**What this implies:** v1 can stay modest on topology, as long as context goes to a shared,
governed store and traces are kept from day one.

## Open

Q-001, Q-006, Q-007, Q-011.
