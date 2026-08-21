# Context Window, Voice, and the ORB

**Train Your Dragon AI**  
**Author:** Matt (tripLr)  
**Date:** 2026-08-21  
**Companion:** `ORIGIN.md`  
**Staged from:** `My-Dragon/dev/2026-08-21_Context-Window-and-ORB-Report.md`

This is a field report, not a product claim. It records what a long voice-and-text development session actually did to an AI context window, and why an external last-state file (the ORB) became the recovery method.

Do not assume any AI has complete access to a user’s full session — in text or in voice.

---

## Why this exists

`ORIGIN.md` already tells the first necessity: truck-driving time, voice journaling, and the fact that a conversation is not a filing cabinet.

This report is the later measurement.

A hunch that the context window was failing on a very long AI-development thread was tested in one Grok window on 2026-08-21 (Android app: Ask / Imagine / Build). The window began at Shard v4.3 with an empty sandbox and ended the same day at Shard v4.8 with Drive writes, a domain Crystal, and an updated ORB.

The hunch was correct. The stores were not one store.

---

## Four stores, not one

| Store | What it actually is |
|---|---|
| Phone chat history | Complete in the app. The screen cache is smaller than the history. Scrolling to the first message required several refresh spins. |
| App file store | Uploads in Ask remain visible in Build. Bytes can still be there after the model no longer knows the file exists. |
| Context window | The budgeted working set the model can reason over this turn. Compaction and drop happen here. |
| Durable files (Drive, GitHub, ORB, Crystal) | What survives after the window forgets. |

Calling the context window “live memory” is false. It is a budget. It shrinks.

xAI’s API documents **context compaction**: prior turns can be shrunk into a salient record; verbose tool output is dropped. Compaction cannot rescue a request that is already over the limit. The consumer app does not publish that same spec. This session showed the working set as **start + compressed middle + recent turns**, not a full transcript.

---

## Limits found in this window

### 1. Display cache ≠ history

The first user turn was still in the phone history. The UI would not show it until the cache loaded more chunks. The model’s start of the window matched that first turn. The scroll limit was the screen, not a second conversation.

### 2. Context window compaction

A long development day does not stay fully addressable. Exact wording from the middle is the first to go. Last-state must live outside the chat.

### 3. Voice is not the same Spec-Lens as text

Voice can share the thread and still lack tools (Google Drive in this session). A voice pass is not a promise of the same connectors. Switching back to text does not automatically restore voice wording that never entered the text context.

### 4. Uploaded files expire from the window, not from the app

Ask-mode uploads can remain in Build storage. Once they leave the context window they are not working files. They become working files again only if something **points** at them and they are reloaded.

### 5. Ask / Imagine / Build

Same app, different working sets. Storage in Build does not put knowledge back into Ask’s context window.

### 6. Same-name Drive writes create ghosts

The connector can upload, download, list, trash. It cannot move a file to a new parent. “Move” is **copy-then-trash** (new ID in the target; old ID in trash). Uploading `Shard.md` beside an existing `Shard.md` makes two files. The first 4.8 upload in this window used the wrong local body. The wrong copies were trashed. The second write was verified.

### 7. “Latest” is the wrong window

More than one ORB can exist on the same day. Loading “the latest” can load a different window. Boot must ask **which window**.

---

## How the ORB overcame it

The ORB is not memory. It is **last-state for one window**.

Process that held:

1. Draft in the sandbox.  
2. Name type, source, target, and action. Wait.  
3. Write only after that confirm.  
4. Keep a thin ORB: position, pointers, open work. Do not copy journals into it.  
5. Point at Crystals and journals. Reload when the window has forgotten them.  
6. History backups use a unique stamp. Live system files keep a stable name (`Shard.md`).  
7. No Status line on Drive files. Sandbox = working copy. Filename date + version + Revised clock.

A file is a working file only while something still points at it.

That is why a long project is possible: the conversation is an interface. The Hoard is the files. The ORB is how this window finds them again after the context window compresses.

---

## Rule for any user, any model

Do not assume the AI can see:

- the full scrollback  
- the voice transcript after a mode switch  
- an uploaded file that is still in the app  
- Drive or GitHub because text mode once could  
- “the latest” file as this window’s file  

Assume a **context window**. Keep last-state outside it.

---

## Where this belongs

- Public story and architecture: `ORIGIN.md`  
- This measurement: a dated report next to it  
- Operating rules: `Shard.md` (Looking Glass)  
- Session last-state: the current ORB (not public)

Personal journals stay private.

---

**End of report — 2026-08-21**
