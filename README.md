---
name: README.md
internal_name: 2026-10-10-2358-readme
object_type: system
file_type: system
type: system (why; root index)
status: live
version: v1.2
date: 2026-10-09
revised: 2026-10-10-2358 PT
author: tripLr
owner: Owner
location: repository root
license: MIT
---

# Dragon

> Your AI is replaceable. Your knowledge system isn't.

**A portable, model-agnostic way to keep your work with AI in plain files that you own.**

## Why this exists

Useful AI conversations, research, journaling and project work outlive any one chat window. Long conversations forget their early parts, insights get trapped in a single thread, and a new AI means teaching everything again. Dragon keeps continuity **outside** the AI, in ordinary files in folders you control, so a different AI, app or storage system can pick up where you left off. The AI can change without losing the knowledge system.

The longer story is in [ORIGIN.md](ORIGIN.md) (a template you fill in with your own).

## The creed

1. **Agency first.** The owner owns the data, the decisions and the direction.
2. **External continuity.** Important state and rules live outside any single AI.
3. **Challenge to improve.** Challenge ideas to test them for failure and learn from it.
4. **Trust.** Say what you mean; clarify intent; prefer accurate output to fast output.
5. **Versioned knowledge.** Keep the path of understanding when interpretations change.

## How this repository is laid out

The root holds four files and the folders. Everything else sits in a folder.

| Layer | Where | What it does |
|---|---|---|
| **Why** | `README.md` (this file, also the root index), `ORIGIN.md`, `LICENSE` | The purpose, your story, the terms. |
| **Contract: behavior** | `AGENTS.md` | The operating rules every AI follows. |
| **Contract: files** | `Resources/Dragon-Object-Schema.md` | How every file is written, named, linked and archived. |
| **How** | `Projects/AI-Work/processes.md`, `Projects/AI-Work/tasks.md` | Repeatable procedures any AI follows instead of being retrained, and daily or recurring work. |
| **Places (PARA)** | `Projects/`, `Areas/`, `Resources/`, `Archive/` | Each has a starter Crystal (an index of the folder). |
| **First project** | `Projects/AI-Work/` | Its Crystal, `processes.md`, `tasks.md`, `Bots/Example-Bot/` (a bot Crystal), `Conversations/`, `Object-History/`. |
| **History** | `Dragon-Object-History/`, `Dragon-Orb-History/` | Dated copies of old versions of files; thin session records (orbs) with their index and a blank template. |
| **Start here** | `Resources/INSTALL.md` | Honest first steps. |

## Key ideas

- **Objects** are files with a short header, a location and typed links (edges) to other files.
- **Crystals** are index files, one per folder or project, so a human or an AI can walk the folders and find things without scanning everything.
- **Point, do not copy.** Refer to a file by its name and location, never by pasting its body or relying on a storage id.
- **Archive first.** Before a live file changes, a dated copy of the old version is kept. Nothing is deleted without the owner's explicit OK.
- **Propose, then write.** Assistants draft and point. Durable writes happen only on the owner's permission.
- **Thin orbs, rich Crystals.** An orb is a short record of one session. The knowledge lives in the Crystals.

## Status: V1, honest

This is a V1 starter set, **not** a one-click install. The contracts and the processes are the valuable part; the folders and Crystals are templates to fill in. See [Resources/INSTALL.md](Resources/INSTALL.md).

## Branches: `main` and `dev`

- **`main` is the stable branch.** What you clone by default. Fixes to the processes, tasks, contracts and Crystals are made here, so the repository always matches the current working version.
- **`dev` is staging for the next major upgrade.** Bigger changes that are not ready, or that would change the structure for everyone, are built there first and merged into `main` only when the upgrade is ready.
- **Why two:** a fix should not have to wait for a big upgrade, and a big upgrade should not break the stable copy while it is built. If you fork this to make your own, start from `main`.

## Object table (root index)

| Name | Location | Version | Status | One-line summary |
|---|---|---|---|---|
| README.md | root | v1.2 | live | This file |
| ORIGIN.md | root | v1.0 | template | Your story (fill in) |
| AGENTS.md | root | v1.2 | template | Operating contract for any AI |
| LICENSE | root | n/a | live | MIT |
| Dragon-Object-Schema.md | Resources | v2.4 | live | File contract |
| INSTALL.md | Resources | v1.1 | live | First steps |
| Projects-Crystal.md | Projects | v0.1 | template | Index of Projects/ |
| Areas-Crystal.md | Areas | v0.1 | template | Index of Areas/ |
| Resources-Crystal.md | Resources | v0.1 | template | Index of Resources/ |
| Archive-Crystal.md | Archive | v0.1 | template | Index of Archive/ |
| Orb-History-Crystal.md | Dragon-Orb-History | v1.0 | template | Index of orbs |
| Blank-Orb-Template.md | Dragon-Orb-History | v1.0 | template | Thin orb to copy |
| AI-Work-Crystal.md | Projects / AI-Work | v1.0 | template | First project's Crystal |

## Dragon Stack

**Role:** primary source of truth and root index of this container
**Facets:** purpose | creed | layout | index

### Edges

- contains:: [[Projects-Crystal.md]] (Projects/) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
- contains:: [[Areas-Crystal.md]] (Areas/) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
- contains:: [[Resources-Crystal.md]] (Resources/) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
- contains:: [[Archive-Crystal.md]] (Archive/) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
- contains:: [[Orb-History-Crystal.md]] (Dragon-Orb-History/) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
- mentions:: [[AGENTS.md]] (operating contract) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
- mentions:: [[Dragon-Object-Schema.md]] (file contract, in Resources) {date: 2026-10-09, by: tripLr, src: build, status: proposed}
- mentions:: [[ORIGIN.md]] (the story behind it) {date: 2026-10-09, by: tripLr, src: build, status: proposed}

**Return:** README.md
**Evidence rule:** Point only. Do not copy the layer below.

## License

MIT. See [LICENSE](LICENSE).

**End of README.md**
