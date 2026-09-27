# Open questions and contradictions

Every contradiction or tension the agent notices goes here. Blocking items are also raised
with the user immediately.

Format:

```
### Q-NNN: short title
- status: open | resolved
- blocking: yes | no
- between: <source A> ↔ <source B>
- raised: YYYY-MM-DD
- notes: …
- resolution: DEC-NNN (and which files were updated)
```

## Open

### Q-001: What does "deployed" mean for the harness?
- status: open
- blocking: no
- between: vision.md ↔ (unspecified)
- raised: 2026-09-27
- notes: This shapes D1 and the eventual runtime choice (C1 is only a v0 default).

## Resolved

### Q-003: Should evolving project-scaffold-v1 be its own goal?
- status: resolved
- blocking: no
- between: DEC-003 ↔ (goal list)
- raised: 2026-09-27
- resolution: DEC-005, which creates goal 002.

### Q-002: What is the scaffold called?
- status: resolved
- blocking: no
- between: DEC-003 ↔ (unnamed)
- raised: 2026-09-27
- resolution: DEC-004 (project-scaffold-v1). The goal question moved to Q-003. Updated CLAUDE.md,
  vision.md, goal 001, and the ingest skill.
