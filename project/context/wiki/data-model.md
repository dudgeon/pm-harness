# The underlying data structure (working notes)

> Q-015, raised by Geoff on 2026-09-27: "There's a big question about the underlying data
> structure and how opinionated it should be. Should projects be recorded, shareable, canonical?
> How about goals?"
>
> **Nothing here is decided.** When asked to choose, Geoff said these questions "need research,
> analysis and deliberation," and not an uninformed decision. The proposals below are inputs to that
> research, not recommendations to adopt.

## Three separate properties

- **Recorded.** The entity persists beyond a session.
- **Shareable.** Other people and agents can find it and use it.
- **Canonical.** It's the authoritative version, not a copy or a view.

These line up with the [stops](path.md):
- **Casual chat:** nothing is recorded.
- **Each PM's own Claude Code:** things are recorded and maybe shareable, but not canonical.
- **A shared, deployed agent:** things can be canonical.

The three properties can also be set **per entity type**. They don't need a single answer.

## A per-entity starting point (agent proposal)

| Entity | Recorded | Shareable | Canonical | Why |
|---|---|---|---|---|
| Constraint (policy, architecture, regulation) | yes | yes | yes, owned by its domain | Re-discovering constraints is the waste H-004 targets, and they cut across projects |
| Decision and its rationale | yes | yes | yes, within its scope | Systems of record rarely hold rationale; it has audit value (H-012) |
| Spec | yes | yes | yes at handoff, versioned | It's the contract with delivery (Q-008) |
| Hypothesis, question, learning | yes | yes | no | They evolve, so provenance matters more than authority |
| Product | yes | yes | link to the system of record if one exists | Long-lived; it owns in-market support |
| Project / initiative | yes | yes: cross-project dependencies are invisible otherwise | link to the portfolio system of record; canonical only if none exists | |
| Goal | yes | yes, within the team | org goals: link to the OKR or portfolio tool; working goals: no | |
| Task | optional | within the team | no; the ticketing system is canonical | |

## Candidate principles (agent synthesis, to test)

1. **Be canonical only where nothing else is.** Link to the existing systems of record for
   portfolio, goals, and tickets rather than competing with them. Be canonical for what nobody holds
   well today: rationale, validated constraints, and hypotheses with their evidence. This also keeps
   the harness out of records governance (C7) until it's worth it.
2. **Share by default, within access tiers (C7).** Cross-project dependencies and constraints are
   invisible otherwise, and that visibility is how H-002 and H-004 are supposed to work.
3. **Keep an opinionated core and loose edges.** Have a small set of typed entities with IDs and
   links: the things the moves consume and produce (Q-004). Keep the content inside them free-form.
4. **Let the agent maintain the structure (H-013).** Users talk and the agent files. That's how an
   opinionated structure avoids taxing users (C6, H-011).

## Is "project" the right primary unit?

The scaffold is project-centric (C4: one repo = one project). Much PM work is product-centric,
though. Products persist and projects end, and in-market support belongs to a product, not a
project. Under a product operating model, the product would be the long-lived container, with goals
and initiatives inside it. This is still open.

## How opinionated?

- **Schemaless.** Free-form documents, with agents inferring the structure. Low friction, but weak
  aggregation.
- **Lightly opinionated.** Typed core entities with IDs and links, and free-form content inside
  them. This is the scaffold's approach.
- **Strongly opinionated.** A full schema, with required fields and workflow states, in the style
  of a portfolio tool. Strong aggregation, but high friction.

## The scaffold is a live experiment in this question

project-scaffold-v1 gives a lightly opinionated answer at the scale of one project:
- IDs, templates, and conventions
- a trust order
- an agent that maintains the structure

Goal 002's friction notes are evidence about where that structure helps and where it pinches
(H-001, H-013).
