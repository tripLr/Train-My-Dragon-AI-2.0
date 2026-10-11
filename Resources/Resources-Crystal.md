---
name: Resources-Crystal.md
internal_name: YYYY-MM-DD-HHMM-Resources-Crystal
object_type: system
file_type: system
type: crystal (PARA: Resources)
status: draft
version: v0.1
date: YYYY-MM-DD
revised: YYYY-MM-DD-HHMM
author: ?
owner: Owner
license: MIT
location: Resources/
copyrighted: no
---

# Resources-Crystal

BLANK TEMPLATE. Fill in on first use. Replace every `YYYY-MM-DD` and `?`.

## Rule header (the rules for this Crystal)

These rules come from the object-creation rules in `Dragon-Object-Schema.md` (Parts 2, 3, 4, 5, 6, 7). They are copied here in short form so this Crystal works on its own.

1. **What a Crystal is.** A traversable index: a reader (human or AI) follows it to find objects instead of scanning every file. Each object also carries its own edges, so the objects together are a *distributed index*. This Crystal is the organized view over them. The graph still works if this Crystal is stale, because the links live in the objects.
2. **Backlinks.** Keep an `up::` edge to the root Crystal and cross-links (`mentions::`, `extends::`) to relevant Crystals in other areas.
3. **Continuity, drift, recovery.** Keep the table below current so a new session, or a new AI, can pick up where the last one stopped. If an object is missing from the table, or the table disagrees with the files, that is drift: say so and fix it.
4. **One row per object:** name, version, status, last touched (by whom, when), one-line summary. Rows point; they never copy bodies.
5. **Names:** the live file name is stable and carries no version. The version lives in the header. Older copies get a dated name (`YYYY-MM-DD-HHMM-<name>`) in the history folder.
6. **Writing to this Crystal (write protection):** sandbox draft, review the content and exact destination, explicit permission from the owner, write, verify by reading back.
7. **Editing an existing file is archive-first:** copy the live file into the history folder under its dated name, read the copy back, edit, write the new version under the stable name, read that back. Never overwrite without a dated copy of the old version. Superseded copies are kept; deleting anything needs the owner's named approval.
8. **Edge lines:** `type:: [[Target]] (why) {date, by, src, conf, status}`. Every edge has a type, a target by name (never an id or private URL), and a one-line reason. Use `status: proposed` until the owner approves. A contradicted edge is kept with `status: replaced` and a `replaced` date, never deleted.
9. **Edge update system (proposed):** runs only when (1) a new file or project is created, or (2) a file is renamed. Updating a file does not trigger it, because pointers use file names. It touches only what the event changed; it is not a full scan.
10. **Write-trigger review (proposed, not yet implemented):** on every file write, check that this Crystal's row, edges and backlinks were updated. **Known gap:** until that review exists, Crystals are not updated automatically. Do not claim they are.
11. **Privacy:** no passwords, tokens, file ids, or private links. Eyes-only material is marked `restricted: true` and linked by name only. Public files carry rules and generic examples only.

## Object table

| Name | Version | Status | Last touched (by, when) | One-line summary |
|---|---|---|---|---|
| Resources-Crystal.md | v0.1 | template | Owner, YYYY-MM-DD | This Crystal: the index of the Resources folder (Reference material and topics of interest) |
| Dragon-Object-Schema.md | v2.4 | live | Owner, YYYY-MM-DD | Contract: how every object is written, named, linked, archived |
| INSTALL.md | v1.1 | live | Owner, YYYY-MM-DD | How to start (honest: not install-ready) |
| *(add one row per object you put in this folder)* | | | | |

## Dragon Stack

**Role:** Index of the Resources folder: reference material and topics of interest
**Facets:** index | resources | places

### Edges

up:: [[README.md]] (root index this Crystal reports to) {date: YYYY-MM-DD, by: Owner, src: build, status: proposed}
contains:: [[Dragon-Object-Schema.md]] (the object contract lives in this folder) {date: YYYY-MM-DD, by: Owner, src: build, status: proposed}
mentions:: [[INSTALL.md]] (how to fill in and maintain this Crystal (Step 4)) {date: YYYY-MM-DD, by: Owner, src: build, status: proposed}

**Return:** README.md
**Evidence rule:** Point only. Do not copy the layer below.

## Change log (optional, append-only, newest at the bottom)

`## [YYYY-MM-DD] action | count | what`

**End of Resources-Crystal.md**
