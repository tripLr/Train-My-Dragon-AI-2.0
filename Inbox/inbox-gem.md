# Inbox Gem

**Type:** Special handling file (Inbox)  
**Status:** Live  
**Created:** 2026-08-16  
**Purpose:** Define how the Dragon Inbox works

---

## What the Inbox is

The Inbox is a catch-all holding area inside a user’s Dragon.

It exists so the human can batch-upload or drop files, notes, exports, and old thread material **as they find them**, without having to organize everything immediately.

It is temporary holding, not permanent organization.

---

## Core rules

1. Anything may be placed in the Inbox.
2. The Inbox is not the final home for durable knowledge.
3. Periodically (or when the human is ready) the Inbox is reviewed.
4. Material worth keeping is moved into the appropriate Crystal, project folder, or notes location.
5. Material that is no longer useful can be archived or removed with permission.
6. The AI must never silently reorganize or delete Inbox contents. All moves follow the Global Write Flow + WRITE / TRASH CHECK.

---

## Suggested structure

```
My-Dragon/
└── Inbox/
    ├── (dropped files and notes)
    └── inbox-gem.md   ← this file
```

---

## How an AI should treat the Inbox

- Treat it as a staging area.
- When asked to “process the Inbox” or “review what I dropped”, list the current contents and propose destinations.
- Never assume a file in the Inbox is ready for a Crystal until the human reviews it.
- Prefer small, clear batches over trying to process everything at once.

---

## Relation to Crystals and ORBs

- An ORB can be used for the working session of sorting the Inbox.
- Durable, reviewed material leaves the Inbox and enters a Crystal (or other permanent location).
- The Inbox itself does not normally need its own full project Crystal unless the human wants one.

---

## Revision Log

### 2026-08-16
- Initial Inbox Gem created for Dragon 2.0 public method.
- Supports the common need to batch-upload scattered notes and threads without immediate organization pressure.
