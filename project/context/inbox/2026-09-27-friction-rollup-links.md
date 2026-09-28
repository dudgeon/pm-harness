---
source: agent, 2026-09-27 session (while running /rollup)
goal: 002
tags: [scaffold-friction]
---

# `/rollup` copies tasks verbatim, which breaks their relative links

Goal tasks cite sources with links relative to their goal folder, e.g.
`src:[friction](context/friction.md)`. `/rollup` says to copy tasks into `project/tasks.md`
verbatim, and from there those links point at the wrong place. On 2026-09-27 the rollup rebased the
links instead, which changes the text but keeps the meaning.

**Options:**
- Allow link rebasing explicitly in the `/rollup` skill.
- Or use links relative to the project root in tasks.

Minor.
