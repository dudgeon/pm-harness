# PRD (reconstructed): Review Buddy, the AI code reviewer

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
| Step in Ramp's loop | **Build**. Review is the bottleneck that came after coding |
| What it is | "An Inspect-powered automated reviewer" (S20). It runs a **panel** of AI reviewers on every PR and loops in the right human |
| Bottleneck it removes | Human code review once agents write most of the code: "Engineers are just constantly combing through a ton of code" (S1 09:01) |
| Users | Everyone who opens a PR (human or Inspect); senior reviewers; teams that write their own review skills (S27) |
| Surfaces | GitHub bots (`ramp-reviewbuddy-2-of-2[bot]` on Ramp's GitHub, S1 slide; `inspect-by-ramp[bot]` on public repos, S21), and review sessions inside Inspect (S20) |
| Numbers (said) | Mar 2026: "a double-digit percentage of our PRs are automatically approved" (S17). Jun 2026, in beta: 8,836 PRs reviewed in a month (S22). Sep 2026: "93% of our PRs are now automatically handled" (S1 09:35) |
| Origin | "Built by a single engineer in a week" (S19). Since grown into a configurable, multi-reviewer system (S20) |
| Evidence | The talk, a slide, the public docs, and **public PR output that was observed** (S21). **High** confidence on how it works. **Low** on what "automatically handled" means |

## Problem and philosophy

Once Inspect was writing about 75% of PRs, "the speed has moved Ramp's bottleneck from writing code
to reviewing it" (S24). Ramp's answer is **review tiered by risk**:

- "time it takes to ship software is completely disconnected from time to produce the PR" (CTO,
  S25)
- Line-by-line review should be saved for "small diffs – in high risk areas of code
  (auth/identity/data access/network access/money movement)" (S25)
- "encode your review standards as rules the reviewer agent reads. auto-merge the low-risk stuff
  classified by your reviewer agent. reserve human eyes for billing, auth, the paths where a mistake
  is expensive." This is from the Head of Engineering, framed as general advice (S26)

## Requirements

### Functional

| ID | Requirement | Label | Source |
|---|---|---|---|
| R1 | Run a **panel**: "a general code reviewer run through Codex and separate reviewers for security, logic, API contracts, data integrity, and performance," plus an optional test-design reviewer | said | S20 |
| R2 | Add specialist reviews from **repo rules**: `.inspect/review/rules.yml`, where each rule has an id, a skill, file globs, a natural-language condition, and a model and reasoning effort | said | S20 |
| R3 | Load review skills from the catalog or `.claude/skills/<skill>/SKILL.md`. Teams write their own "so that they can codify the knowledge that they have built up over the years" | said | S20, S27 |
| R4 | Read "all the prompts that led you to build that code, so it can actually audit how you used AI in the first place." Inspect PRs link to their originating session, and the review runs on the same session id | said; observed | S1 09:01; S21 |
| R5 | Post a **summary** with context, issues, and a status, such as "🔴 Blocking findings remain — 1 Critical open" or "🟢 LGTM — no blocking findings, ready for human review" | observed | S21 |
| R6 | Post **inline findings** tagged critical, suggestion, or informational. Each is attributed ("Found by: Codex, Logic") and ends "I'll respond and resolve this comment once the issue is addressed" | observed; said (slide) | S21; S1 slide 09:12 |
| R7 | Discuss in the thread and propose fixes. Hand agreed fixes to Inspect ("resolves only the feedback you authorized") | said; observed | S1 slide; S20 |
| R8 | Re-review on new commits. On demand via `/reviewbuddy` or `/rb` | observed | S21 |
| R9 | **Route** to the right human reviewer, based on complexity and ownership | said | S1 09:01; S17; S19 (diagram) |
| R10 | Triage PRs into "automatically handled" (93%) and "needs a senior human" (7%) | said | S1 09:35 |
| R11 | An experimental opt-in for post-deploy monitoring | observed | S21 |

### Models

- The default is "`gpt-5.6-terra` with `high` effort." Through Ramp Router, the Codex reviewer can
  use any provider's model, and each rule can override the model (S20). **Said.**

### Human in the loop and controls

- **Before human review.** Findings come "before human review," and a clean pass reads "ready for
  human review" (S20, S21). **Observed.**
- **What "automatically handled" might mean** isn't defined anywhere public (S1). Three readings:
  1. **Auto-approved.** Consistent with "automatically approved" (S17, March).
  2. **Auto-merged for low-risk changes.** Consistent with S26's general advice.
  3. **No blocking findings**, then merged by the author after a glance. Consistent with the public
     output (S21) and the CTO's goal to "click the green button" (S23).
- **Control rationale for Inspect** (S7): PRs are opened under the human's identity so no one can
  approve their own change. This suggests Ramp does care about independent approval. Whether the
  bot's approval counts as that approval isn't public.

## Open questions

- Which of the three readings of "93% automatically handled" is right, and what's the denominator?
- Do the bot's approvals count toward branch protection?
- The false-positive rate, and the acceptance rate of its findings.
- The "2-of-2" bot name. A guess, not evidence: it could supply the second of two required
  approvals.

## Through our lens (goal 004, R3)

| Axis | Ramp's answer |
|---|---|
| First move | Not a PM move. It's the bottleneck that appears once delivery is agentic (DEC-010) |
| Deployment model | A shared bot, running as review sessions on Inspect's platform |
| Context approach | Review standards encoded as **rules and skills** that teams own and version in the repo, plus the **prompt trace** behind each change |
| Traces | It *consumes* traces: the originating session behind every PR |
| Controls | Tiered by risk. Severity gates. A human for the high-risk 7%. Approvals under the person's own identity |
| PM moves | Indirect. It makes acceptance cheaper, and it's the gate that Ramp's "next contract" code passes through |
| Delegation | **L4** for the 93% (if "handled" means approved without senior review). **L3** for the 7% |

## What transfers to a regulated enterprise (R4)

**Transfers:**
- **A panel of reviewers** with domain specialists (security, data integrity, API contracts), plus
  **team-owned review rules as code**. Control expectations become executable and versioned.
- **Review risk tiers named explicitly:** auth, identity, data access, network access, money
  movement. These map closely onto a regulated enterprise's high-risk change categories.
- **The prompt trace as review evidence.** Reviewing *how* a change was produced is strong control
  evidence (H-012).

**Needs adapting:**
- *Change management.* It usually requires a named, independent human approver. "Automatically
  handled" would become "AI review plus human attestation, tiered by risk." Any auto-merge class
  would need explicit approval from whoever owns change management (C7, Q-014).
- *Model risk.* It covers the reviewer models themselves.
