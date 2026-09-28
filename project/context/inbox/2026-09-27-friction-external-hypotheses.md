---
source: agent, 2026-09-27 session (Ramp round 2)
goal: 002
tags: [scaffold-friction]
---

# No home for hypotheses about the outside world

Geoff offered a hypothesis about a beacon: "Glass is where the majority of intent shaping happens"
at Ramp. The scaffold's H-NNN register holds claims about *our* project, with tests we can run. This
claim was about someone else's product and could only be tested against public sources. So it
became a page in the teardown
([intent-shaping](../../goals/004-beacon-teardowns/teardowns/ramp/intent-shaping.md)) with a
verdict, and it isn't in `decisions.md`.

That worked, but nothing in the scaffold says where such claims go. Nor does it say how their
verdicts should feed the project's own hypotheses. This time the verdict fed H-002, H-009, and
Q-016 by hand.

**Options:**
- Keep them in the goal that tests them, and have `/lint` check that verdicts are linked from the H
  or Q they bear on.
- Or add an "external claims" section to `decisions.md`, with its own IDs.

Minor. It may recur with each beacon teardown.
