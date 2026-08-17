# INSTALL.md — Dragon 2.0 (Detailed)

**A human-owned method for continuous AI work across instances, models, and storage locations.**

This file is both an installation guide and the first education layer.  
It assumes the user may not have read the README, ORIGIN, or Creed in full.

---

## 1. Why Dragon exists (read this first)

The creator wanted complete agency over his AI experience.  
He did not want to depend on any single subscription, server, model, or company’s limitations.

He needed a versioned knowledge layer that belonged to him and could grow over time.

Necessity drove the design.  
Long hours of personal-development training and journaling had to happen while also spending long hours driving a commercial truck. Reading and writing while driving was not possible. Voice became essential.

He also discovered instance limitations: long conversations lost earlier context, insights became trapped, and starting a new AI instance meant teaching everything again.

Instead of waiting for someone else to solve it, the driver and an AI began building Dragon — a system that keeps continuity and durable knowledge under human ownership, outside any single AI.

---

## 2. Critical rules before any work begins

### Agency
You own your data, your decisions, and your direction.  
The AI is a collaborator, not the owner.

### Global Write Flow (mandatory)
1. Draft in the local artifact workspace  
2. Review the **content** and the **exact destination** with you  
3. Obtain your explicit permission  
4. Perform the write  
5. Verify when possible  

The AI must never silently change system files or project files.

### Permission drift is dangerous
If the AI stops following the write permissions above, that is permission drift.  
It is a serious threat to project integrity and can lead to unauthorized overwrites.  
Surface it immediately.

### Context drift
You (the human) may notice context loss before the AI does.  
A practical check: review the earliest prompts and material the AI can still see.  
When early context disappears, the context window limit has been reached.  
This is one reason the ORB exists.

### Privacy and sensitive information
- Personal notes are always private.
- An ORB is optional.
- If you put sensitive information (including anything that may fall under privacy or health rules) into a session, move those files into storage you control and delete them from the temporary artifact workspace.
- You are responsible for reviewing the license and terms of any AI you use with this system. Those terms can be broad about data use, retention, and sharing.

---

## 3. The core objects (short definitions)

**Shard**  
The AI-agnostic boot layer and knowledge contract.  
It tells any AI how you want it to behave and where your files live.  
You may edit it. The AI cannot change it without permission.

**Looking Glass**  
A section inside the Shard.  
It holds the high-level interaction contract (agency, write flow, relationship between working and durable knowledge).

**Ocular**  
How you send and receive information (voice, text, hands-free, interruption patterns, accessibility needs).

**Spec-Lens**  
What a particular AI or environment can actually see and do, including observed limits.  
A new or special Spec-Lens may be created when needed.

**ORB**  
An external working file that lives outside the live conversation.  
- Starts in session artifacts  
- A blank one can be provided on install  
- Optional but important for continuity, versioning, and revealing limits  
- Only needs updating once in a while  
- Can later feed Crystals  
- Saved into your My-Dragon history  
- Can contain conversations, summaries, sources, and links you request  

**Crystal**  
The durable multi-session knowledge object for a project or domain.  
- Can be loaded into an active ORB  
- Updates only after review and permission  
- Status values: init | Live | Stable | Archived | Deprecated  
- Does not hold live working notes  

All parts of Dragon are versioned and linkable.

---

## 4. Minimum install set

Copy these files into a location you control:

| File | Purpose |
|------|---------|
| `Shard.md` | Boot layer + operating contract |
| `README.md` | Overview + privacy + structure |
| `ORIGIN.md` | Full story |
| `Dragon-Creed-2.0.md` | Values layer |
| `INSTALL.md` | This file |
| `LICENSE` | MIT |

Recommended folders (with their init Crystals):

- `Dragon-Gems-Crystals/`
- `Dragon-Orbs/`
- `Dragon-Lenses/`
- `Dragon-Skills/`
- `Dragon-Structure/`

---

## 5. First-run sequence (voice-friendly)

An AI should walk a new user through these steps, pausing for confirmation:

1. Tell the origin story (Section 1 above).
2. State agency and the Global Write Flow.
3. Explain privacy, sensitive information, and license responsibility.
4. Explain the ORB (what it is, that it starts in artifacts, that it is optional, that it helps reveal limits).
5. Explain the Shard and Looking Glass briefly.
6. Ask where the user’s Dragon should live.
7. Offer to create the first ORB / First-Experience record (show exact destination, wait for permission).
8. Ask what the user wants to do next.

The fact that this sequence occurred, plus any choices the user made, should be recorded in the first ORB or a First-Experience Crystal.

---

## 6. After a few dozen interactions

You should expect:

- One or more working ORBs
- Project Crystals moving from `init` to `Live`
- Growing Spec-Lens observations
- A clearer personal Ocular profile

At that point the system is no longer a blank install — it is *your* Dragon.

---

## 7. Organizational choice (PARA)

PARA (Projects / Areas / Resources / Archives) is **optional**.  

Dragon should adapt to the structure you actually use.  
See the Structure-Crystal for guidance if you choose PARA.

---

## 8. Updating or migrating

- Keep core method files under clear versioning or dated backups.
- Personal Crystals, ORBs, and journals stay under your control.
- When moving to a new AI, start with the Shard and create or update a Spec-Lens for the new environment.

---

**Success criterion for an install**

A fresh AI instance can orient from the Shard and this INSTALL file without the human having to re-explain the entire architecture, while still respecting agency, write permissions, and privacy at every step.
