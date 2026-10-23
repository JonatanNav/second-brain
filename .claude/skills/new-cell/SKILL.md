---
name: new-cell
description: Create a new project cell (one consulting engagement) in the second brain from cells/_template, under a neutral codename. Use when the user starts a new client project, engagement, assignment or proposal – e.g. "start a new cell for…", "new project", "nytt uppdrag", "starta en ny cell", "set up a project for <client>".
---

# new-cell

Creates `cells/<codename>/` from `cells/_template/`. The real client identity goes only in the cell's git-ignored `PRIVATE.md`; everything committed uses the codename.

## 1. Gather the essentials
Ask only for what the user hasn't already given, in one message, in the user's language:

- **Client** and **project name** (these go in `PRIVATE.md` only)
- **One-paragraph description** of the engagement (goal, why now)
- **Confidentiality level** – explain briefly and suggest C2 as the default:
  - C1 Open – internal / non-sensitive
  - C2 Client-confidential – normal engagement
  - C3 Restricted – NDA or the client forbids AI processing
  If the user is unsure, ask whether the contract says anything about AI tools or subcontractors.
- **SharePoint folder link** (may be added later; goes in `PRIVATE.md`)
- Optional: start date, industry, geography, key stakeholders (names → `PRIVATE.md`, roles → `CELL.md`), slide format skill (default `navigio-format`; a client-specific format skill if one exists)

## 2. Pick a codename
Propose one neutral, single-word codename in kebab-case – a bird, animal, star or similar. It must **not** hint at the client, its industry, location or the project (no initials, no puns). Check that `cells/<codename>/` doesn't exist. Let the user accept or pick another.

## 3. Create the cell
1. Copy the template: `cp -r cells/_template cells/<codename>` (includes the hidden `.claude/` folder).
2. Rename `PRIVATE.template.md` to `PRIVATE.md` and fill it in: client, project, SharePoint root, team and stakeholder names, and the SharePoint link as source `S01` if given.
3. Fill in `CELL.md`: codename, an anonymous `client_profile` (e.g. "Nordic healthcare region", "~2 bn SEK manufacturer"), confidentiality, dates, industry, geography, description, goals, scope, and stakeholders **by role**. Set `created` and `start` to today unless told otherwise; `lang` to the user's language.
4. **Leak check before finishing:** grep the new cell, excluding `PRIVATE.md`, for the client name, project name and every person's name you were given (case-insensitive, also without å/ä/ö). Fix any hit.
5. Confirm with `git check-ignore cells/<codename>/PRIVATE.md` that it is ignored. If it isn't, stop and tell the user.

## 4. Respect confidentiality from the start
- **C3:** do not open the SharePoint link or search mail/Fireflies for this client. Tell the user that Claude will only work with what they write into the cell.
- **C1/C2:** offer – don't do it unasked – to look in SharePoint/Outlook/Fireflies for kickoff material to summarise into `notes/` (citing sources by ID, without names).

## 5. Check Core for a head start
Search `core/knowledge/` (facts, topics, benchmarks) and `core/methods/` for the cell's industry and geography. List up to five relevant items with links. Do not copy them into the cell – link instead.

## 6. Report back
Short summary: codename, cell path, confidentiality level, what was filled in, what is still missing, and the relevant Core items. Remind the user that `PRIVATE.md` exists only on this machine – keep the codename list in SharePoint as well. Don't commit unless the user asks; if you do, use the codename only in the commit message.
