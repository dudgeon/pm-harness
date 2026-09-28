---
status: draft
updated: 2026-09-27
---

# Constraints

> These begin vague and get sharpened. Each has an ID so goals, wiki pages, and
> `open-questions.md` can refer to it.

| ID | Constraint | Firmness | Source |
|----|-----------|----------|--------|
| C1 | For now, the agent layer is Claude Code native (CLAUDE.md plus `.claude/skills/`). | soft, v0 choice | kickoff 2026-09-27 |
| C2 | Project state is plain markdown in git, readable and editable by humans and agents alike. | soft | kickoff 2026-09-27 |
| C3 | The agent never changes priors without human approval. | firm | kickoff 2026-09-27 |
| C4 | One repo = one project; a project may have many goals. | firm | kickoff 2026-09-27 |
| C5 | The repo is public. It describes the target environment only as "a large, complex, regulated enterprise," with no company, industry, or internal facts. | firm | DEC-006 |
| C6 | Adoption must be earned. The harness has to be clearly better than the status quo for the people using it; plan for no mandated rollout. | firm | DEC-008 |
| C7 | The harness operates under a large regulated enterprise's controls (data classification, access, audit, model risk, human accountability). Which controls apply specifically is still unknown (Q-014). | firm (specifics ?) | DEC-007 |
| C8 | Delivery is agentic, via spec-driven development. PM outputs that feed delivery must be specs SDD can consume. | soft, working assumption | DEC-010 |

Firmness values: **firm** (changing it needs explicit sign-off), **soft** (a current default),
**?** (unknown).
