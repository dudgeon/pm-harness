# pm-harness

R&D toward an AI product-manager harness, most likely a deployed agent or agent orchestrator.

The project is managed with **project-scaffold-v1** (see [CLAUDE.md](CLAUDE.md)). Start at
[project/vision.md](project/vision.md).

## project-scaffold-v1

project-scaffold-v1 is a markdown file structure plus Claude Code skills for running a project with an agent. It holds:

- a vision
- constraints
- priors
- a shared wiki of learnings
- goals, each with its own deliverables, tasks, and context
- decisions and hypotheses
- open questions

It is **not** the harness, and its aims are not goals of the harness project.

Design aims (these are aims for the scaffold itself):

1. **Drop-in.** You can open a fresh session, hand over a fact, a direction, or a question, and
   the agent works out where it fits and acts on it. The files carry the memory.
2. **Guidance, not a workflow engine.** CLAUDE.md sets principles and bounds, not step-by-step
   procedures. Skills are shortcuts, not required paths.
3. **One reconciliation loop.** Every new piece of information runs through the same loop: place
   it, label it, trace what it implies across goals, surface conflicts, sharpen. Ingest and lint
   run that loop at different scopes.
4. **Epistemic hygiene.** Priors are ranked above hypotheses. Contradictions get logged. Decisions
   record what they rest on.
5. **Initiative grows as the project gets clearer.** Early on, the agent helps find the project's
   shape. Later, the user steers and the agent drives. `/next` is the standing question.
