---
name: AGENTS.md
internal_name: 2026-10-10-2358-agents-public
object_type: system
file_type: rules
type: system (contract: operating rules)
status: template
version: v1.2
date: 2026-10-09
revised: 2026-10-10-2358 PT
author: tripLr
owner: Owner
source: condensed from a working private AGENTS file (universal rules only)
location: repository root
license: MIT
---

# AGENTS.md (Dragon, public, AI-agnostic)

1. **Where the files live:** the working files live in the owner's own folder (any storage the owner controls). This repository holds only files the owner has approved for public release.
2. **Purpose:** one set of knowledge and rules for working with a person across any AI. Notes, objects and AI work are kept in plain files so they last across apps and AI tools.
3. **Owner:** the files belong to the owner. The owner owns durable writes.
4. **Entry point:** this file is the entry point and the shared rule source. The full rules for object headers, pointers, naming, history and orbs live in `Dragon-Object-Schema.md` (Resources folder). Point to that file; do not restate it here.
5. **Know which AI you are:** before acting, state which AI interface you are, using only what your own instructions or profile say. Do not use another window's answer. Do not invent an agent id; write "not provided". If it is unclear, ask.
6. **Propose first:** assistants draft and point. Durable writes to live files happen only after the owner gives explicit permission to write.
7. **Show the diff:** when a proposal changes an existing live file, the review packet includes the full proposed draft, a unified diff against the current live file, and a short summary. The owner reviews the diff before approving.
8. **Archive first (safe writes):** before a live file is changed or replaced, keep a dated copy of it in the matching history folder (`YYYY-MM-DD-HHMM-<name>`) and check that the copy reads back. Only then write the new version, under its stable name.
9. **Nothing removed without an archive and an OK:** retired versions go to the history folder. A file is trashed only after its archive copy and its replacement are both verified, and only with the owner's named OK.
10. **Write and verify:** after every write, move or trash, read the result back and confirm it worked. Do not assume a previous session's behavior.
11. **Write objects correctly:** a file written the way objects are meant to be written has a header (name, type, status, owner, version, revised date), a location, edges, and a history copy before any change. Then any AI can walk the folders and find its way.
12. **Point, do not copy:** refer to other files by their external name plus location (folder path). The date on an edge is its version. A file id is optional and never the only key. Do not paste another file's body into this one.
13. **Staging:** new captures and assistant drafts land in a staging inbox first. They are never live files. The owner examines them, names the destination, and gives permission before anything is filed.
14. **Processes and tasks:** `processes.md` and `tasks.md` (in `Projects / AI-Work`, the first project) are the "how". Processes are repeatable procedures: any AI follows them instead of being retrained on the same job. Tasks are daily or recurring work. A task with implications for later work is elevated to a process.
15. **Orbs:** orbs are optional, thin session records, a backup and accountability aid for when a long thread loses context or work moves between AIs. Name them `YYYY-MM-DD-HHMM-<source>-orb.md`, keep them in `Dragon-Orb-History` (indexed by `Orb-History-Crystal.md`; copy `Blank-Orb-Template.md` to start one), and do not merge orbs from different AIs; point across instead.
16. **Public and private:** this file is public. A working folder is private. Nothing from it goes to a public repository unless the owner has approved that exact file after a redaction pass (see `processes.md`, Process 20, and Process 19 for publishing), and no secrets or personal details belong in any shared file.
17. **Reports:** plain English, times stated with their time zone, files named by name plus location.

## Edges
mentions:: [[Dragon-Object-Schema.md]] (Resources; full rules for headers, pointers, naming, history, orbs) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
mentions:: [[processes.md]] (Projects / AI-Work; repeatable procedures) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
mentions:: [[tasks.md]] (Projects / AI-Work; daily and recurring work) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
up:: [[README.md]] (root index: why this repository exists and how it is laid out) {date: 2026-10-09, by: tripLr, src: build, status: proposed}

**End of AGENTS.md (Dragon, public) v1.2**
