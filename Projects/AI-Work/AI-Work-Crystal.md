---
name: AI-Work-Crystal.md
internal_name: YYYY-MM-DD-HHMM-AI-Work-Crystal
object_type: system
file_type: crystal
type: crystal (project: AI work)
status: template
version: v1.0
date: 2026-10-09
revised: 2026-10-09-1958 PT
author: tripLr
owner: Owner
license: MIT
location: Projects / AI-Work / AI-Work-Crystal.md
---

# AI-Work-Crystal

**What this is:** the master Crystal for everything you do with an AI in this container. It indexes the project's processes, tasks, conversations and history. Pointers only; no body text of other objects is pasted here. Copy this folder for each new project and rename it.

## Folder map
- `Projects / AI-Work /` (this project folder)
  - `AI-Work-Crystal.md` (this file)
  - `processes.md` (repeatable procedures any AI follows instead of being retrained)
  - `tasks.md` (daily or recurring work for the bots or the owner)
  - `Bots/Example-Bot/Example-Bot-Crystal.md` (template bot Crystal; copy per bot)
  - `Conversations/` (conversation records, written only when the owner asks; see processes.md Process 14)
  - `Object-History/` (dated copies of every superseded version of this project's objects; archive-first)

## Rules
1. **Processes and tasks:** a task with implications for later work is elevated to a process.
2. **Object history:** before any live write in this folder, the old version is copied to `Object-History/` with a dated name (processes.md Process 3). The owner owns durable writes.
3. **Conversations** go in `Conversations/` and are indexed below.
4. Edges follow `Dragon-Object-Schema.md` (typed, with a short reason).

## Object table

| Name | Version | Status | Last touched (by, when) | One-line summary |
|---|---|---|---|---|
| AI-Work-Crystal.md | v1.0 | template | Owner, YYYY-MM-DD | This Crystal |
| processes.md | v1.0 | template | Owner, YYYY-MM-DD | Repeatable procedures |
| tasks.md | v1.0 | template | Owner, YYYY-MM-DD | Daily and recurring work |
| Example-Bot-Crystal.md | v1.0 | template | Owner, YYYY-MM-DD | Template bot Crystal (Bots/Example-Bot/) |
| *(add one row per object you put in this folder)* | | | | |

## Conversation index
(empty; filled when Conversations/ is populated)

## Dragon Stack

**Role:** master index of the AI-Work project folder
**Facets:** index | project | processes | tasks

### Edges

up:: [[Projects-Crystal.md]] (this is a Projects-level folder) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
contains:: [[processes.md]] (repeatable procedures) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
contains:: [[tasks.md]] (daily and recurring work) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
contains:: [[Example-Bot-Crystal.md]] (template bot Crystal; knowledge, files, assignment ledger) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
contains:: [[Conversations]] (conversation records on request) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
contains:: [[Object-History]] (dated copies of superseded versions) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
mentions:: [[Dragon-Object-Schema.md]] (the rules these objects follow) {date: 2026-10-09, by: tripLr, src: build, status: proposed}

**Return:** Projects-Crystal.md
**Evidence rule:** Point only. Do not copy the layer below.

## Version log
- v1.0 (2026-10-09): public starter.

**End of AI-Work-Crystal.md**
