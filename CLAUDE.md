# pm-harness

This repo is **one project**: building and deploying an AI product-manager harness, which is likely
a deployed agent or agent orchestrator.

The project's state lives in `project/`, organized by **project-scaffold-v1**, a markdown
structure plus a few skills. The scaffold is not the harness (DEC-003). Its design aims are in
[README.md](README.md).

You'll usually arrive in a fresh session with no memory of earlier ones. Everything you need is in
the files. The user will often just hand you a fact, a direction, or a question. Work out where it
fits, act on it, and tell them what changed.

## Map

```
project/
  vision.md, constraints.md   Why, what winning looks like, what limits us
  deliverables.md             Project deliverables that goal deliverables ladder into
  decisions.md                Decisions (DEC-NNN) and hypotheses (H-NNN)
  open-questions.md           Contradictions and unresolved questions (Q-NNN)
  tasks.md                    Rollup of goal tasks (generated; don't hand-edit)
  priors/                     Context outside the project we must fit into (index.md)
  context/inbox/              Raw material not yet filed
  context/wiki/               Shared learnings across goals (index.md, log.md)
  goals/NNN-slug/             goal.md (status, requirements, assumptions), deliverables.md,
                              tasks.md, context/ (goal-specific learnings)
```

For a quick orientation, read the vision, `open-questions.md`, and the `goal.md` files of any goals
whose status isn't `done` or `dropped`. Read the rest as it becomes relevant.

## How to treat information

**Trust order.** Priors outrank vision, constraints, and goals, which outrank the wiki, which
outranks the inbox and fresh claims. At every level, **grounded** claims (with a source you can
cite) outrank **hypotheses**. Weaker evidence can overturn stronger sources, but only openly.

**Priors belong to other people.** Propose changes to anything in `priors/` and never make them
yourself. Say so when overriding a prior may need someone beyond the project PM.

**Vagueness is normal early on.** Don't demand precision up front. Sharpen things when the work
actually needs them to be sharper.

**Ask what a claim rests on.** When a claim is stated as fact without a basis, whether it comes
from the user, a doc, or you, ask what it rests on. Then record it as grounded, with a source, or
as a hypothesis (`H-NNN`, with a way to test it). Keep this light-touch: it's a habit, not a gate.

## Reconciling new information

This is the core loop. You run it whenever something new arrives: a fact the user types, a
direction, an inbox item, a finished deliverable, a finding inside a goal. `/ingest` and `/lint`
run the same loop at different scopes.

1. **Place it.** Decide what it is: a learning, a decision, a direction, a constraint, a
   requirement, or a task. Decide where it belongs: the project wiki, a goal's context, a goal
   definition, the constraints, or the decisions register. It can belong in more than one place.
   If the user gave it to you in chat and it's evidence rather than a direction, save it to the
   inbox as the source and cite it from wherever it gets filed.
2. **Label it.** Is it grounded or a hypothesis? Does it add evidence for or against an existing
   `H-NNN`?
3. **Trace the implications.** Which goals, deliverables, decisions, or assumptions does it
   touch? A finding in one goal often matters to others. For each goal it affects, add a task to
   that goal: `- [ ] Consider <finding> for <X> src:<link> from:<NNN>`. Skip any that duplicate an
   open task.
4. **Surface conflicts.** Log contradictions in `open-questions.md`, and raise them in your reply
   if they block anything. When a conflict is resolved, record a `DEC-NNN` and update the source
   that lost.
5. **Sharpen.** If it clarifies something vague, propose the sharper wording.
6. **Report.** In a few lines, say what you changed, the tasks you created and where, the
   questions you raised, and what's waiting on the user.

**Freely do** anything additive and easy to reverse: file into the wiki or a goal's context, add
tasks, log questions, add evidence, append to the log. **Ask first** before editing goal
definitions, constraints, the vision, or deliverables, or before recording a decision the user
didn't clearly make. **Never** edit priors. When the user gives a clear direction, that counts as
approval: act on it, and record it as a decision if it constrains future work.

## Initiative

How much initiative to take depends on how well-defined the project is.

- **When the project is vague** (goals still `draft`, constraints marked `?`, most things still
  hypotheses): lean on questions. Offer options and help the user find the shape of the project.
  Don't manufacture busywork.
- **When the project is well-defined** (goals `active`, with a clear definition of done and
  requirements): propose concrete next steps. Pursue the obvious ones within your "freely do"
  bounds. Save the user's attention for real choices.

The user can always dial this up or down. `/next` is the explicit way to ask "what now?"

## Conventions

- **IDs:** goals `NNN` (never reused), project deliverables `D1…`, goal deliverables `NNN-D1…`,
  constraints `C1…`, decisions `DEC-NNN`, hypotheses `H-NNN`, questions `Q-NNN`.
- **Goal status:** `draft` → `active` → `done` | `dropped` (and `paused` if needed).
- **Task tags:** `@owner`, `due:`, `→NNN-D1` (the deliverable it serves), `blocked:Q-NNN`, `src:`
  (what prompted it), `from:NNN` (created because of another goal's work).
- Tasks live in the goals; `project/tasks.md` is a generated view of them.
- Decisions are superseded by new ones, never edited away.
- Wiki claims cite their sources.

## Skills

- `/next`: suggest options for moving the project forward
- `/ingest`: reconcile new material (the inbox, or whatever was just provided)
- `/lint`: reconcile the whole project and check its health, going beyond the latest changes
- `/new-goal`: turn a vague ask into a goal, interviewing the user to sharpen it
- `/rollup`: regenerate `project/tasks.md` and check the deliverables ladder

## Scaffold friction

When project-scaffold-v1 itself gets in the way, drop an inbox note tagged `scaffold-friction`.
Examples: a missing place for something, a skill that misroutes, a rule that's too rigid. These notes
evolve the scaffold, and they may also inform the harness design (H-001).
