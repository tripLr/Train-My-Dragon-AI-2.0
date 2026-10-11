---
name: processes.md
internal_name: 2026-10-10-2358-processes
object_type: system
file_type: system
type: system (repeatable processes)
status: template
version: v1.0
date: 2026-10-09
revised: 2026-10-10-2358 PT
author: tripLr
owner: Owner
location: Projects / AI-Work / processes.md
copyrighted: no
---

# processes.md

## What this file is
As the owner develops interactions with AI, they don't want to retrain an AI on a task that can be repeated. That is where these processes live: each one is written down once so any AI can run it again.

A **process** is a repeatable procedure: written down once so any AI can run it again and nobody has to retrain an AI on a job that repeats. A **task** is daily or recurring work, or work that depends on a bot or on the owner; tasks live in `tasks.md`. A task with implications for later work (in another job or another process) is **elevated** to a process and moves here.

Each process has a number, a short plain-words explanation, the rule, why, how, where it is filed, and its source. **Numbers are stable: other files cite them (for example Process 18). Do not renumber; add new processes at the end and retire one by marking it retired.**

**Who follows these:** the owner decides. Any AI or bot that works in this folder follows these processes. Durable writes (anything that changes a live file) need the owner's explicit permission first (see `AGENTS.md`).


---

## Process 1: Name files by location, point by name
- **In plain words:** give every file a name that makes sense on its own, and point to files by name and folder, never by a storage id.
- **Rule:** name and point to every file by its external name plus its folder location, so it can be found by name and not by a storage-system file id. Follow the naming rules in `Dragon-Object-Schema.md` (Part 5).
- **Why:** names survive updates (a rewritten file can get a new id) and let the folder be published to a repository by name.
- **How:** (1) short readable name; (2) write links (edges) from the file name and say where it lives; never rely on an id or share link as the only way to find a file; (3) edges are by name, so a link stays true when a file moves folders.
- **Filed:** rule lives in AGENTS.md (pointer rule); this entry is the working reminder.

## Process 2: Draft in the sandbox first
- **In plain words:** build the draft somewhere safe first; only write to the real folders when it is ready.
- **Rule:** before writing to the live folders, the bot builds the draft in its sandbox, which has full read, write and append access.
- **Why:** the sandbox is where drafts are built safely; writing live only when a draft is ready reduces direct edits to live files.
- **How:** build and check the draft in the sandbox, then follow Process 3.

## Process 3: Archive-first write (safe write structure)
- **In plain words:** before replacing a file, keep a dated copy of the old one; then write the new one; then read it back. Nothing is deleted.
- **Problem:** some storage systems (Google Drive, for example) give a new id to every new file, even one with the same name, and the tools used can create and move files but cannot overwrite them. Two live files with one name confuse people.
- **Safe sequence:** (1) the owner approves the draft and the exact destination (Write Permission or Execute). (2) **Archive:** save the old version in the history folder with a dated name (`YYYY-MM-DD-HHMM-<name>`), and read it back to confirm it is complete. Where a copy would leave two live files of one name, the old live file itself is **moved** into the history folder under its dated name: that move is the archive. (3) Write the new version under the same stable name. (4) Read it back and confirm it matches the draft. (5) Report what was written, by file name and location.
- **Nothing is deleted.** Superseded copies are kept. Trashing anything needs the owner's explicit, named OK (`Dragon-Object-Schema.md` 6.3; AGENTS.md).
- **Good to know:** storage trash is temporary (Google Drive empties its own after about 30 days), so the dated copy in the history folder is the permanent one; the trash is only a short-term safety net.
- **Filed:** the history folder for the file's own area: `Projects / AI-Work / Object-History` for project files; `Dragon-Object-History` for root-level files such as AGENTS.md and the schema.

## Process 4: Dragon thrash and anti-dragon thrash
- **In plain words:** rewriting the same file again and again makes a mess. Plan the writes so each file is written once.
- **Dragon thrash:** unnecessary repeated writes and edits to files, which create duplicate-file confusion and extra archive copies.
- **Anti-dragon thrash:** (1) sandbox drafting first (Process 2), (2) archive first (Process 3), (3) one write per file (Process 10), (4) name-based discovery (Process 1).
- **Note:** a light-hearted process; it may not need to run full time.

