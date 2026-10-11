---
name: Blank-Orb-Template.md
internal_name: 2026-10-09-2005-blank-orb-template
object_type: system
file_type: template
type: template (thin orb)
status: template
version: v1.0
date: 2026-10-09
revised: 2026-10-09-2005 PT
author: tripLr
owner: Owner
location: Dragon-Orb-History / Blank-Orb-Template.md
license: MIT
---

# Blank orb (thin)

An orb is a **minimal session review**: what happened in one session, and nothing more. It does not carry the knowledge graph; the Crystals do. Orbs are optional (see `Dragon-Object-Schema.md`, Part 10).

**To use:** copy this file to `YYYY-MM-DD-HHMM-<source>-orb.md` in `Dragon-Orb-History/`, fill it in, add a row to `Orb-History-Crystal.md`, and set `status: closed` when the session ends. Closed orbs are history and are not edited. Delete these instructions in your copy.

---

```markdown
---
name: YYYY-MM-DD-HHMM-<source>-orb.md
type: orb
status: live
date: YYYY-MM-DD
revised: YYYY-MM-DD-HHMM
author: ?
source: ?
---

# YYYY-MM-DD-HHMM <source> orb

## In hand
(What was being worked on, in one or two lines.)

## Objects touched
- (name, then read / created / changed; one line each)

## Open items
- [ ] (what is unfinished) (from [[YYYY-MM-DD-HHMM-<source>-orb]])

## Edges
- up:: [[Orb-History-Crystal.md]] (orb index) {date: YYYY-MM-DD, by: ?, src: build}
- prev:: [[previous orb name]] (previous session from the same source) {date: YYYY-MM-DD, by: ?, src: build}
- produced:: [[Object.md]] (made this session) {date: YYYY-MM-DD, by: ?, src: YYYY-MM-DD-HHMM-<source>-orb.md}

**End of YYYY-MM-DD-HHMM-<source>-orb**
```

## Edges
up:: [[Orb-History-Crystal.md]] (index that lists orbs made from this template) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
mentions:: [[Dragon-Object-Schema.md]] (Part 10: orb rules) {date: 2026-10-09, by: tripLr, src: build, status: proposed}

**End of Blank-Orb-Template.md**
