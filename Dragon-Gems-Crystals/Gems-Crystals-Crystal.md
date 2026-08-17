# Gems-Crystals-Crystal

**Type:** Project Crystal  
**Domain:** Gems & Crystals  
**Internal Version:** 1.0  
**Status:** init  
**Created:** 2026-08-16  
**AI:** Grok  

---

## 1. Purpose

This Crystal defines what Crystals (and residual Gems) are, how they are created, named, versioned, and used.

It is the durable reference for the Crystal system itself.

## 2. Core Definition

A **Crystal** is the durable multi-session knowledge object for a project or domain.

- It holds structure, current state, harvested insights, and pointers.
- It can be loaded into an active ORB when the domain is being worked on.
- Updates return to the Crystal only after review (Global Write Flow).
- It does **not** hold live working notes (those belong in an ORB or Journal).

**Gems** were the earlier generation of this concept. New durable project knowledge should be created as Crystals.

## 3. Naming

**Drive / working copies:**  
`date-Domain-Crystal-ai.md`  
Example: `2026-08-16-Personal-Development-Crystal-Grok.md`

**GitHub / installable set:**  
Stable names.

**Versioning is internal** (header + Revision Log).

## 4. Status Values

- `init` — first version, purpose + structure
- `Live` — active and in normal use
- `Stable` — mature, rarely changing
- `Archived` — no longer active but preserved
- `Deprecated` — explicitly superseded

## 5. Relationship to ORBs

- An ORB may declare this Crystal (or any Crystal) as active for a session.
- Loading brings the current stable state (or selected sections) into the working context.
- The ORB records which Crystal was loaded and at what version/date.
- At the end of meaningful work, selected updates are reviewed and written back only with explicit permission.

## 6. Revision Log

### 2026-08-16 — v1.0 (Grok)
- Initial Crystal created during the Dragon 2.0 simplification.