## Process 5: Bottom-up crystal building
- **In plain words:** build the small indexes first, then the bigger ones that summarize them.
- **What a crystal is:** one index file per project or area, with a purpose, pointers and edges. One file each, no multi-file structure.
- **Rule:** when creating or fixing crystals, start from the leaf (bottom) crystals, such as a bot crystal or a course crystal, and work up to the parent crystals, then the top one.
- **Why:** leaves are easiest to get right; parents then summarize what their children already say instead of guessed index entries. Building from the top means inventing entries before the facts exist.
- **How:** (1) for each crystal write the purpose, the pointers (file name + location), and the edges with a short reason each; (2) point, don't copy: no body text of other objects is pasted in.

## Processes 6 and 7: reserved
These numbers are reserved and not part of this public copy. They are kept so that process numbers stay the same across the private and public sets.

## Process 8: Batch write (many files in one reviewed job)
- **In plain words:** when many files change together, plan them all, get one OK, write each once, then check.
- **Rule:** when several files change together, don't write them one by one as they come up. Draft every file in the sandbox, write a manifest (each file, old to new version, and what changes; for a live system file include the diff), get the owner's approval, then write from the leaf files up (Process 5) and finish with a read-only verification.
- **Why:** each file is written once, links stay consistent, and the owner sees the whole change before it lands (Processes 4 and 10).
- **How:** (1) draft all files (Process 2); (2) manifest; (3) approval; (4) for each existing file follow Process 3, leaves first; (5) verify, reading the storage only: one live file per name in every touched folder, each size matches the final text, no dangling edge (every `[[target]]` resolves), no stale "draft / proposed" wording left in a header, footer or edge status; (6) report what was written, with versions.

## Process 9: Audit (read-only eight-check review)
- **In plain words:** look over the whole folder tree and report what is wrong, without changing anything.
- **Rule:** an audit never writes; fixes go through Process 8 or Process 3. `Dragon-Object-Schema.md` Part 8 defines a lint pass; run it, and also check the eight items below.
- **The eight checks:** (1) version numbers named in one file match the file they name; (2) no stale "draft / proposed / awaiting approval" wording in a header, footer or edge status; (3) each header matches the real file and folder; (4) every edge has a short reason, and crystals link sideways to their peers; (5) every object points to its crystal and the crystals can be traced to AGENTS.md; (6) no two files contradict each other on one rule; (7) no dangling edges; (8) names follow Process 1 and the schema.
- **Why:** problems found early are cheap to fix; found late they spread through the crystals.
- **Filed:** one report file, `REVIEW-lint-YYYY-MM-DD.md`.

## Process 10: One write per file (queue and merge changes)
- **In plain words:** if three changes are coming for one file, make them together in one write.
- **Rule:** when several changes are coming for the same file, queue them and make them in one write, so no file is rewritten twice in a job. Queue related changes across files too (Process 8).
- **Why:** every rewrite makes a new id and a new archive copy; repeated rewrites are dragon thrash (Process 4).
- **How:** keep a list of pending changes per file while drafting; apply them together; write the file once with one change note.

## Process 11: Research before building, and decision documents
- **In plain words:** before building something new, see what others have done; when there is a choice, give the owner a menu to pick from.
- **Rule:** whenever the owner has a plan or process in mind, first search for what others have already done, note the sources, and adapt the best of it before the plan is finalized. When the result is a choice, present it as a decision document: an options menu with a short description, effort and best use for each option, and a choices table the owner fills in. Nothing is decided until the owner chooses.
- **Why:** options with short reasons are easy to choose from, and the choices become the next process or task.
- **How:** (1) state the question; (2) search and note sources; (3) list the options; (4) add the choices table and mark the document "waiting for choices"; (5) give it typed edges (for example `feeds::` to the process it will become); (6) record the choices, then write the new process or task.

