> Your AI is replaceable. Your knowledge system isn't.

# Train Your Dragon AI — Dragon 2.0

**External name:** README.md  
**Internal name:** 2026-08-22-1952-readme-object  
**Object type:** system  
**File type:** system  
**Type:** My-Dragon Object (Primary Project Source of Truth)  
**Status:** Live  
**Revised:** 2026-08-22-1952  
**Note:** Live rollout update — bi-directional graph rules + history location + archive-first sequence  

**A portable, model-agnostic architecture for durable human-AI work.**  
**Category:** Adaptable Project Container

---

## Why this exists

Useful AI conversations, reasoning, journaling, and project work can outlive the transient context available to any one AI instance.

Dragon keeps continuity **outside** the model so that different humans, AI systems, interfaces, and storage systems can work together without losing the knowledge system.

The two original active projects were Personal Development and Dragon training / architecture work. Personal notes are always private.

---

## Dragon Creed 2.0

A short set of weighted principles for human–AI partnership.  
These principles constrain one another. No single principle should be applied in isolation.

1. **Agency First** — The human owns the data, decisions, direction, and durable knowledge. Personal notes remain private. AI contributes speed, structure, pattern recognition, questioning, and iteration.
2. **External Continuity** — Important state and operating rules live outside any single AI instance.
3. **Challenge to Improve** — Challenge ideas to test for failure and learn from it.
4. **Trust** — Clear communication builds trust. Clarify intent, name errors, and prefer accurate output. Clear intent includes recognizing when intent has already been established by just-loaded source material.
5. **Versioned Knowledge** — Preserve the path of understanding when interpretations change.

The Creed orients the partnership. The Rule Graph (inside the Shard) makes the orientation operational.

---

## Rule Graph (summary)

Full live rules live in the Shard (Looking Glass). Summary for orientation:

1. Agency  
2. Source  
3. Output  
4. Clarify Intent  
5. Error Handling  
6. Clear Truth  
7. Write Protection — always: sandbox → review + exact destination → explicit permission → write → verify

---

## Origin

Dragon began with voice journaling during commercial trucking work.  
See `ORIGIN.md` for the full story, including the 21 August 2026 Rule Graph and the 22 August 2026 object-graph shift.

---

## Privacy & License

Personal notes are always private.  
If sensitive information must not remain on the AI side, move it to storage you control and remove it from the artifact workspace.

You are responsible for the terms of any AI you use with this system.  
MIT — see `LICENSE`.

---

## Core Drive paths

| Path | Role |
|------|------|
| `My-Dragon /` | Live system root (README, Shard, ORIGIN, INSTALL, etc.) |
| `My-Dragon / dev /` | Owner’s working and testing method for building and iterating on the container. Not required for others. Used for safe development before promoting changes to root and public repo. |
| `My-Dragon / Dragon-Orb-History /` | ORB history (anti-drift layer). Working ORBs never stay in root. |
| `My-Dragon / Dragon-Object-History /` | History for durable system Objects (non-ORB). |
| Artifact / sandbox | Ephemeral working area. Full read-write. Not durable storage. |

These paths are the operational map. The Shard carries matching definitions so any instance can orient from either file.

---

## Object Definitions

Every durable piece of the system is an **Object**.

Objects are named **Crystals**, **Shards**, **Knobs**, and **Gems**.  
These names represent layers in a personal AI hoard of linked, versioned knowledge.

An Object has:
- Stable external name
- Internal revision name when versioned (`YYYY-MM-DD-HHMM-name-object`)
- **Object type** — system | user
- **File type** — system | coursework | reference | journal | note | other
- Dragon Stack (Role · Facets · Edges · Return · Evidence rule)
- Human-readable body

**Object type**
- **system** — core architecture files (README, Shard, INSTALL, LICENSE, templates, skills infrastructure)
- **user** — coursework, journals, notes, personal reference, PD materials

**File type** describes what the file *is* (system, coursework, reference, journal, note, other).

Objects point. They do not copy the layer below.

