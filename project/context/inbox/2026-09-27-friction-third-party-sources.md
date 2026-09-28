---
source: agent, 2026-09-27 session (the Ramp teardown)
goal: 002
tags: [scaffold-friction]
---

# Full third-party sources have no home in a public repo

The Ramp teardown rests on material that can't be republished in full. There are:
- a conference talk's transcript and slide frames
- three recovered X articles
- caption transcripts of three interviews

The teardown still needs them to stay checkable, and to be there for future sessions.

**Workaround.** `project/context/inbox/_local/` has a `.gitignore` that ignores everything in the
folder. Full texts live there, on this machine only. The committed digest keeps short quotes with
timestamped links. Goal 004's R7 now names this practice.

**Related.** This is the same need as the
[private-context friction](_processed/2026-09-27-friction-private-context.md): context that can't
live in the public repo. That one is confidential; this one is under someone else's copyright.

**Options:**
- Adopt `_local/` as a scaffold convention, and use it for confidential context too.
- Use a separate private repo for sources that can't go public.
- Keep only links, and re-fetch on demand. That's fragile: X blocks crawlers, and YouTube needs
  tooling.

**Implication for the harness (H-001).** A context layer must hold material it may not
redistribute. Licensing is an access tier alongside classification. Provenance should point to the
restricted copy, not only to a public URL.
