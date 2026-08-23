# Blank ORB Template

**External name:** Blank-ORB-Template.md  
**Internal name:** 2026-08-22-1857-blank-orb-template-object  
**Object type:** system  
**File type:** system  
**Type:** ORB template (single source)  
**Status:** Live  
**Revised:** 2026-08-22-1857  

**Why an ORB exists:**  
Context windows expire. Voice / truck cannot rebuild a day from chat. Work was lost that way.  
An ORB is thin last-state outside the live conversation: what was in hand, which objects were touched, what is still open.  
It is not the study and not the course.

---

## How any AI should find an existing ORB

Before creating a new one:

1. Check the **sandbox / artifacts** workspace (this AI may call it artifacts, working dir, or session files).
2. Search Drive under My-Dragon / Dragon-Orb-History for the latest dated `*-ORB*.md`.
3. If one is open for this domain, **append or update it** — do not spawn a parallel orb for the same window.
4. Terminology differs by AI. Treat “orb”, “session state”, “working memory file” as the same job.

---

## Header (fill on copy)

```
# YYYY-MM-DD-[Domain]-ORB.md

**Type:** Session ORB  
**Object type:** system  
**File type:** system  
**Date:**  
**Updated:**  
**AI:**  
**Status:** Live | Closed  
**Active knob:** (if any)  
**Active crystal(s):**  
```

---

## Dragon Stack

**Role:** today’s working map  
**Facets:** open-work | active-objects | graphs | return  

**Edges (fill):**
- → current Opel-Knob (session)
- → project Crystal (parent)
- → Shard / Looking Glass (rules)
- → Git-Status-Object (if /dev or GitHub touched)
- ← sandbox (this file may live here first)

**Return:** this ORB  
**Evidence rule:** Point only.

---

## Why this window opened

(one to three lines)

---

## In hand

- Knob:
- Crystal:
- Study journal:
- Course section (if any):

---

## Open work

- 

---

## Pointer graphs this window (by Object)

List every Object whose graph was added or changed during this window.

Format:

**Object name**
| date | kind | from | to | relation | why | status |
|------|------|------|----|----------|-----|--------|
| ...  | ...  | ...  | ...| ...      | ... | ...    |

If a file is edited and its Edges change, record the new graph rows here so the ORB stays the living map of what moved.

---

## Write-back candidates (review last)

- Crystal updates: none until reviewed
- Knob graph rows: none until reviewed
- Drive targets: name exact path when ready

---

## Close

When the window ends: update this ORB once, then stop.  
Move to Dragon-Orb-History only when the human asks or the window is clearly finished.

---

**End of Blank-ORB-Template**