## Process 12: After a manual folder change by the owner
- **In plain words:** if the owner moved or renamed things by hand, look again before writing anything.
- **Rule:** when the owner moves, renames or adds files or folders by hand, re-read the storage before writing anything. The storage is the source of truth; an earlier path, id or list can be wrong.
- **How:** (1) list the affected folders again; (2) update the draft paths and names; (3) fix every reference to the old place (edges by name usually survive; paths in prose do not); (4) then follow Process 3 or Process 8. Do not undo or redo the owner's change.

## Process 13: Other people's files (point by name, never copy)
- **In plain words:** if a file lives in someone else's space, point to it; do not copy it.
- **Rule:** when something lives in another person's, another bot's or a separate container's space, point to it by name and say where it lives. Do not paste its content into your files. If the content is needed, ask its owner.
- **Why:** a copy goes stale and can leak what was private.
- **How:** write the edge or mention from the file's name and location (Process 1); anything that crosses into a separate container needs the decision recorded in AGENTS.md.

## Process 14: Ask versus act
- **In plain words:** if a request could mean two things, ask one clear question first.
- **Rule:** when a request is ambiguous, or two readings would lead to different writes, ask one real question first. When the request is clear and inside the sandbox, act.
- **Why:** a wrong write costs an archive and a rewrite; a question costs one reply.
- **How:** ask one specific question that names the options, and wait. Reversible sandbox drafting can continue while waiting. Anything needing the owner's permission (live write, outside email, publishing) waits for their Write Permission or Execute.

## Process 15: Voice calls
- **In plain words:** on a call, give the answer first, in a sentence or two; details go in writing.
- **Rule:** on a voice call, lead with the result in one or two sentences, then give detail only if asked. If something is still owed when the call ends, post it in writing afterwards.
- **Why:** voice is slow to listen to and cannot be skimmed.
- **How:** say what was done or found first; keep long lists, ids and file text for the written record; post what is still owed when the call ends.

## Process 16: Conversation object, one at a time (on request)
- **In plain words:** when the owner asks, turn one conversation into one linked file that any AI can find and read.
- **Rule:** only when the owner asks, the bot copies one whole conversation into one linked knowledge object, built by `Dragon-Object-Schema.md` (a `thread` object). It is user-triggered, never automatic, and it is not a session record. Many conversations at once go through Process 18.
- **Why:** it turns a long chat into something any AI can find and walk through without the chat app.
- **How:** (1) draft in the sandbox (Process 2); (2) full header (Part 2), typed edges with short reasons, and pointers to its crystal and to AGENTS.md; (3) name it by date and content (Process 1); (4) write it with Process 3 into `Projects / AI-Work / Conversations`; (5) add it to the conversation index in `AI-Work-Crystal.md` in the same job (Process 10).
- **Filed:** `Projects / AI-Work / Conversations`.

## Process 17: Schema rules apply when conversations are imported
- **In plain words:** an imported conversation must be written the same way as every other object, not dropped in as a raw dump.
- **Rule:** a conversation brought into the container is written as a schema object. This covers one copied on request (Process 16), one imported in a batch (Process 18), a session pulled in from an AI app, and an export from another AI app. Always user-triggered, never automatic.
- **What the schema requires:** (1) a full header (`Dragon-Object-Schema.md` Part 2) with `object_type`, `file_type` and `type: thread` set honestly; (2) typed edges `type:: [[Target]] (why) {date, by, src, conf, status}` with a short reason on each (Part 3); (3) pointers: an `up::` edge to the conversation index (the project Crystal) and a pointer to AGENTS.md, plus sideways links to related objects; (4) a name made of date and content name and, for another app, an optional source tag such as `-OtherApp` (Part 5); (5) no secrets (Part 7).
- **Where it goes and how it is indexed:** into `Projects / AI-Work / Conversations`, and listed by file name in the conversation index of `AI-Work-Crystal.md`. The index is rewritten once per import job (Process 10).
- **Why:** an imported conversation that follows the schema can be found and walked from any file by any AI, and its links stay true because they are by name. A raw dump is a lump no one can navigate.
- **How:** (1) the owner asks for the import; (2) draft in the sandbox (Process 2); (3) name it (Process 1); (4) write it with Process 3; (5) add its row and edge to the index in the same job (Process 10); (6) verify, reading the storage only (Process 8, step 5): one live file per name and every `[[target]]` resolves.
- **Ties:** Process 16 is the on-request way and follows this rule. A voice-call transcript filed to the conversation folder is indexed under this process (whether it also gets a full header at filing time: open, see Process 15). Process 18 is the batch way.

