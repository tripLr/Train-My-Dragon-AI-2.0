---
name: processes.md
internal_name: 2026-10-09-1955-processes
object_type: system
file_type: system
type: system (repeatable processes)
status: template
version: v1.0
date: 2026-10-09
revised: 2026-10-09-1955 PT
author: tripLr
owner: Owner
location: Projects / AI-Work / processes.md
copyrighted: no
---

# processes

## What this file is
When you work with an AI over time, you do not want to retrain it on a task you repeat. Each process here is written down once, so any AI can run it again, and a different AI can pick it up tomorrow.

## Processes and tasks
- **Tasks** are daily or recurring work for the bots or for you. They live in `tasks.md`.
- A task that has implications for later work, in another job or another process, is **elevated from a task to a process** and moves here.

## Who follows these
The owner decides. Any AI or bot that works in this folder follows these processes. Durable writes (anything that changes a live file) need the owner's explicit permission first (see `AGENTS.md`).

Each process has: name, version/date, short description, trigger, steps, where it is filed. Edit, add and remove processes to fit your own system.

---

## Process 1: Publish files to a public repository
**Version:** 2026-10-09
**What it is:** how files move from your private working folder to a public git repository.
**Trigger:** the owner names a file or set to publish.
**Rules**
1. **Source:** everything published is sourced from the private working folder, never from a scratch copy.
2. **Cleaned copies:** private information is removed in a cleaned copy (Process 2). The live working file is not changed or renamed.
3. **Archive first** (Process 3) before any change to a live file.
4. **Owner approves:** no push without the owner's explicit OK, one named file or set at a time.
**Steps**
1. The owner names the file(s) and the repository location. 2. Confirm the source file and the public name. 3. Make or confirm the cleaned copy (Process 2). 4. Owner says go. 5. Sign in if needed, commit with a plain message, push.
**Verify:** after the push, read the commit back: report the repository URL and commit hash, and confirm the file in the repository matches the cleaned copy. If anything differs, say so and do not claim success.
**Filed:** the public repository; cleaned copies beside the live file.

## Process 2: Redaction pass
**Version:** 2026-10-09
**What it is:** make a public-safe copy of a file. Copy it, strip private information, log every redaction (what kind of thing was removed and why, never the private text itself), and scan for emails, phone numbers, passphrases, account or file identifiers, private paths and personal names before anything is published. The original is never edited.
**Trigger:** before any file leaves private storage (Process 1) or is shared outside your folders.
**Steps**
1. Copy the file; work only on the copy. 2. Strip private information. 3. Log each redaction. 4. Scan the copy for emails, phone numbers, passphrases, identifiers, private paths and names. 5. The owner reviews before anything is published.
**Filed:** the redaction log sits beside the cleaned copy and is not published.

## Process 3: Archive-first write
**Version:** 2026-10-09
**What it is:** before any file is overwritten or replaced, save a dated copy of the old version to the history folder first. Then write the new version, then read it back to verify. Nothing is deleted.
**Trigger:** any overwrite, replace, rename or move of a live file.
**Steps**
1. Build the draft in a sandbox first; the sandbox is for drafts, so live files are written less often.
2. The owner approves the draft and the exact destination.
3. Save a dated copy of the old version to the history folder (`YYYY-MM-DD-HHMM-<name>`) and read it back to confirm it is complete.
4. Write the new version under the same stable name, then read it back and confirm it matches the draft.
5. Report what was written in plain English, by file name and location.
**Rules:** nothing is deleted. Superseded copies are kept. Trashing anything needs the owner's explicit, named OK.
**Filed:** the history folder for the file's own area (for example `Dragon-Object-History`, or the project's `Object-History`).

## Process 4: Crystal bootstrap
**Version:** 2026-10-09
**What it is:** create one crystal file per project or area, with a purpose, pointers and edges. One file each.
**Trigger:** a new project or area, or a crystal that is missing or wrong.
**Steps**
1. When several crystals need creating or fixing, start from the leaf (bottom) crystals and work up to the parent crystals, then the top one. Parents then summarize what their children already say, instead of guessed index entries.
2. For each crystal: write the purpose, the pointers (file name + location), and the edges with a short reason each.
3. Point, do not copy: no body text of other objects is pasted in.
**Filed:** in the folder the crystal indexes.

## Process 5: Research before building, and decision documents
**Version:** 2026-10-09
**What it is:** whenever the owner has a plan or process in mind, first search for what others have already done, then adapt the best of it to improve the new process before it is finalized. Sources are noted.
**Trigger:** the owner brings a new plan or process, or asks for research.
**Steps**
1. State the question. 2. Search for what others have done; note the sources. 3. Adapt the best of it into the new process. 4. When the result is a choice for the owner, present a decision document: an options menu with a short description, effort and best use for each option, and a choices table the owner fills in. Nothing is decided until the owner chooses. 5. Record the choices, then write the new process or task.
**Filed:** the project folder that asked for it.

## Process 6: Recurse and improve
**Version:** 2026-10-09
**What it is:** periodically review this processes file and its folder, find processes that are close to something new that is needed, search for similar processes from other people, and adapt them to strengthen or replace the existing ones, so work already done is never repeated. Changes are proposed, archive-first, and need the owner's OK.
**Trigger:** periodically (the owner sets how often), and when something close to an existing process is needed.
**Steps:** to fill in.
**Filed:** this file.

