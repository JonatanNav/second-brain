# Second Brain – operating rules for Claude

This repository is a consulting second brain. It has three zones:

| Zone | Path | What it holds | Changes |
|---|---|---|---|
| **Core** | `core/` | Firm-wide knowledge, methods, templates, facts | Slow, curated |
| **Cells** | `cells/<codename>/` | One engagement each: context, notes, deliverables | Fast, isolated |
| **Harvest** | `harvest/` | Anonymised lessons from cells awaiting promotion to Core | Reviewed |

Active skills live in `.claude/skills/` (Core skills) and `cells/<codename>/.claude/skills/` (cell-specific skills, which take precedence inside that cell).

## Hard rules

1. **Cells inherit from Core, never the reverse.** Never copy client content into `core/` directly. The only path is `harvest/` → review → `core/`.
2. **No client documents in this repo.** Client source material lives in SharePoint. Cells store distilled notes; SharePoint links live in the cell's git-ignored `PRIVATE.md`. Never save PDFs, Office files or raw transcripts under `cells/`.
3. **Codenames, not client names.** Every cell has a neutral codename (e.g. `falcon`). Real client names, project names, people's names and SharePoint URLs go **only** in `cells/<codename>/PRIVATE.md`, which is never committed. In every committed file – and in branch names and commit messages – use the codename, an anonymous profile ("Nordic healthcare region") and roles ("CIO", "project sponsor"). You may read `PRIVATE.md` for context, but never copy its contents elsewhere.
4. **Respect the cell's confidentiality level** (`confidentiality` in `CELL.md`) before reading or processing anything for that cell:
   - **C1 Open** – may read sources and ingest/summarise freely.
   - **C2 Client-confidential** (default) – may read sources in-session when the user asks; store only notes and SharePoint links.
   - **C3 Restricted** – never open, fetch or summarise the cell's sources (SharePoint, mail, Fireflies). Work only with what the user writes into the cell. If asked to, refuse and explain why.
5. **Never mix cells.** When working in one cell, do not read or cite another cell's notes unless the user explicitly asks. Cross-project knowledge comes from Core.
6. **No number without a source.** Every fact needs `source`, `period` and `origin` (see `core/templates/fact.md`). Never invent or "estimate silently" – if you estimate, mark `origin: estimate` and explain the method.
7. **Sources are immutable, notes are derived.** Notes refer back to what they came from by source ID from `PRIVATE.md` (e.g. `S03`), meeting date or Fireflies ID – never by URL.

## Conventions

- **Structure in English, content in either language.** Folder names, file names and frontmatter keys are English. Body text may be Swedish or English; set `lang: sv|en`. Answer in the language the user writes in.
- **File names:** `kebab-case`, ASCII only (å→a, ä→a, ö→o). Dated notes: `YYYY-MM-DD-short-title.md`.
- **Frontmatter on every note.** Use the templates in `core/templates/`. Required on all notes: `type`, `created`, `lang`.
- **Links:** use relative Markdown links between notes so the repo works without special tooling.
- **Cell folders:** `cells/<codename>/`, a single neutral word in kebab-case (animals, birds, stars…), e.g. `cells/falcon/`. Never derived from the client or project name.

## Where things go

| You have… | Put it in |
|---|---|
| A public market size, statistic, benchmark | `core/knowledge/facts/` (use `capture-fact`) |
| A synthesis across many facts on a theme | `core/knowledge/topics/` |
| A report / database we rely on | `core/knowledge/sources/` |
| A reusable way of working | `core/methods/` |
| Who knows what in the firm | `core/people/` |
| Anything about a specific client engagement | `cells/<codename>/` |
| Client name, people's names, SharePoint links | `cells/<codename>/PRIVATE.md` (never committed) |
| A lesson worth reusing, from a cell | `harvest/` (anonymised) |