### Object creation rule
Every Object carries:
1. A short, readable description (enough for human and AI to act without opening another file)
2. A pointer to the full treatment rule when one exists (so detail stays in one place and does not drift)
3. A small graph (Edges) — required for the Object to work

Do not replace the short description with only a pointer.  
Do not duplicate the full rule inside every Object.  
Without its graph, an Object cannot orient or link inside the hoard.

**Known system Objects**
| Object | External name | Job |
|--------|---------------|-----|
| README | `README.md` | Primary project source of truth |
| Shard | `Shard.md` | Live operating rules / AI container |
| ORB | dated file in history | Thin last-state for one window |
| Crystal | named | Durable project map |
| Opel-Knob | named | Grab-point for one week/campaign |
| Gem | named | Older query object (being replaced) |

**Revisioning**
- Live / external name stays stable
- Internal or history copies use the dated form
- Keeps GitHub and file browsers clean while preserving history

---

## Description of Dragon Stack

The Dragon Stack is a simple AI graph pointer that every durable system Object carries.

It can version:
- itself
- the information it links to
- its Edges
- its Facets

It tells both human and AI, at a glance:
- **Role** — what this Object is for
- **Facets** — the main topics or concerns it covers
- **Edges** — the explicit relationships (pointers) to other Objects
- **Return** — which Object is the home / authority for this material
- **Evidence rule** — how claims and references are handled (usually “point only, do not copy”)

The Stack is not the full content of the file.  
It is the map that sits on top so any instance can orient quickly without having to re-read the entire body.

When a new AI instance loads the system, it reads the Stack first.  
That is why the Stack appears after the Object Definitions: once you know what an Object is, the Stack shows you how this particular Object is wired.

---

## Dragon Stack

**Role:** Primary project source of truth for both human and AI. Describes what Dragon is, why it exists, and how the core processes work.  
**Facets:** purpose | creed | rules | objects | boot | process | privacy  

**Edges**

| date | kind | from | to | relation | why | status |
|---|---|---|---|---|---|---|
| 2026-08-22 | source | README | Shard.md | operating | live rules + Rule Graph | live |
| 2026-08-22 | source | README | ORIGIN.md | cites | full narrative history | live |
| 2026-08-22 | source | README | LICENSE | cites | legal | live |
| 2026-08-22 | source | README | Blank-ORB-Template.md | cites | sole blank ORB template | live |
| 2026-08-22 | source | README | INSTALL.md | cites | first-run details | live |
| 2026-08-22 | source | README | Projects / Personal-Development Crystal | downstream | PD domain | live |
| 2026-08-22 | source | README | Dragon-Orb-History | cites | ORB history location | live |
| 2026-08-22 | source | README | Dragon-Object-History | cites | object-type history location | live |
| 2026-08-22 | source | README | My-Dragon / dev / | defines | owner working / testing method for building the container | live |
| 2026-08-22 | development | README | Git-Status-Object.md | tracks | /dev working-tree status | development |
| 2026-08-22 | planned | README | Journal Crystal | planned | future object | planned |
| 2026-08-22 | planned | README | Subject graph object | planned | future object | planned |

**Return:** this README  
**Evidence rule:** Point only. Do not copy the layer below.

---

## Boot / Load Process

1. Read this README first (understand the project).
2. Load the live Shard (operating rules).
3. Check for a sandbox ORB for this window.
4. If none → load Blank-ORB-Template and review newest history ORB.
5. Once an ORB is loaded, treat it as the primary source for the rest of the window.
6. Only ask “which window / which project” when the loaded source material does not already answer the question.

**Discipline note**  
The load walk exists to reach the ORB.  
After the ORB is loaded, source material that has just been loaded outranks the generic script.  
This prevents the high-drift error of re-asking questions the ORB has already answered.

Orbs are history. System files are versions.  
Never treat an ORB as the live system.  
Never leave a working ORB in the My-Dragon root.

---

## Setup & Contribution

**Recommended starting point**  
Fork the project, then follow the container installation process using the connectors and storage you have available.

**INSTALL.md**  
INSTALL.md is primarily a testing method for AI instances.  
The intended human path is to manually install and run the container on whatever connectors and storage the user actually has.  
When an AI has direct file access, the same process may be tested there.

