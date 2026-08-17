# Train Your Dragon AI — Dragon 2.0

**Internal Version:** 4.0  
**Updated:** 2026-08-16  

**A portable, model-agnostic architecture for durable human-AI work.**

> Your AI is replaceable. Your knowledge system isn't.

Train Your Dragon AI grew from a practical problem: useful AI conversations, reasoning, journaling, and project work can outlive the transient context available to any one AI instance.

Dragon keeps continuity outside the model while allowing different humans, AI systems, interfaces, and storage systems to work together.

---

## Important: Privacy, Responsibility & License Awareness

**This project was created for voice journaling and research.**  
The two original active projects were Personal Development and Dragon training / architecture work.

**Personal notes are always private.**  
This method does not claim ownership of your personal data.

### Sensitive information

An ORB is optional.  
If you do not want sensitive information (including anything that may be covered by HIPAA or similar rules) left on the AI side, you must:

1. Transfer the files to storage you control, and  
2. Delete them from the artifact workspace.

You may run private instances where they are available. My-Dragon can run inside those instances. You remain responsible for removing private or sensitive information.

### What you must be aware of

When using this system with any AI, be aware that information may exist in:

- The AI’s native memory / personalization features
- The artifact / local workspace used during a session
- Conversation or instance history saved by the app or platform

### License responsibility

**Know the model’s license and terms before continuing.**

AI provider licenses and terms of use can be broad about data use, retention, training, and sharing.  
You are responsible for reviewing the license and terms of any AI you use with this system.

This project is a method and architecture under your control. It is not a hosted service and does not change the terms of the AI platforms you choose to use.

---

## Values Layer

See **`Dragon-Creed-2.0.md`** for the short set of weighted principles that orient the human–AI partnership (Agency First, External Continuity, Challenge to Improve, Connection Before Correction, and others).

The Creed complements the operating rules in the Shard. It does not replace them.

---

## Core Structure

Dragon is organized as layered containers:

- **Physical container** — the user’s real files and folders
- **AI container (Shard)** — modular kernel / operating definition
- **ORB** — working container for live session continuity
- **Crystal** — durable project / idea container

The Shard holds the current operating rules (Looking Glass principles, Ocular, Spec-Lens, ORB and Crystal handling).  
Crystals hold durable project knowledge and can be loaded into an active ORB. Updates return only after review.

---

## Organization (PARA is optional)

PARA (Projects • Areas • Resources • Archives) is the organizational pattern used by the original author.  

It is **not required**.  

A user may organize information differently. Dragon should adapt to the user’s chosen structure rather than force one folder system.  

See `Dragon-Structure/Structure-Crystal.md` for the rationale and guidance on how My-Dragon can sit inside a PARA layout when that choice is made.

---

## Global Write Flow

`local artifact workspace → review content + exact destination → explicit permission → persistent write → verify`

Drafting and modification happen locally first. Before writing to Drive, GitHub, or another persistent store, review the content and intended destination with the user and obtain explicit permission.

---

## Model-agnostic by design

Dragon must not depend on one AI provider.

Models, companies, interfaces, context windows, and storage systems will change.

A different AI should require a different or updated Spec-Lens — not reconstruction of the user’s knowledge system.

---

## Origin

Dragon began with voice-based personal-development journaling during commercial trucking work and evolved as practical limits in private training access, AI context, continuity, storage, and repeated instance training were discovered.

See `ORIGIN.md` for the full story, including the 16 August 2026 simplification.

---

## License

MIT — see `LICENSE`.

The public method and documentation are separate from a user’s private living data and knowledge stores.
