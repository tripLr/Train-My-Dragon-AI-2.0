---
name: Dragon-Object-Schema.md
internal_name: 2026-10-09-1957-dragon-object-schema
object_type: system
file_type: system
type: schema (standard for all Dragon objects)
version: v2.4
status: live           # master rule file for objects and pointers (approved 2026-10-08)
date: 2026-10-08
revised: 2026-10-09-1957 PT
author: tripLr
owner: Owner
location: Resources / Dragon-Object-Schema.md
license: MIT (same as the public repo)
supersedes: 2026-10-08-1945-dragon-object-schema (v2.3). Earlier: 2026-10-08-1835-dragon-object-schema (v2.2). Also replaces the separate Dragon-Pointer-Schema draft (deprecated, folded into Part 3). v1 had no single file; its rules were spread across README.md and Shard.md.
---

# Dragon Object Schema

The master standard for every Dragon object: header, pointers, body, naming, history, privacy, lint, and the optional orb tool. Pointer rules live here (Part 3); there is no separate pointer schema file. Standard version: see the header. The version is never in the filename.

| Part | Section | Part version |
|---|---|---|
| 1 | Scope, layers, kinds, placement | v1.3 |
| 2 | Header / frontmatter rules | v2.1 |
| 3 | Pointer rules | v1.3 |
| 4 | Body rules | v2.2 |
| 5 | Naming and versioning | v2.3 |
| 6 | History / archive-first | v2.3 |
| 7 | Privacy and public safety | v1.2 |
| 8 | Lint pass | v1.3 |
| 9 | Minimal example object | v2.1 |
| 10 | Orbs (optional, advanced) | v1.0 |
| 11 | Sources | v1.0 |
| 12 | Changelog | — |

**Version-bump rule (applies to every part and to the standard):**
- **Minor** (vX.Y → vX.Y+1): wording fixes, clarifications, or *adding* something optional: a new kind, edge type, field, or rule that nothing existing has to change for.
- **Major** (vX → vX+1): *renaming or removing* a kind, edge type, or field; making an optional item required; or changing the edge line form.
- When a part changes, bump that part, then bump the standard by the same level. Unchanged parts keep their version.
- Type lists and kind lists change only through a version bump, never mid-run.

Words: **MUST** = required. **SHOULD** = expected unless there is a reason. **MAY** = optional.

---

## 1. Scope, layers, kinds, placement (v1.3)

Every durable file in a Dragon system is an **object**. Sandbox drafts are exempt until promoted, but they MAY carry a header already so promotion is clean.

### 1.1 Layers
| Layer | What it holds | Who edits |
|---|---|---|
| **Raw** | Source captures (conversation text, transcripts, scans). Never edited after capture. | Nobody (append-only) |
| **Objects** | Orbs (optional), threads, hubs, concepts, journals, notes, skills, system files | Human, or an assistant with permission |
| **Schema** | This file and other rule files | Human decides; assistant drafts |
| **Index (Crystal)** | One Crystal per project, domain, or assistant: current version of each object, one-line summary, date, and edges | Assistant on permission |

### 1.2 Kinds
| Kind | Job |
|---|---|
| `orb` | **Optional, advanced.** A dated backup of where one working session stood, for when long threads lose context or you switch AIs. Never a live system file. See Part 10. |
| `crystal` | Durable project map and index (HEAD). Does not hold live notes. |
| `schema` | A rule file that defines how objects are written (this file is one). |
| `shard` | Live operating rules for an assistant. |
| `knob` | Grab-point for one week or campaign. Parent is a project Crystal. |
| `thread` | One object per conversation, pointing to its raw file. |
| `hub` | Map of Content for one subject. Create one at about 3 to 5 members. |
| `home` | The top hub of a project (SHOULD be one per project): links every hub, holds a running summary and the top open prompts. |
| `log` | Append-only change log for a project: one dated line per run or change (§4.3). |
| `concept` | One lasting idea, organized by concept, not by source. |
| `source` | One external source (book, paper, video, URL), so public URLs live in one place. |
| `journal` / `note` / `reference` / `coursework` | User material |
| `skill` / `template` / `system` | System material |
| `gem` | Legacy query object (being replaced by Crystals) |

### 1.3 Placement (MAY)
A PARA-style layout works well: **Projects** (active, with a goal), **Areas** (ongoing responsibilities), **Resources** (reference and interests), **Archives** (inactive). When a hub matures it MAY move from a project to an Area or Resource, leaving a pointer behind. Keep folders at most about 4 levels deep and use the same folder names everywhere.

---

## 2. Header / frontmatter rules (v2.1)

