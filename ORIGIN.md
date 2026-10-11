---
name: ORIGIN.md
internal_name: 2026-10-09-1958-origin-template
object_type: system
file_type: system
type: system (why, narrative template)
status: template
version: v1.0
date: 2026-10-09
revised: 2026-10-09-1958 PT
author: tripLr
owner: Owner
location: repository root
license: MIT
---

# Origin (template)

This file is a **template**. Fill it in with your own story, then keep it as the narrative record of why your Dragon exists and how it changed. Replace every prompt in `[brackets]`. Delete this paragraph when you are done.

## Why this exists
[What problem were you trying to solve? What were you doing when you ran into it?]
[What did you try first, and where did it break? (For example: a long chat that lost its early context, notes trapped in one app, a new AI that knew nothing about you.)]
[What did you decide you needed? Write it as one sentence.]

## The core idea
[In your own words: what lives outside the AI, and what does the AI do with it?]

## Vocabulary you adopted
| Term | What it means in your system |
|---|---|
| Object | [A file with a header, a location and edges to other files] |
| Crystal | [An index file for one folder or project] |
| [Your term] | [Its job] |

## Timeline
| Date | Event |
|---|---|
| YYYY-MM-DD | [First experiment] |
| YYYY-MM-DD | [What you changed and why] |

## Design lessons that survived
- [A rule you learned the hard way]
- [Another]

## Continuity principle
[What must still be true if your AI, your app or your storage changes?]

## Edges
up:: [[README.md]] (the why this narrative expands on) {date: YYYY-MM-DD, by: Owner, src: build, status: proposed}
mentions:: [[Dragon-Object-Schema.md]] (the rules your objects follow) {date: YYYY-MM-DD, by: Owner, src: build, status: proposed}

**End of ORIGIN.md (template)**