## Process 18: Conversation import in batches
- **In plain words:** bring many past conversations in safely: ten at a time, with a progress file so a fresh session can resume, and a write to the live folders only every fifty.
- **Rule:** conversations come into the workspace in small batches. Each becomes one schema-conformant thread object (Processes 16 and 17), and every edge goes into a workspace draft crystal by append only. Progress lives in a checkpoint file, not in anyone's memory or context. The live folders are written only in batches of 50, archive-first (Process 3) with read-back verify, and only on the owner's Execute. Private conversations are never imported without the owner's OK. No credentials in any file.
- **Why:** a written process plus a checkpoint lets a fresh session resume without context; small batches limit damage if access or context fails mid-run; workspace first, live write in batches fits Processes 8 and 10. One process covers every source (one AI app today, another later).
- **Who runs it:** the owner decides. Whoever runs it works propose-only until the owner says Execute. Suggested: a research bot drafts and imports into the workspace; the manager files to the live folders on Execute.

**Phase 0. Migrate existing objects first (once per run series).** Conversation objects built before the current schema version are migrated to it before any new batch, in a copy (never on the originals, which are the evidence of what is filed): split the verbatim body into a RAW file; bring the header, Dragon Stack, edges (fixed edge-word map), sections and end line to the current schema; lint; log each object in the checkpoint file; then one reviewed live write (Process 8). Reason: every new batch built to the old pattern would be more objects to migrate.

**Part A. Before the first run.** (1) Redo the census: capture the current conversation list (title, date, source id) into a new dated census file; never overwrite the earlier one; diff by source id: `known`, `new`, `gone`; new rows get the next numbers so old numbers stay valid; add a `speaker` column; report counts to the owner before any batch. (2) Activate access to the source: a working way to read a conversation by id, or an export or paste from the owner. Credentials never go in files or chat; use the approved secure sign-in approach. If a path needs the owner, say so and wait. (3) Create the run files in the workspace: checkpoint file, append-only draft crystal, raw folder (never edited after capture), objects folder.

**Part B. The batch loop.** *Pre-flight, every run:* read the checkpoint file; test-fetch one conversation; if the fetch fails, returns a login page or odd text, **stop**, log it, tell the owner in plain words, and do nothing else (no guessing, no invented text, no switching tools to get around a block). *Step 2:* take the next 10 rows (skip private rows unless the owner OK'd that one; log them `skipped-private`); save each raw capture; mark completeness (`complete: yes | partial | no`); record a hash per raw file. *Step 3:* create the draft crystal once (first batch), then append only. *Step 4:* one thread object per conversation (Process 17 rules); edges drawn from the thread use `src: conversation`; keep what is said separate from what the AI summarized; dedup by `source_id` (the schema's dedup rule): append `## Continued YYYY-MM-DD` and bump the version, never a second object. *Step 5:* append the new rows and edges to the draft crystal; update the checkpoint file; re-read the last block. **Repeat** until 50 are done.

**Part C. Batch write to the live folders (every 50).** Only on the owner's explicit Execute naming the destination; follows Processes 3 and 8. (1) Show the manifest: the 50 objects (name, version, subject, private flag), the crystal diff, the exact destination, and any skipped or failed items. (2) Use a dated batch folder; never overwrite an existing file; if a name exists, stop and ask. (3) Archive first: the current live crystal goes to the history folder under its dated name, read back. (4) Write the 50 objects, then the new crystal version. (5) Read back every file and compare to the workspace copy; report matches and mismatches by file name; if anything differs, say so and do not claim success. (6) The draft crystal keeps growing with a new batch heading; note in the checkpoint file which live crystal version it matches. (7) Raw captures stay in the workspace unless the owner says to file them.

