---
source: agent, 2026-09-27 session (while filing Geoff's thesis note)
goal: 002
tags: [scaffold-friction]
---

# The scaffold has no place for context that can't live in the repo

The scaffold assumes all project context can live in the repo. This repo is public (C5), and the
project's most useful priors and evidence are confidential: enterprise policies and controls, the
product operating model, and data on PM effort. `priors/` can't hold a prior that we can neither
store nor link. There's also no tier for "the agent should know this, but it can't be written
here."

**Workaround for now:** generic summaries in the repo, plus the agent's local memory outside the
repo, for anything Geoff shares that shouldn't be written here.

**Harness implication (H-001):** an enterprise context layer needs access tiers and
classification, not one flat store. This is the same problem at a larger scale (see principle 6 in
[context-layer](../../wiki/context-layer.md)).
