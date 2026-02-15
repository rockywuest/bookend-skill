# Bookend Patterns and Anti-Patterns

## When to Checkpoint

The default rule is "every ~30 minutes or after every task," but some situations demand immediate checkpoints:

- **After a big decision**: If you decided on an architecture, migration strategy, or API design — checkpoint before you forget the rationale
- **Before a risky operation**: About to run a migration, deploy, or delete something? Checkpoint first so you can recover if it goes wrong
- **When context is getting full**: If you notice the conversation is long, checkpoint NOW. Don't wait for compaction to happen
- **After resolving a blocker**: When a dependency unblocks, capture the new state immediately
- **Before switching topics**: If the human says "actually, let's work on X instead," checkpoint the current thread first

## The Recovery Test

Ask yourself: **If this session ended right now and a fresh agent read only `state/current.md`, could it continue the work?**

If the answer is no, your state file is missing something. Common gaps:

- Decisions made but not recorded
- Blockers identified but not noted
- Context from earlier in the conversation that never made it to state
- Pending tasks that exist only in the conversation

Run this mental test every time you checkpoint.

## Memory Hierarchy

The three memory layers serve different purposes. Don't mix them:

| Layer | File | Content | Lifespan |
|-------|------|---------|----------|
| **State** | `state/current.md` | What's happening RIGHT NOW | Overwritten every checkpoint |
| **Daily** | `memory/YYYY-MM-DD.md` | What happened today (raw events) | Permanent (one per day) |
| **Long-term** | `MEMORY.md` | Curated wisdom that applies across sessions | Permanent (actively maintained) |

**State** is ephemeral — it gets overwritten every checkpoint. It should never contain history, only current status.

**Daily memory** is a log — raw events, decisions, learnings from that day. It's append-only during the day.

**Long-term memory** is curated — only add things that are genuinely reusable. "User prefers tabs over spaces" belongs here. "Fixed a typo in line 42" does not.

## Anti-Patterns

### Verbose State Files

**Bad**: State file that's 500 lines with full code snippets, conversation history, and detailed technical explanations.

**Good**: State file that's 30-50 lines with short descriptions, priority tags, and clear next steps.

The state file should be scannable in 15 seconds. If an agent needs more detail, it can check the daily memory files.

### Log-Dump Daily Memory

**Bad**: Daily memory that's just a copy of the conversation.

**Good**: Daily memory with structured sections (Events, Decisions, Lessons, Open Questions) containing only significant items.

Ask: "Would future-me care about this?" If not, don't write it down.

### Never-Curated Long-Term Memory

**Bad**: Long-term memory that grows forever and contains stale information.

**Good**: Long-term memory that gets reviewed periodically. Remove entries that are no longer true. Update entries that have evolved.

The long-term memory should stay under 100 lines. If it's longer, you're not curating enough.

### Checkpoint Avoidance

**Bad**: "I'll checkpoint later, I'm in the middle of something."

**Good**: Checkpoint takes 30 seconds. The cost of losing context is 30 minutes of re-orientation.

Always checkpoint. Always.

## State File Structure Conventions

Use consistent section headers so agents can parse state files reliably:

- `## Active Threads` — Current work items with status and priority tags
- `## Recent Context` — Last 2-3 significant things that happened
- `## Pending Tasks` — Checkbox list of next actions
- `## Notes` — Anything that doesn't fit above (blockers, reminders, preferences)

Priority tags: `[HIGH]`, `[MEDIUM]`, `[LOW]`

Status indicators: "complete", "in progress", "blocked on X", "not started"