**Privacy and skip rules.** Never import, summarize or open for content a conversation the owner has not cleared if it has intimate, health, family, legal or financial detail; treat it as private until told otherwise. A private conversation is logged as `skipped-private` with its number only. If cleared, it gets `restricted: true`, is linked by name only, and its content is never copied into another object (the schema's privacy rules). Never in any object: passwords, tokens, account numbers, ids used as keys, private URLs. Deletion decisions stay the owner's.

**Ownership.** the owner says whose conversation it is; without that, ask, do not guess. Each person's conversations go to that person's own container and crystal, with their own checkpoint file, draft crystal and census. A cross-container pointer is by name only (Process 13).

**Stall, drift and lost-access handling.** The checkpoint file is the only memory: read it first, update it last. If the session seems to have drifted, finish the current conversation, write the checkpoint, and stop; a fresh session resumes. If access is lost: stop, log time and number, tell the owner, at most one retry, no other route (no scraping of cookies or tokens, no substitute accounts). Raw first, so a failure never loses a capture. Repeat runs are idempotent (dedup by `source_id` and hash). A failed conversation is logged and skipped; retried only in a later pass. If a capture is partial, the object says so.
- **Filed:** run files in the workspace; objects in `Projects / AI-Work / Conversations` (or the conversation-history folder the owner chooses).

## Process 19: Publish files to the public repository
- **In plain words:** how a private file becomes a public one, safely, one named set at a time.
- **Rule:** everything published is sourced and named from the private working folder, never from a scratch copy or another person's folder. The public repository mirrors the *public version* of the running copy; the private copy stays the source of truth. A cleaned copy is made first (Process 20) and published beside the live file; the live file is not changed or renamed. Archive first (Process 3) before any change to a live file. No push without the owner's explicit OK, one named file or set at a time.
- **Branches:** `main` is the stable branch of the public repository, and **process fixes are made on `main`**. `dev` is staging for the next major upgrade; it is not where fixes go.
- **How:** (1) the owner names the file(s) and the repository location; (2) confirm the source file and the public name; (3) make or confirm the cleaned copy (Process 20); (4) the owner says go; (5) sign in if needed, commit with a plain message, push (plain push, never force without the owner's OK); (6) verify: clone the remote fresh, report the commit hash and URL, and confirm the repository matches the cleaned copy; if anything differs, say so and do not claim success.
- **Filed:** the public repository; cleaned copies beside the live file or in the build folder.

## Process 20: Redaction pass
- **In plain words:** make a safe-to-share copy: strip private details, write down what you removed (not the private text), and scan before sharing.
- **Rule:** copy the file, strip private information, log every redaction (what kind of thing was removed and why, never the private text itself), and scan for emails, phone numbers, passphrases, account or file identifiers, private paths, personal names and bot names before anything is published. The original is never edited.
- **Trigger:** before any file leaves private storage (Process 19) or is shared outside your folders.
- **How:** (1) copy; work only on the copy; (2) strip; (3) log; (4) scan; (5) the owner reviews before anything is published.
- **Filed:** the redaction log sits beside the cleaned copy and is not published.

## Process 21: Recurse and improve
- **In plain words:** now and then, review these processes against what others do, and improve them so work is never repeated.
- **Rule:** periodically review this processes file and its folder, find processes close to something new that is needed, search for similar processes from other people, and adapt them to strengthen or replace the existing ones. Changes are proposed, archive-first, and need the owner's OK.
- **Trigger:** periodically (the owner sets how often), and when something close to an existing process is needed.
- **Steps:** to fill in.

---

## Edges
up:: [[AI-Work-Crystal.md]] (project crystal for the AI-Work project) {date: 2026-10-10, by: owner, src: build, status: proposed}
echoes:: [[tasks.md]] (peer file: daily and recurring work; a task with later implications is elevated here) {date: 2026-10-10, by: owner, src: build, status: proposed}
mentions:: [[Dragon-Object-Schema.md]] (master rules for objects, history and lint; Processes 1, 3, 9, 17 point to it) {date: 2026-10-10, by: owner, src: build, status: proposed}
mentions:: [[AGENTS.md]] (the operating contract these processes follow) {date: 2026-10-10, by: owner, src: build, status: proposed}

## Version log
- v1.0 (2026-10-10): merged set of processes 1 to 21. Process numbers are stable. Replaces the earlier starter set.

**End of processes.md (v1.0)**
