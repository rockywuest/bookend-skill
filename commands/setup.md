---
description: Set up the Bookend memory system in your workspace
allowed-tools: [Read, Write, Bash, Glob, Grep]
---

# Bookend Setup

Initialize the Bookend structured memory system in the current workspace.

## Instructions

Perform the following steps to set up Bookend:

1. **Check for existing setup**: Use Glob to check if `state/current.md` already exists. If it does, inform the user that Bookend is already set up and ask if they want to reinitialize.

2. **Create state directory and files**:
   - Create `state/current.md` with this content:

     ```markdown
     # Current State

     > Last updated: (today's date and time)

     ## Active Threads

     - (none yet)

     ## Recent Context

     - Fresh session — Bookend just initialized

     ## Pending Tasks

     - [ ] (none yet)

     ## Notes

     - Bookend memory system initialized
     ```

   - Create `state/ROUTINES.md` with morning briefing, checkpoint, and end-of-day routine descriptions
   - Create `state/nightly-backlog.md` as an empty task list

3. **Create memory directory**: Create the `memory/` directory if it does not exist.

4. **Create long-term memory file**: Create `MEMORY.md` with this content:

   ```markdown
   # Long-Term Memory

   > Curated wisdom. Only add things that are genuinely reusable across sessions.

   ## Preferences

   -

   ## Project Context

   -

   ## Patterns That Work

   -

   ## Anti-Patterns (Avoid)

   -

   ## Key Decisions (with rationale)

   -
   ```

5. **Update AGENTS.md**: Read the existing `AGENTS.md` if it exists, then append the Bookend protocol section:

   ```markdown
   ## Bookend Protocol

   ### Session Start
   1. Read `state/current.md` — where things stand RIGHT NOW
   2. Read `memory/YYYY-MM-DD.md` (today + yesterday) — recent context
   3. If main session: also read `MEMORY.md` — long-term memory

   ### Checkpoints (every ~30 min or after completing a task)
   1. Update `state/current.md` with current state
   2. Append significant events to `memory/YYYY-MM-DD.md`
   3. If context is getting full: checkpoint NOW
   4. Rule: If context compacts, `state/current.md` must be enough to continue

   ### Session End
   1. Finalize `state/current.md`
   2. Close daily memory file
   3. If lessons learned: update `MEMORY.md`
   ```

   If `AGENTS.md` does not exist, create it with a header and the protocol section.

6. **Report results**: Tell the user what was created and how to use it. Mention:
   - The morning briefing will happen automatically at session start
   - Checkpoints happen every ~30 minutes or after each task
   - They can say "checkpoint" at any time to trigger a manual save
   - End-of-day wrap happens when they say "end of day" or "wrap up"
