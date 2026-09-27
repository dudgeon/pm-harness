---
name: new-goal
description: Scaffold a new project goal from a vague ask and interview the user to sharpen it. Use when the user wants to start, add, or define a goal.
---

# /new-goal

1. **Number it.** Use the next unused `NNN` in `project/goals/`. Numbers are never reused.
   Slug = 2–4 kebab-case words.
2. **Scaffold it.** Copy `project/goals/_template/` to `project/goals/NNN-slug/` and fill in the
   frontmatter (`status: draft`, today's dates).
3. **Read before asking.** Read `vision.md`, `constraints.md`, `deliverables.md`, `priors/index.md`,
   the wiki index, and the other goals' `goal.md` files.
4. **Interview.** Ask with AskUserQuestion, 2–4 questions per round, and offer concrete options
   drawn from what you just read. Cover:
   - why the goal matters and which project deliverable(s) it ladders to
   - the definition of done
   - requirements and goal-specific constraints
   - non-goals and overlap with existing goals
   - the assumptions it rests on. For each one, ask what it's based on, and record it as
     grounded (with a source) or as a hypothesis (`H-NNN` in `project/decisions.md`)
   Stop when the goal is actionable. Leave anything that is still fuzzy under **Open**. Don't
   force false precision.
5. **Check for conflicts.** Compare against the priors, the project constraints, and the other
   goals. Log conflicts in `project/open-questions.md`, and ask about any that block the goal.
   Record any choices made during the interview that constrain future work as `DEC-NNN` entries.
6. **Seed it.** Add initial deliverables (each with a `Ladders to`) and first tasks. If the goal
   implies a new project deliverable, propose adding it to `project/deliverables.md` and ask
   first.
7. **Finish.** Set `status: active` only if the user agrees the goal is sharp enough. Then run
   `/rollup`.