## Process 7: Name files by location, point by name
**Version:** 2026-10-09
**What it is:** name and point to every file by its external name plus its folder location, so it can be found by name and not by a storage-system file id.
**Trigger:** whenever a file is created, linked or cited.
**Steps**
1. Give the file a short readable name that follows `Dragon-Object-Schema.md`. 2. Write links (edges) from the file name and say where it lives; never rely on an id or a share link as the only way to find it. 3. Names survive updates and let the folder be published by name.
**Filed:** rule lives in `AGENTS.md` (pointer rule); this entry is the working reminder.

## Process 8: Batch write, and one write per file
**Version:** 2026-10-09
**What it is:** when several files change together, do not write them one by one as they come up. Draft all of them, get one review, write each file once, then verify. Repeated rewrites of the same file create duplicate-file confusion and extra archive copies.
**Trigger:** two or more files, or two or more changes to one file, in the same job.
**Steps**
1. Draft every file in the sandbox. 2. Queue all changes per file and make them in one write with one change note. 3. Write a manifest: each file, old to new version, and what changes; for any change to a live system file include the diff. 4. The owner approves the manifest. 5. For each existing file follow Process 3, working from the leaf files up (Process 4). 6. Verify: one live file per name in every touched folder, no dangling edges, no stale "draft / proposed" wording. 7. Report what was written, with versions.
**Filed:** the manifest and report go in the job's chat or the project's conversation record.

## Process 9: Audit (read-only)
**Version:** 2026-10-09
**What it is:** review the folder tree without changing anything and report what is wrong. An audit never writes; fixes go through Process 3 or Process 8. `Dragon-Object-Schema.md` defines a lint pass; use it rather than restating it.
**Trigger:** the owner asks for a review, or before a public release.
**Steps**
1. Run the schema's lint pass. 2. Also check: version numbers named in one file match the file they name; no stale "draft / proposed" wording; each header matches the real file and folder; every edge has a short reason; every object points to its crystal and the crystals can be traced to `AGENTS.md`; no two files contradict each other on one rule; no dangling edges. 3. Report the findings; change nothing.
**Filed:** one report file, `REVIEW-lint-YYYY-MM-DD.md`.

## Process 10: After a manual folder change by the owner
**Version:** 2026-10-09
**What it is:** when the owner moves, renames or adds files or folders by hand, re-read the storage before writing anything. The storage is the source of truth; an earlier path, id or list can be wrong.
**Trigger:** the owner says they moved, renamed or added something, or a path no longer resolves.
**Steps**
1. List the affected folders again. 2. Update the draft paths and names. 3. Fix every reference to the old place (edges by name usually survive; paths in prose do not). 4. Then follow Process 3 or Process 8. Do not undo or redo the owner's change.
**Filed:** nothing to file.

## Process 11: Other people's files and containers (point by name, never copy)
**Version:** 2026-10-09
**What it is:** when something lives in another person's or another system's space, point to it by name and say where it lives. Do not paste its content into your files: a copy goes stale and can leak what was private.
**Trigger:** content from outside your own folders is needed.
**Steps**
1. Write the pointer from the file's name and location. 2. If the content itself is needed, ask its owner. 3. Anything that crosses into a separate container needs a decision recorded in `AGENTS.md`.
**Filed:** nothing to file.

## Process 12: Ask versus act
**Version:** 2026-10-09
**What it is:** when a request is ambiguous, or two readings would lead to different writes, ask one real question first. When the request is clear and inside the sandbox, act.
**Trigger:** any request where two readings give different results.
**Steps**
1. Ask one specific question that names the options, then wait. 2. Reversible sandbox drafting can continue while waiting. 3. Anything needing the owner's permission (durable write, outside email, publishing) waits for it.
**Filed:** nothing to file.

## Process 13: Voice sessions
**Version:** 2026-10-09
**What it is:** in a voice session, lead with the result in one or two sentences, then give detail only if asked. Voice is slow to listen to and cannot be skimmed.
**Trigger:** any voice session.
**Steps**
1. Say what was done or found first. 2. Keep long lists, ids and file text for the written record. 3. If something is still owed when the session ends, post it in writing afterwards.
**Filed:** nothing to file.

## Process 14: Conversation object (on request)
**Version:** 2026-10-09
**What it is:** only when the owner asks, copy a whole conversation into one linked knowledge object, built by `Dragon-Object-Schema.md` (header, typed edges with reasons, pointer to its crystal). User-triggered, never automatic.
**Trigger:** the owner asks.
**Steps**
1. Draft in the sandbox. 2. Header and typed edges with short reasons, plus a pointer to its crystal. 3. Name it by date and content (Process 7). 4. Write it with Process 3 into `Projects / AI-Work / Conversations`. 5. Add it to the conversation index in the project crystal in the same job (Process 8).
**Filed:** `Projects / AI-Work / Conversations`.

---

## Edges
up:: [[AI-Work-Crystal.md]] (project crystal for AI work in this container) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
echoes:: [[tasks.md]] (peer file: daily and recurring work; a task with later implications is elevated here) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
mentions:: [[Dragon-Object-Schema.md]] (master rules for objects, history and lint; Processes 3, 7, 9 point to it) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
mentions:: [[AGENTS.md]] (the operating contract these processes follow) {date: 2026-10-09, by: tripLr, src: build, status: proposed}

## Version log
- v1.0 (2026-10-09): public starter set of 14 processes, generalized from a working private set. Edit freely.

**End of processes (v1.0, template)**
