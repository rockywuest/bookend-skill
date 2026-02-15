# Example: Evening Wrap

This is what a typical end-of-day routine looks like when the Bookend skill runs the evening wrap protocol.

---

## What the agent does

1. Updates `state/current.md` with final state
2. Finalizes the daily memory file `memory/YYYY-MM-DD.md`
3. Evaluates if anything belongs in `MEMORY.md` (long-term)
4. Summarizes what was accomplished

## Example state update

The agent updates `state/current.md` to reflect end-of-day status:

```markdown
# Current State

> Last updated: 2026-02-15 18:30

## Active Threads

- Auth refactor: JWT middleware done, session migration tested and working
- Settings page: design review Thursday 10am
- Staging access: still waiting on DevOps (day 3)

## Recent Context

- Ran session migration script successfully on local DB
- Updated API docs for /auth/login, /auth/refresh, /auth/logout
- Reviewed PR #47 — approved with minor comments

## Pending Tasks

- [ ] Run session migration on staging (blocked: no access yet)
- [ ] Address Maria's response to PR #47 comments
- [ ] Prepare design review materials for Thursday

## Notes

- Migration script needs BATCH_SIZE env var set (default 1000 is too slow for prod)
```

## Example daily memory entry

The agent appends to `memory/2026-02-15.md`:

```markdown
# Memory: 2026-02-15

## Events

- Ran session migration script — works on local, 45k records in 3 minutes
- Updated API docs (3 endpoints)
- Reviewed and approved PR #47 with 2 minor comments

## Decisions Made

- Set BATCH_SIZE=5000 for migration based on load testing
- Keep old session table for 30 days post-migration as rollback safety net

## Lessons Learned

- Migration dry-run on local first saves debugging time on staging

## Open Questions

- Should we backfill analytics events for migrated sessions?
```

## Example long-term memory update

If a lesson is broadly reusable, the agent adds it to `MEMORY.md`:

```markdown
## Patterns That Work

- Always dry-run data migrations on local before staging — catches 90% of issues
```

---

## Key characteristics

- **State is self-contained**: A fresh session tomorrow can pick up from `state/current.md` alone
- **Daily memory is raw**: Events, decisions, and learnings captured while fresh
- **Long-term memory is curated**: Only genuinely reusable wisdom gets promoted
