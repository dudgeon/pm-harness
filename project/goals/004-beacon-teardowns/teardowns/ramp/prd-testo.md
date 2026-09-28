# PRD (reconstructed): Testo, the browser-based QA agent

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
| Step in Ramp's loop | **Build**, the testing bottleneck. For PMs, it's the **acceptance** move |
| What it is | "A browser-based QA agent" (S1 10:08) that "creates Playwright tests" (S19), built on Inspect (S19 diagram). Ramp pairs it with Review Buddy: "Our custom review agents, Review Buddy and Testo" (S22) |
| Bottleneck it removes | Manual QA that fell to PMs: spinning up QA environments, tweaking fixtures, clicking through screens (S1 09:35) |
| Users | PMs and engineers accepting a change; designers, through its design-system feedback |
| Surfaces | Natural-language instructions. Results come back as a table comparing the QA and Preview environments across vertical × role, with screenshots (S1 slide 10:18). It appears in Inspect's sidebar (S1 slide 08:38) |
| Numbers (said) | "Testo in the last 30 days has caught 425 bugs" (S1 10:40). "100 different combinations" per run (S1 10:08) |
| Where the idea came from | "Grandma testing": "agents basically with a goal right pay this bill… book this travel… use our deployed environment… automated QAing" (S18, Jul 2026) |
| Evidence | The talk, a slide, one first-party line of text, and a secondary report. **Med** confidence on scope, **Low** on mechanics |

## Problem and ambition

- **Problem.** Checking a change for every kind of customer was manual, and often the PM did it
  (S1 09:35).
- **The ambition** (S18, Jul 2026): "once we have that stack… there's no reason why you would
  necessarily need to do code reviews apart from… architectural review of code." Ramp sees
  agentic QA as the thing that eventually makes most line-by-line review unnecessary.

## Requirements

| ID | Requirement | Label | Source |
|---|---|---|---|
| T1 | Take a goal in natural language, e.g., "pay an invoice, but amortize it" | said | S1 10:08 |
| T2 | Spin up the product in many configurations ("100 different combinations") "based on the actual production data that we have access to" | said | S1 10:08 |
| T3 | Drive the deployed product in a browser "like a user" | said | S1 10:08; S18 |
| T4 | Report **blocking** feedback (bugs, issues, blockers) and **design and quality** feedback (confusing flows, breaks from the design system or design language) | said | S1 10:08 |
| T5 | Compare QA (current) with Preview (the change) for each configuration, with a screenshot of each | said (slide) | S1 slide 10:18 |
| T6 | Build the configuration matrix from **customer vertical × role × account settings** (e.g., accounting-firm and financial-institution admins and regular users) | said (slide) | S1 slide 10:18 |
| T7 | Give a plain-language verdict for each row ("Pass: Clients hidden; preview nests Reporting and Price intelligence under Insights") | said (slide) | S1 slide 10:18 |
| T8 | Create Playwright tests | said (reported) | S19 |
| T9 | Send findings back to be fixed | said | S1 10:40 |
| T10 | Log in as fixture users on deployed previews (the pattern Inspect already uses) | inferred | S26 |

## Related Ramp patterns (said; not called Testo)

- **Nightly QA on Ramp Sheets** (Ramp Labs). A QA agent that "surfaced several real production bugs
  every day" and opened fix PRs (S29).
- **Design QA agent** (Inspect docs). It "checks it against the design system at each breakpoint,
  then posts screenshots and a ranked list of problems" (S20). This is a generic example in the
  docs.
- **Data handling elsewhere** at Ramp: debugging uses a "sanitized read-only prod DB replica"
  (S19), and the integration factory uses "test credentials and synthetic values, not customer
  data" (S30).

## Open questions

- What "based on the actual production data" means: copies, sanitized replicas, or synthetic data
  shaped like production?
- The trigger: every PR, UI PRs only, or on request?
- Does it gate merges, or only advise?
- What counts as a "bug caught," and how many are false positives?

## Through our lens (goal 004, R3)

| Axis | Ramp's answer |
|---|---|
| First move | Acceptance testing, which PMs used to do by hand |
| Deployment model | A shared agent on Inspect's sandbox infrastructure |
| Context approach | Production-shaped data, the design system, the matrix of verticals and roles |
| Traces | Screenshots and a verdict per configuration, which amount to an acceptance record |
| Controls | Not public (data handling is the open question) |
| PM moves | **Acceptance (5)**, one of Geoff's judgment moves. Testo automates the checking, and the human keeps the judgment |
| Delegation | **L3**: the AI tests, and a human decides what to accept |

## What transfers to a regulated enterprise (R4)

**Transfers:**
- **Testing the matrix of roles and entitlements.** Driving every role and customer type through
  the browser is also access-control testing, which regulated firms need anyway.
- **Acceptance evidence.** Screenshots and verdicts per configuration can serve as
  change-management evidence (H-012).
- **Goal-based "grandma testing."** It's a direct way to accept SDD output against user journeys
  (C8, Q-008).

**Needs adapting:**
- *Test data.* It must be masked or synthetic under data classification (C7, Q-014). Ramp itself
  uses sanitized replicas and synthetic values elsewhere.

**Doesn't transfer as-is:**
- Seeding test environments straight from production data, if that's literally what Ramp does.
