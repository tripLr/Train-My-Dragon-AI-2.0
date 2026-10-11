---
name: tasks.md
internal_name: 2026-10-10-2358-tasks
object_type: system
file_type: system
type: system (tasks)
status: template
version: v1.0
date: 2026-10-09
revised: 2026-10-10-2358 PT
author: tripLr
owner: Owner
location: Projects / AI-Work / tasks.md
copyrighted: no
---

# tasks.md

**Purpose:** daily or recurring runs, and work that depends on a bot or on the owner. Each task has a name, a date, who it belongs to, what triggers it, a short plain explanation, and the steps. Repeatable procedures live in `processes.md`.

**Promote to a process:** a task with implications for later work, in another job or another process, is elevated to a process in `processes.md`. A task that the owner repeats can also be upgraded to a process.

**Numbers are stable.** Other files cite them (for example Task 4). Add new tasks at the end; mark a finished one done instead of removing it.


## Task 1: Daily in-progress list mirror
- **Date:** 2026-10-09
- **Belongs to:** the manager assistant (bot)
- **In plain words:** every day, keep one copy of the list of work in progress in the project's Bots folder, so any AI can see what is open.
- **Trigger:** every day at a set time. The routine is paused until the owner gives Execute.
- **Steps:** 1. Use the local in-progress list (rebuild it from session history and context history if missing or empty). 2. Archive the previous stored copy to the history folder first (Process 3). 3. Write the new copy to the Bots folder under Projects / AI-Work. 4. Read it back to verify. 5. Message the owner only on failure or a rebuilt list. Nothing is deleted.

## Task 2: reserved
This number is reserved and not part of this public copy, so task numbers stay the same across the private and public sets.

## Task 3: Shared reminders (owner and bots)
- **Date:** 2026-10-09
- **Belongs to:** the owner and the manager assistant
- **In plain words:** one place for reminders that the owner and the bots both use; nothing is added without the owner's OK.
- **Trigger:** whenever the owner or a bot adds a reminder; reviewed at the start of a session (AGENTS.md boot steps).
- **Steps:** 1. Reminders are kept in `reminders.md` in the Personal-Assistant area. 2. A bot proposes a new reminder as a draft. 3. It is written only after the owner's Write Permission or Execute, archive-first (Process 3). 4. Done items are marked, not deleted. (Detailed steps to fill in.)

## Task 4: Conversation import series
- **Date:** 2026-10-10
- **Belongs to:** the owner decides; a research bot drafts and migrates in the workspace; the manager assistant files to the live folders on Execute
- **In plain words:** the recurring job of bringing past conversations in, ten at a time, following Process 18, until the list is done.
- **Trigger:** the owner says to start or resume a run (propose-only until Execute). Status: waiting on the owner's decisions.
- **Steps:** 1. Read the checkpoint file first. 2. Phase 0 of Process 18: migrate existing conversation objects to the current schema before any new batch. 3. Run the census refresh, then batches of 10 (Process 18, Part B). 4. Every 50: show the manifest, wait for Execute, then write archive-first (Process 3) and verify. 5. Update the checkpoint file last. 6. Report counts and skips (private ones by number only).

## Task 5: Public repository check (monthly)
- **Date:** 2026-10-10
- **Belongs to:** the manager assistant 
- **In plain words:** once a month, check the public repository still matches the live schema and processes, and fix it if not.
- **Trigger:** monthly, and after any change to the schema or to `processes.md`.
- **Steps:** 1. Compare the public copy of the schema and of the processes with the private live ones (cleaned copies only; Process 20). 2. List differences. 3. the owner decides what to publish (Process 19). Fixes to processes go on `main` (the stable branch); `dev` is only for the next major upgrade. 4. Report; change nothing without the owner's OK.

## Task 6: History index refresh (CANDIDATE, not adopted)
- **Date:** 2026-10-10
- **Belongs to:** the manager assistant 
- **In plain words:** Some setups keep an index of archived copies. If the owner wants one here, it would be refreshed once per job that archives files.
- **Trigger:** only if the owner adopts a history index; today there is none.
- **Steps:** the owner decides first. Nothing is done until then.

---

## Edges
up:: [[AI-Work-Crystal.md]] (project crystal for the AI-Work project) {date: 2026-10-10, by: owner, src: build, status: proposed}
echoes:: [[processes.md]] (peer file: repeatable procedures; a task is elevated there) {date: 2026-10-10, by: owner, src: build, status: proposed}
mentions:: [[reminders.md]] (Personal-Assistant area; home of Task 3) {date: 2026-10-10, by: owner, src: build, status: proposed}
mentions:: [[Dragon-Object-Schema.md]] (the rules Process 18 migrates objects to) {date: 2026-10-10, by: owner, src: build, status: proposed}

## Version log
- v1.0 (2026-10-10): merged tasks 1 to 6. Task numbers are stable.

**End of tasks.md (v1.0)**