### 2.1 Form
- New objects SHOULD use YAML frontmatter between `---` lines at the top.
- The v1 bold-label block (`**Field:** value`, one per line) stays valid. Readers and lint MUST accept both. Don't mix the two forms in one file.
- YAML field names are lowercase with underscores. The bold-label form uses the same words in Title Case.
- **Nodes inside a Crystal** (an object listed as a block in an index) MAY carry header fields inline as `` `field: value` `` lines under the node name.

### 2.2 Fields
| Field | Req | Values / meaning |
|---|---|---|
| `name` | MUST | Stable external name (the filename). No version in it. |
| `internal_name` | MUST when versioned | `YYYY-MM-DD-HHMM-slug` (this revision) |
| `object_type` | MUST | `system` \| `user` |
| `file_type` | MUST | `system` \| `coursework` \| `reference` \| `journal` \| `note` \| `other` |
| `type` | MUST | A kind from §1.2, optionally followed by a short free-text label in parentheses |
| `status` | MUST | `draft` \| `proposed` \| `live` \| `closed` \| `superseded` \| `archived` |
| `version` | MUST for system objects | `vMAJOR.MINOR`. Header only. |
| `date` | MUST | The object's own date, `YYYY-MM-DD`. `node_date` is an accepted alias (common on nodes inside a Crystal). |
| `revised` | SHOULD | `YYYY-MM-DD-HHMM` of the last write; name the time zone once per system |
| `author` | MUST | Who wrote it: a name from the system's roster, or `?`. Default `by` for edges drawn from its text. |
| `owner` | SHOULD | The accountable human (a role name such as `Owner` in public files) |
| `source` | MUST for user material | How it entered: `scan` \| `pdf` \| `image` \| `pasted` \| `voice` \| `conversation` \| `web` \| `generated` |
| `source_id` | MAY | Stable id of the raw source (e.g. a conversation id) used for dedup (§6.4). Never a private URL. |
| `domain` | MAY | Short subject area label |
| `location` | SHOULD | Folder path by name (never an id or URL) |
| `use` | MAY | `readable` \| `voice-readable` \| `study` \| … |
| `copyrighted` | MUST for user material | `yes` \| `no` (see §4.4) |
| `supersedes` | SHOULD when replacing | Internal name(s) of the prior revision |
| `archived_at` | SHOULD on any object that has a superseded copy | Path + name of where the older copy lives (replaces the old `archived-in` edge) |
| `restricted` | MUST when true | `true` for eyes-only material (§7) |
| `source_hash` | MAY | Content hash for dedup and re-ingest |

Comments after `#` in YAML are allowed. Unknown fields are allowed, but lint reports them so they can be added in a schema bump or removed.

---

## 3. Pointer rules (v1.3)

This part is the only pointer rule set. The earlier standalone Dragon-Pointer-Schema draft is deprecated and folded in here.

One shared vocabulary, so every Crystal, orb, and object writes links the same way and lint can read the graph without guessing.

### 3.1 Edge line form (v1.1)
```
edge:: [[Target]] (why) {date, by, src, conf, status, replaced, valid, restricted}
```
A leading list marker (`- `) is optional; lint accepts edge lines with or without it.