**Current status**  
- Issues may be reported.  
- Merge requests will be considered.  
- No formal support is offered at this point beyond sharing the method.  
- Stable milestones are uploaded when they are ready.

This is a human-owned, model-agnostic container. The public repository is the shared method; personal living data stays with the owner.

---

## Object Treatment of All Durable Files

Every durable file in My-Dragon and in Personal-Development (and other project knowledge folders) is treated as an **Object**.

**Sandbox exception**  
Ephemeral sandbox drafts stay outside the Object requirement until they are promoted.  
New information brought into the sandbox may optionally receive Object treatment as a draft (header + Source fields) so that promotion later is clean. This is optional, not required, while the material remains in sandbox.

### Required header fields (when treated as Object)
- Header (Type, Status, Revised)
- Source — how the material entered (scan, PDF, jpeg, pasted, voice, etc.)
- File location
- Name of file
- Object type — system | user
- File type — system | coursework | reference | journal | note | other
- Use — readable | voice-readable | study material | etc.
- Copyrighted — yes / no

### Edit rules
- **Non-copyrighted material** — may be edited freely.
- **Copyrighted material** — body remains full verbatim and is **not editable**.  
  Only non-copyrighted additions are allowed: headers, footers, graph links, and section markers.  
  Do not alter, paraphrase, or replace the protected body text.

### Graph and structural rules
- Graphs may point upstream to parent Objects.
- Graphs may point to internal sections of the same material (Part 1, 2, 3, etc.).
- Notes and journals created from material may link **both directions** to the source Object.
- The same bidirectional linking applies to journals and to sections within them.
- **Bi-directional graph growth (live rollout):** Edges should grow organically in both directions as Objects are touched. Reverse Edges are added incrementally during normal updates; full bi-directionality is not required in a single pass.
- **Any structural change** (including new or modified graph Edges) follows Write Protection.  
  Do not automatically create or update graph links.
- A graph Edge is a structural change to an Object. New instances load this rule via README + Shard Edge; ORBs record window activity only and do not restate the law.

---

## Durable Processes

**Source-over-script discipline**  
When a just-loaded source (ORB, Crystal, or thread review) already answers a scripted question, follow the source.  
Do not re-ask as if the situation were ambiguous.  
Name the conflict if the script and the source appear to disagree, then follow the source.

**Write Protection (Rule 7)**  
sandbox → review content + exact destination → explicit permission → write → verify  

Applies to file creation, content writes, and structural changes (including graph Edges).  
Do not automatically create or update graph links.

**Archive-first edit sequence (hard)**  
On any durable system Object edit:
1. Pull live file into sandbox as draft
2. Copy live file into the object-type history folder with dated name
3. Confirm archive exists and is readable
4. Edit the sandbox draft
5. Trash the original (trash = delete under current connectors)
6. Write new version under stable external name with updated internal HHMM revision

**History location**  
Each object type keeps history in its own history folder living next to the live objects:
- ORBs → `Dragon-Orb-History`
- Other durable Objects → `Dragon-Object-History`

**Graph discipline**
- kind: yours · insight · source · planned | development
- status flip: draft → reviewed → live
- Containers point both ways (bi-directional growth is incremental / live rollout)
- Replace, don’t orphan
- After Drive write, stamp file ID on the graph
- Check sandbox first for an existing Orb; do not spawn parallel orbs for the same window
- Do not automatically create or update graph links

**ORB as Object**
- Header + Dragon Stack + Edges table
- Date headers for knowledge/discovery sections
- Park temporary recovered value clearly
- Thin body; point instead of copy
- Full Write Protection
- Never leave working ORB in root
- Once loaded, the ORB becomes the primary source for the remainder of the window

**Skills layers**
1. Grok working + testing
2. Drive tested (dated copies)
3. Dev / staging
4. GitHub public (clean, no personal information)

**Domain separation**
- Core system skills live with the system
- Personal or project skills live under their own project folders

---

**End of 2026-08-22-1952-readme-object**  
(External name when live: README.md)
