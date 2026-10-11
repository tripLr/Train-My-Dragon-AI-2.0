---
name: INSTALL.md
internal_name: 2026-10-09-2005-install
object_type: system
file_type: system
type: system (how to start)
status: live
version: v1.1
date: 2026-10-09
revised: 2026-10-09-2005 PT
author: tripLr
owner: Owner
location: Resources / INSTALL.md
license: MIT
---

# INSTALL

## Honest status

This repository is a **V1 starter set. It is not install-ready.** There is no installer, no script and no app. What you get are the rules (the contracts) and the procedures (the how), plus empty folders and template files to copy. A power user can fork it and adjust it to their own tools. Expect to read and edit.

## What you need

- A place to keep files that you control (a folder on your computer, a cloud drive, or a git repository).
- Any AI that can read text files you give it (paste them in or connect the folder).
- About an hour to read `AGENTS.md` and `Dragon-Object-Schema.md`.

## Steps

1. **Copy the set.** Fork or download this repository into your own storage. Keep it private at first.
2. **Pick your root.** The top folder is your Dragon root. Keep only `README.md`, `ORIGIN.md`, `AGENTS.md` and `LICENSE` there. The file contract, `Dragon-Object-Schema.md`, and this file live in `Resources/`.
3. **Write your ORIGIN.** Fill in the `ORIGIN.md` template with your own why. Short is fine.
4. **Fill the Crystals.** Each folder (`Projects/`, `Areas/`, `Resources/`, `Archive/`, `Projects/AI-Work/`, `Dragon-Orb-History/`) has a starter Crystal. Replace the placeholders (`YYYY-MM-DD`, `?`, `Owner`) and add a row for each object you put in the folder.
5. **Adapt the contract.** Edit `AGENTS.md` for your owner name, your folders and your tools. Keep the safety rules (propose first, archive first, nothing deleted without an OK) unless you have a reason to change them.
6. **Give your AI the contract.** At the start of a session, give the AI `AGENTS.md`, then `Dragon-Object-Schema.md` when it needs the object rules. Tell it which folder is the root.
7. **Work in the project folder.** Use `Projects/AI-Work/` as the pattern for a project: its Crystal, `processes.md`, `tasks.md`, `Conversations/` and `Object-History/`. Copy the folder for each new project.
8. **Orbs (optional).** When a thread gets long or you switch AIs, copy `Dragon-Orb-History/Blank-Orb-Template.md`, fill it in and add it to `Orb-History-Crystal.md`.

## What is not here yet

- Skills and more bots (`Projects/AI-Work/Bots/Example-Bot/` is a pattern for one bot Crystal; copy it for each bot).
- Tooling to lint or sync the folders (the lint rules are in `Dragon-Object-Schema.md` Part 8; run them by hand or ask your AI).
- A tested cold-start on a second person's machine.

## If something does not fit

The schema is a standard, not a law. Change what you need, version the change, and keep the old copy in `Dragon-Object-History/`. When a file belongs to a project, its old copies go in that project's `Object-History/`.

**End of INSTALL.md**