| Field | Req | Meaning |
|---|---|---|
| `edge` | MUST | One type from the fixed list (§3.3–3.4) |
| `[[Target]]` | MUST | External name of the target; add a folder path only when the name is ambiguous. Never an id or private URL. For `researched` / `decided`, the target is the question or decision phrase. |
| `(why)` | MUST | One line saying why the link exists. No bare "see also" lists. |
| `date` | SHOULD | When the link was stated (the source object's date; the build date for edges a Crystal builds itself) |
| `by` | SHOULD | Who stated it (§3.6) |
| `src` | SHOULD | Where the edge was drawn from: an object name, or one keyword: `build` (made by an index build), `read` (read from storage), `conversation`, `web`, `training`. For `researched`, use `web` \| `training` \| `conversation`. |
| `conf` | MAY on any edge; SHOULD where inference was involved | Word-level confidence (§3.7). No `conf` means the edge was stated directly. |
| `status` | MAY | `proposed` (default until approved) \| `live` \| `replaced` |
| `replaced` | MUST when `status: replaced` | `YYYY-MM-DD` the edge was replaced (§3.5 rule 3) |
| `valid` | MAY | `YYYY-MM..YYYY-MM`: when the relation held in the world ("believed X until …") |
| `restricted` | MAY | `true` when the target is eyes-only |

Example:
`supersedes:: [[Old-Index.md]] (Crystal takes over the summary role, archive-first) {date: 2026-10-08, by: Owner, src: Project-Crystal.md, status: proposed}`

### 3.2 Where edges live (v1.1)
Lint accepts any of these:
- Under an `### Edges` heading inside the Dragon Stack (preferred, §4.2), or a `## Edges` heading.
- After a bold `**Edges**` label.
- Directly under a node block inside a Crystal (after the node's inline fields).

v1 Edge tables (`| date | kind | from | to | relation | why | status |`) stay readable. Convert them on the next archive-first edit using §3.8.

### 3.3 Core 18 types (v1.0, unchanged)
Write the forward type only. Lint infers the inverse. An object MAY have more than one `up` (a thread can sit under several hubs).

| # | Type | Meaning | Inverse (lint) |
|---|---|---|---|
| 1 | `up` | Parent hub, Crystal, or rule file | `down` |
| 2 | `part-of` | Member of a series or collection (a course day or week when the object *is* course material). Not a topic. | `has-part` |
| 3 | `prev` | Item just before in time (`next` is inferred) | `next` |
| 4 | `supersedes` | Newer version replaces an older one; old copy kept | `superseded-by` |
| 5 | `twin-of` | Same content in two places (backup or exact duplicate) | symmetric |
| 6 | `derived-from` | Made from this source in whole or part (object from raw, merge, transcript) | `derivation` |
| 7 | `about` | Main subject | `subject-of` |
| 8 | `uses-method` | Applies this method or practice | `method-used-in` |
| 9 | `echoes` | Symmetric "related": same idea, no hierarchy | symmetric |
| 10 | `extends` | Builds on or continues | `extended-by` |
| 11 | `contradicts` | Reaches the opposite claim. Keep both sides. | `contradicted-by` |
| 12 | `supports` | Gives evidence or reasons for | `supported-by` |
| 13 | `researched` | What was asked or looked up (the question, never the answer) | — |
| 14 | `cites` | External source used; point at a `source` object | `cited-by` |
| 15 | `course-link` | Course session or week this session belongs to (if the object *is* course material, use `part-of`) | `course-content` |
| 16 | `person` | Person or agent involved | `appears-in` |
| 17 | `journal-of` | Dated journal entry this came from or fed | `journal-for` |
| 18 | `produced` | File or output created in the session | `produced-by` |

### 3.4 Optional, dropped, and not-adopted types (v1.1)
**Optional** (only where content clearly supports them):

| Type | Meaning | Inverse |
|---|---|---|
| `mentions` | Passing reference, not the subject. Also Crystal-to-Crystal "should use" pointers. | `mentioned-in` |
| `questions` | Raises an open question about | `questioned-by` |
| `answers` | Answers a question or prompt | `answered-by` |
| `decided` | A decision taken (target = decision phrase or affected item) | `decided-in` |
| `blocked-by` | Can't proceed until target is done | `blocks` |
| `example-of` | Concrete instance of a general pattern | `has-example` |
| `branches-from` | Side thread that starts from one point in another note | `has-branch` |
| `merged-into` | Dedup stubs only: folded into a survivor | survivor `supersedes` |

**Dropped / moved:** `holds` → split into `about` / `uses-method` / `researched` / `produced`. `feeds` → `up`. `replaces` → `supersedes`. `moves-to` → a move-list file, never an edge. `archived-in` → header field `archived_at`. Open actions → task lines `- [ ] … (from [[Object]])`, not edges. No negative (`-edge::`) prefix; use `contradicts`.

**Considered, not adopted** (use the mapping instead of inventing the type): `continues` → `extends` · `responds-to` → `answers` or `extends` · `version-of` → `supersedes` · `quoted-from` → `derived-from` · `defines` → `about` · `refines` → `extends` · `disputes` → `contradicts` or `questions` · `evolution-of` → `supersedes` + `contradicts` · `source` / `data-from` / `background` → `cites` · `voice-of` / `endorses` → the `by` field · `indexed-in` → `up` · `same` / `sibling` → inferred from a shared `up` · `todo` → task line.

### 3.5 Pointer rules (v1.1)
1. **Fixed type list per run.** Use only §3.3–3.4. Anything that doesn't fit is reported as unmapped. New types arrive only through a version bump (see the version-bump rule at the top).
2. **One direction only.** Write the forward edge on the newer or child object. Lint infers inverses. Don't hand-write `down`, `next`, `superseded-by`, etc.
3. **Never delete a contradicted edge.** Keep it, set `status: replaced` **and** `replaced: YYYY-MM-DD` (both, always), and add the new edge beside it. Changes of mind stay visible.
4. **Record who said it.** Every edge SHOULD carry `by`. Use `?` rather than guess.
5. **Names and paths only.** No file ids, no passwords or passphrases, and no URLs except public ones inside `source` objects.
6. **Propose first.** New edges on live objects carry `status: proposed` until the owner approves; then they are applied archive-first (§6). Edges are structural changes and are never auto-written.
7. **Keep it readable.** The `(why)` must make sense as a sentence on its own.

### 3.6 `by`: who said it (v1.1)
- Value: a name from the system's roster, or `?` (unknown or not on the roster). `author` (§2.2) uses the same roster.
- Each system keeps its roster in a private instance file. Public files use role names (`Owner`, `Assistant`).
- **Role-aware trust:** when claims conflict, the owner's statement outranks an assistant's. An assistant's inference never overwrites an owner edge; it is added beside it with `conf`.
- **Decisions** (`decided`) default to `by: <owner>` with `conf: likely` unless the source names the decider.

### 3.7 `conf`: word-level confidence (v1.1)
Words, not numbers (numeric model "strength" scores proved arbitrary in practice).

| Word | Use when |
|---|---|
| `confirmed` | Stated directly by the owner, or read verbatim from the source |
| `likely` | Inferred with good support (name, date, size, or content match) |
| `guess` | Weak inference; needs a human check |

Leaving `conf` off means "stated directly", the same as `confirmed`. Legacy `high` / `med` / `low` read as `confirmed` / `likely` / `guess`; lint flags `high` on an inferred edge for review, since by meaning it is usually `likely`.

### 3.8 v1 Edge-table mapping (v1.1)
| v1 table value | v2 edge |
|---|---|
| kind `under`; relation `operating` | `up` |
| relation `source` | `derived-from` (or `mentions` if it is only read, not built from) |
| relation `cites` | `cites` (external) or `mentions` (internal) |
| relation `downstream` | write `up` on the child instead |
| relation `tracks`; kind `pointer` | `mentions` |
| relation `defines` | `about` |
| kind `planned` | edge with `status: proposed` |
| kind `prior` | `supersedes` (on the newer object) |
| kind `sideways` | `echoes` |
| kind `contains` | `location` header field, not an edge |
| `related` | `echoes` (or `mentions` for a passing reference) |
| `governed-by` | `up` (a rule file is a valid `up`) |
| `inherits` | `up` (rules) or `extends` (builds on) |
| `indexed-by` | write `up` on the child object instead |

---

## 4. Body rules (v2.2)

### 4.1 Order
1. Title line (`# Name`)
2. Short readable description: enough for a human or an assistant to act without opening another file
3. **Dragon Stack** (§4.2)
4. Body sections for the kind (§4.3)
5. End line: `**End of <internal_name>**`

### 4.2 Dragon Stack (v2.1)
Every durable object carries it, right after the description, in this order: Role, Facets, Edges, Return, Evidence rule.

```
## Dragon Stack
**Role:** what this object is for
**Facets:** topic | topic | topic
### Edges
up:: [[Parent]] (why) {…}
**Return:** the object that is the home or authority for this material
**Evidence rule:** Point only. Do not copy the layer below.
```

An object without edges can't orient or link and fails lint.

### 4.3 Kind templates (v2.1)
- **Orb:** see Part 10 (optional tool).
- **Thread:** Summary · Key ideas · Quotes (speaker marked) · Owner's insights · Open questions · Answer provenance (each answer tagged `web` \| `training` \| `conversation`) · Journal prompts (SHOULD be 2–3) · Research prompts (SHOULD be 2–3). One thread per conversation; when it grows, append `## Continued YYYY-MM-DD` and bump the version, never a second object.
- **Hub:** One-paragraph synthesis of current thinking · Members (one line each) · Open prompts collected from members as tasks.
- **Home:** Running summary · Links to every hub · Top open prompts (about 5).
- **Crystal:** Rule header (the rules for that project) · Object table (name, version, status, last touched by and when, one-line summary) · Edges · optional Change log section. Each Crystal SHOULD also carry an **anchor** (an edge or line naming the rule file, by name + folder) and **side links** (`echoes`) to its peer Crystals, so a reader starting at any Crystal can reach the rules and its neighbours without climbing to the root.
- **Log:** Append-only, newest at the bottom, one line per run or change: `## [YYYY-MM-DD] action | count | what`. Never edit past lines; correct with a new line.
- **Journal / note:** Free body; date headers for discovery sections.

### 4.4 Content rules (v2.1)
1. **Point, don't copy.** Link to the layer below; don't restate it.
2. **Description plus pointer.** Give a short description and a pointer to the full rule; never only one of the two.
3. **Copyrighted material:** the body stays full verbatim and is not editable. Only headers, footers, edges, and section markers may be added.
4. **Prompts stay alive:** prompts are task lines `- [ ] prompt (from [[Object]])`. When answered, the answer gets a `journal-of` or `answers` edge back and the task is checked.
5. **Speakers marked:** quotes say who said them (owner, assistant, or third party).
6. **Mixed content:** flag off-topic parts in place rather than splitting the object.

---

## 5. Naming and versioning (v2.3)

1. **Live filename is stable and carries no version:** `Shard.md`, `Project-Crystal.md`, `Dragon-Object-Schema.md`.
2. **Version lives in the header** (`version`, `revised`, `internal_name`); per-part versions live inside the file, as in this one.
3. **History copies are dated:** `YYYY-MM-DD-HHMM-<name>` (e.g. `2026-10-08-1830-Dragon-Object-Schema.md`).
4. **Dated objects** (orbs, journals, threads) carry the date in the name because the date is their identity: `YYYY-MM-DD-HHMM-<source>-orb.md` (§10.4), `YYYY-MM-DD-<slug>.md`. The compact form `YYYYMMDD-HHMM-<slug>` is also accepted. Add a short discriminator (`a`/`b`) only when two sessions share a name.
5. **Prefixes** MAY mark kinds: `HUB_`, `CONCEPT_`, `SRC_`, `RAW_`. Review files use `DRAFT-` / `REVIEW-` and never become live under that name. `PRIVATE-` marks a file that is **never public**.
6. **Versions** are `vMAJOR.MINOR`, bumped by the version-bump rule at the top of this file.
7. **Source tag (MAY):** content that came from another app MAY carry a short source tag in its name (for example `-OtherApp`), so its origin is visible without opening it.

---

## 6. History / archive-first (v2.3)

### 6.1 Write protection
Every durable write (file creation, content edit, edge change) follows:
`sandbox draft → review content + exact destination → explicit permission → write → verify`

### 6.2 Archive-first edit sequence
1. Pull the live file into the sandbox as the draft base.
2. Copy the live file into the object kind's history folder under its dated name (§5.3).
3. Read the archive back and confirm it is complete (for example, its size matches the live file).
4. Edit the draft; update `version`, `revised`, `internal_name`, and `supersedes`.
5. Write the new version under the stable external name (overwrite in place where storage allows; otherwise replace the original only after step 3 passed).
6. Read the new live file back and confirm it matches the draft.

### 6.3 History rules
- Each object kind keeps history in its own history folder next to the live objects (e.g. object history). Orbs live in the instance's single orb home folder (§10.5).
- Superseded copies are kept, never silently deleted. Deleting anything needs the owner's explicit, named approval.
- Duplicates are parked (moved to history with a `twin-of` or `merged-into` note) before any trash decision.
- An orb never stays in the system root.

### 6.4 Dedup and merge
1. One thread per conversation, keyed by `source_id` when there is one.
2. Before making a hub or concept, search the Crystal for the name or a synonym; add to the existing one if found.
3. When two objects cover one idea, the older survives. The other becomes a stub with `merged-into::`, and its old text goes to history.
4. Conflicting ideas are not merged. They get a `contradicts::` edge.
5. A manifest (`source_id, date, source_hash, object version, status`) MAY track raw → object so re-runs touch only what changed. Re-ingest appends new material and keeps existing edits.

---

## 7. Privacy and public safety (v1.2)

1. Personal notes are always private. Public files carry rules and generic examples only.
2. **Eyes-only material:** set `restricted: true`. Link it by name only and never copy its content into any other object.
3. Other personal material (health, family, finances, address) stays at topic level in shared objects.
4. **Never in any object:** passwords, passphrases, tokens, social security or account numbers, file ids used as keys, or URLs to private files.
5. **Instance split:** a public schema stays generic. The owner's real folder paths, Crystal list, roster, and restricted-item list live in a `PRIVATE-` instance file that points `up` to this schema.
6. **Publish single files, never folders.** Push only the named public file. Draft, review, and `PRIVATE-` files never leave private storage.
7. Before anything goes public, run the public-safety lint check (§8, check 9).

---

## 8. Lint pass (v1.3)

Run on a schedule (weekly is a good default) and before any public release. Lint **reports**; it never writes. Fixes are proposed and applied archive-first on approval. Output: one report file, `REVIEW-lint-YYYY-MM-DD.md`.

| # | Check |
|---|---|
| 1 | Header: required fields present; values in range (`status`, `type` kind, `version` form); no version in the live filename |
| 2 | Edge form: matches §3.1 (bulleted or not, in any §3.2 location); `(why)` present; type in the fixed list (else "unmapped") |
| 3 | Edge values: `by` / `author` on the roster or `?`; `conf` in the allowed words (legacy words noted); `status: replaced` has `replaced:` |
| 4 | Inverses: build the inferred inverse set; flag any hand-written inverse |
| 5 | Contradictions: `contradicts` pairs listed; replaced edges kept and dated, none deleted |
| 6 | Orphans: objects with no `up`; subjects mentioned 3+ times without a hub (suggest one) |
| 7 | Broken pointers: targets that don't resolve by name or path; ambiguous names needing a path |
| 8 | Twins and dedup: same name in one folder, same hash in two places, stubs missing `merged-into`, two threads with one `source_id` |
| 9 | Public safety: ids, private URLs, secrets, restricted content, or personal names and folders in a file meant to be public |
| 10 | Stale index: Crystal rows whose version or date doesn't match the live object; superseded objects without `archived_at` |
| 11 | Stale claims: `valid` ranges that have ended, and old claims never revisited |
| 12 | Archive candidates (suggest only): objects untouched for a long time or fully superseded, each with a proposed archive note. Never a delete. |
| 13 | Orbs (only if the instance uses them): filename carries its source (§10.4); file sits in the orb home folder; every orb has a row in the Orb-History Crystal and every row resolves to a file |
| 14 | Crystals (suggest only): missing anchor to the rule file, or no side links to peer Crystals |

---

## 9. Minimal example object (v2.1)

```markdown
---
name: 2026-10-08-1405-Example-Thread.md
internal_name: 2026-10-08-1405-example-thread
object_type: user
file_type: note
type: thread
status: proposed
version: v1.0
date: 2026-10-08
author: Assistant
owner: Owner
source: conversation
source_id: example-conversation-001
location: Projects / Example-Project / Threads
copyrighted: no
---

# Example Thread: patience as a skill

Summary of one conversation about treating patience as a trainable skill. Full text is in the raw file.

## Dragon Stack
**Role:** thread object for one conversation
**Facets:** patience | habits
### Edges
- up:: [[HUB_Habits]] (main subject hub) {date: 2026-10-08, by: Assistant, src: 2026-10-08-1405-Example-Thread.md, status: proposed}
- derived-from:: [[RAW_2026-10-08-1405-Example-Thread]] (full conversation text) {date: 2026-10-08, by: Assistant, src: RAW_2026-10-08-1405-Example-Thread}
- prev:: [[2026-10-01-0900-Example-Thread]] (earlier talk on the same topic) {date: 2026-10-08, by: Assistant, src: build, conf: likely}
- about:: [[CONCEPT_Patience]] (core topic, named by the owner) {date: 2026-10-08, by: Owner, src: 2026-10-08-1405-Example-Thread.md}
- contradicts:: [[CONCEPT_Patience-Is-Fixed]] (now sees it as trainable) {date: 2026-10-08, by: Owner, src: 2026-10-08-1405-Example-Thread.md}
- supports:: [[CONCEPT_Patience-Is-Fixed]] (earlier view) {date: 2026-09-20, by: Owner, src: 2026-09-20-0800-Example-Thread.md, status: replaced, replaced: 2026-10-08}
**Return:** HUB_Habits
**Evidence rule:** Point only. Do not copy the layer below.

## Key ideas
- Patience improves with deliberate practice.

## Answer provenance
| Answer | Provenance |
|---|---|
| Practice schedule suggestion | training |

## Journal prompts
- [ ] Where did I practice patience this week? (from [[2026-10-08-1405-Example-Thread]])
- [ ] What made waiting harder today? (from [[2026-10-08-1405-Example-Thread]])

## Research prompts
- [ ] What does habit research say about practicing patience? (from [[2026-10-08-1405-Example-Thread]])
- [ ] Which methods train delayed gratification in adults? (from [[2026-10-08-1405-Example-Thread]])

**End of 2026-10-08-1405-example-thread**
```

---

## 10. Orbs (optional, advanced) (v1.0)

### 10.1 Why orbs exist
**If your long threads lose context, or you switch AIs, use this tool.**

Long AI conversations forget their early parts, and a different AI starts with nothing. An orb is a small dated file, kept in your own storage, that records where a session stood: what was in hand, which objects were touched, and what is still open. The next session (same AI or a different one) reads the newest orb and picks up without you re-explaining. It is also an accountability record: what was done, by whom, and what changed.

### 10.2 Optional and advanced
- Orbs are **optional**. A Dragon works without them; Crystals, threads, and journals don't depend on them.
- They are an **advanced** tool. Start using them when you notice context loss, run very long threads, or work across more than one AI.
- An orb is a backup and a pointer map, not the study, the journal, or a live system file. It points to objects; it doesn't copy them.

### 10.3 Structure
Header (§2) plus five sections, in this order:

| Section | What goes in it |
|---|---|
| Header | `name`, `type: orb`, `status: live \| closed`, `date`, `revised`, `author`, `source` (the bot, project, or journal the session belongs to), optional `restricted` |
| In hand | What was being worked on: the project, Crystal, document, or question that was open |
| Objects touched | Each object read, created, or changed, one line each, by name |
| Open items | What is unfinished, as task lines `- [ ] … (from [[orb name]])` |
| Edges | `up::` the Orb-History Crystal; `prev::` the previous orb from the same source; `produced::` / `mentions::` for objects touched |

Optional extras: why the session opened, signs of drift or context loss, rule changes made this session.

### 10.4 Naming
- `YYYY-MM-DD-HHMM-<source>-orb.md`. The `<source>` names where the session came from: an assistant's name, a project name, a journal, etc.
- Examples: `2026-10-08-1405-Assistant-orb.md`, `2026-10-08-1405-Example-Project-orb.md`, `2026-10-08-2100-Journal-orb.md`.
- The compact date form (`YYYYMMDD-HHMM-<source>-orb.md`) and older `-ORB.md` names are accepted.

### 10.5 Home and index
- **One orb home folder per instance.** All orbs live there, never in the system root.
- An **Orb-History Crystal** in that folder indexes every orb: name, date, source, status, and a one-line summary, newest first.
- New orbs are added to the Crystal on the same write, archive-first like any object.

### 10.6 Rules
1. One orb per session per source. If one is already open for this session, update it; don't start a parallel one.
2. Write or update it at the end of a session, before a thread gets very long, and before switching AIs. Once per session is usually enough.
3. To resume, read the newest orb for that source first; once loaded it outranks generic start-up steps.
4. Close it (`status: closed`) when the session ends. Closed orbs are history and aren't edited.
5. Privacy rules (§7) apply in full: no secrets, restricted material by name only.

### 10.7 Minimal orb
```markdown
---
name: 2026-10-08-1405-Example-Project-orb.md
type: orb
status: closed
date: 2026-10-08
revised: 2026-10-08-1530
author: Assistant
source: Example-Project
---

# 2026-10-08-1405 Example-Project orb

## In hand
Drafting the project's reading list.

## Objects touched
- Example-Project-Crystal.md (read)
- Reading-List.md (created)

## Open items
- [ ] Add three more sources to Reading-List.md (from [[2026-10-08-1405-Example-Project-orb]])

## Edges
- up:: [[Orb-History-Crystal.md]] (orb index) {date: 2026-10-08, by: Assistant, src: build}
- prev:: [[2026-10-06-0900-Example-Project-orb.md]] (previous session) {date: 2026-10-08, by: Assistant, src: build}
- produced:: [[Reading-List.md]] (made this session) {date: 2026-10-08, by: Assistant, src: 2026-10-08-1405-Example-Project-orb.md}

**End of 2026-10-08-1405-Example-Project-orb**
```

---

## 11. Sources (v1.0)

Public sources these rules draw on (public URLs listed once, per the `source` rule):

| Source | Used for |
|---|---|
| Karpathy, "LLM Wiki": https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f | Raw / objects / schema layers, index, append-only log, lint pass |
| Breadcrumbs (Obsidian): https://breadcrumbs-docs.michaelpporter.com/edge-fields/ | `up` / `prev`, one direction with implied inverses |
| Typed Graph (Obsidian): https://community.obsidian.md/plugins/typed-graph | `type:: [[Target]] {props}` edge form |
| Andy Matuschak, Evergreen notes: https://notes.andymatuschak.org/zF8xCU4BwXwbmSyp7tmff9i | Concept-oriented notes; a reason on every link |
| Nick Milo, Maps of Content: https://notes.linkingyourthinking.com/Cards/MOCs+Overview | Hubs and home note |
| Tiago Forte, PARA: https://fortelabs.com/blog/para/ | Placement (§1.3) |
| SKOS Reference: https://www.w3.org/TR/skos-reference/ | `up` / `echoes` (broader / related) |
| DCMI Metadata Terms: https://www.dublincore.org/specifications/dublin-core/dcmi-terms/ | `part-of`, `supersedes`, `derived-from` |
| PROV-O: https://www.w3.org/TR/prov-o/ | `derived-from`, `twin-of`, `produced`, provenance |
| CiTO: https://sparontologies.github.io/cito/current/cito.html | `cites`, `supports`, `extends`, `uses-method` |
| IBIS vocabulary: https://vocab.methodandstructure.com/ibis | `questions`, `answers`, `supports`, `contradicts` |
| Graphiti / Zep: https://help.getzep.com/facts | Never delete contradicted edges; validity time |
| obsidian-kg-forge: https://github.com/Jimmycarroll2021/obsidian-kg-forge | Source, confidence, and timestamp on every edge |
| personal-temporal-knowledge-graph: https://github.com/vsevolodnedora/personal-temporal-knowledge-graph | Owner-over-assistant trust |
| Microsoft GraphRAG: https://microsoft.github.io/graphrag/index/outputs/ | Words, not numeric strength scores |

---

## 12. Changelog

**v2.4 (2026-10-09, live)**
- Cosmetic (1957): end marker and internal name corrected to this revision (the 1955 first write still carried the v2.3 end marker). No rule changed.
- Part 1 → v1.3: Crystal index may be per assistant as well as per project or domain.
- Part 3 → v1.3: §3.8 maps more foreign edge words (`related`, `governed-by`, `inherits`, `indexed-by`) onto the fixed list. No new edge types.
- Part 4 → v2.2: Crystal template adds an anchor to the rule file and side links to peer Crystals (SHOULD).
- Part 5 → v2.3: optional source tag in names for content from another app.
- Part 6 → v2.3: archive read-back may compare size.
- Part 7 → v1.2: social security and account numbers added to the never-in-any-object list.
- Part 8 → v1.3: check 14 for Crystal anchor and side links (suggest only).
- All additions are optional or SHOULD; nothing existing becomes required, so this is a minor bump.

**v2.3 (2026-10-08, live)**
- This file is now the master rule file for objects and pointers (`status: live`).
- Part 3 → v1.2: states it is the only pointer rule set. Dragon-Pointer-Schema (standalone draft v1) is **deprecated and folded into Part 3**; its old copy is kept in history only.

**v2.2 (2026-10-08, draft)**
- Part 10 v1.0 (new): Orbs as an optional, advanced tool: why they exist ("if your long threads lose context, or you switch AIs, use this tool"), structure (header, in hand, objects touched, open items, edges), naming `YYYY-MM-DD-HHMM-<source>-orb.md`, one orb home folder per instance indexed by an Orb-History Crystal, rules, and a minimal orb.
- Part 1 → v1.2: `orb` kind marked optional/advanced; ORB template moved to Part 10.
- Part 5 → v2.2: orb naming carries its source.
- Part 6 → v2.2: orbs live in the orb home folder.
- Part 8 → v1.2: orb check (source in name, home folder, Crystal row).
- Sources renumbered to Part 11 and Changelog to Part 12 (content unchanged).

**v2.1 (2026-10-08, draft)**
- Part 1 → v1.1: added `schema`, `home`, and `log` kinds; added PARA placement (MAY).
- Part 2 → v2.1: header now obeys its own rules (`version`, `status: draft`, `revised`, `owner`, `location`); `node_date` accepted as an alias of `date`; added `source_id` and `domain`; inline fields allowed for nodes inside a Crystal.
- Part 3 → v1.1: `conf` MAY on any edge, SHOULD where inferred (fixes a contradiction); kept the high/med/low equivalence with a lint flag for `high`; `status: replaced` and `replaced:` always paired; added `valid` and `restricted` to the line form; `src` keywords; bulleted and unbulleted edges and three edge locations accepted; multiple `up` allowed; decision default for `by`; no negative-prefix edges; considered-but-not-adopted list; legacy map fixed (`source` → `derived-from`, added `pointer` → `mentions`). Core 18 unchanged.
- Part 4 → v2.1: Dragon Stack order fixed (`### Edges` inside the stack); answer provenance and 2–3 prompts on threads; home and log templates; Crystal change log section.
- Part 5 → v2.1: `PRIVATE-` prefix (never public); compact `YYYYMMDD-HHMM` date form accepted; one version-bump rule for the whole file.
- Part 6 → v2.1: dedup keyed by `source_id`; re-ingest appends and keeps edits.
- Part 7 → v1.1: publish single files, never folders.
- Part 8 → v1.1: roster / conf / replaced value check; stale-claim check; archive-candidate check (suggest only).
- Part 9 → v2.1: example follows the fixed rules (bulleted edges, real `src`, no `conf` on stated edges, provenance, prompts).
- Part 10 v1.0: new Sources part (renumbered to Part 11 in v2.2).

**v2.0 (2026-10-08, draft):** first standalone schema. Parts 2, 4, 5, 6, 9 at v2.0 (carried over from v1 and revised); parts 1, 3, 7, 8 new at v1.0. Added YAML frontmatter, the edge line form and fixed type list, one-direction edges, never-delete contradictions, `by`, word confidence, `archived_at`, names-and-paths-only (dropped v1 "stamp file ID"), archive-first with read-back (no trash step), dedup, privacy, and lint.

**v1 (Aug 2026):** object definitions, header fields, copyright edit rules, Edge tables, archive-first sequence, and history locations, published in the public repo's README.md and Shard.md.

**End of 2026-10-09-1957-dragon-object-schema**
