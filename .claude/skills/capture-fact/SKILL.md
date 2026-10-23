---
name: capture-fact
description: Save a horizontal fact – market size, statistic, growth rate, benchmark, price level, regulation figure – into the second brain's Core knowledge base with source, period and origin. Use when the user says "capture this fact", "save this number", "spara den här siffran", "lägg in marknadsstorlek", pastes a figure, report excerpt or link and wants it remembered, or asks to update an existing fact.
---

# capture-fact

Turns a number or claim into an atomic fact card in `core/knowledge/facts/`, using `core/templates/fact.md`.

## 1. Extract the fact(s)
From what the user gave (text, link, report, table), identify each distinct claim. One fact = one number or claim. If the input holds several, list them and ask which to capture (default: all that have a clear source).

For each fact determine: `claim`, `value`, `unit`, `geography`, `industry`, `topic`, `period`, `source`, `source_url`.

## 2. Enforce the golden rule
A fact needs **source**, **period** and **origin**.
- Missing source or period → ask. Never guess, never fill in from your own memory as if it were the source.
- If the user wants to save their own estimate, set `origin: estimate`, `confidence: low` unless they argue otherwise, and write the method in the body.
- **Client-derived numbers** (a client's own figures, or an estimate built from client data): do **not** put these in Core. Tell the user it belongs in the cell, and offer to write an anonymised proposal in `harvest/` instead (`core/templates/harvest.md`, `kind: benchmark`).

## 3. Set confidence
- `high` – official statistics or well-known primary research with a stated method
- `medium` – reputable secondary source, consulting/industry report, method partly stated
- `low` – press article, vendor marketing, estimate, unclear method

## 4. Avoid duplicates
Search `core/knowledge/facts/` for the same topic + geography + subject (grep frontmatter and file names).
- **Same claim, newer period or better source** → create the new fact and set `supersedes:` to the old file name; add a line to the old fact's Notes: "Superseded by <file>".
- **Same claim, same period, different value** → keep both, and tell the user about the conflict with both sources so they can judge.
- **Identical** → don't create a new file; tell the user it already exists.

## 5. Write the file
- Path: `core/knowledge/facts/<topic>-<geography>-<subject>-<period>.md`, kebab-case, ASCII only. Example: `market-size-se-healthcare-it-2025.md`.
- `captured` = today, `review_by` = today + 12 months (6 months for fast-moving markets or forecasts).
- `lang` = language of the source. Write the body (method/definition, notes) in that language.
- `value` as a plain number in base units (12 bn → `12000000000`).

## 6. Register the source and link topics
- If the source isn't in `core/knowledge/sources/`, offer to add it (`core/templates/source.md`).
- If a topic page exists in `core/knowledge/topics/` for this subject, add the fact to its Key facts list. If none exists and there are now 3+ facts on the subject, offer to create one.

## 7. Report back
One line per fact: claim, file path, confidence, and anything the user should check (conflicts, missing source page, low confidence).
