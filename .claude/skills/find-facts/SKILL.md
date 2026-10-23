---
name: find-facts
description: Answer "what do we know about…" questions from the second brain's Core knowledge – market sizes, statistics, benchmarks, topic pages – with sources, periods and confidence. Use when the user asks what the firm knows about a market, industry, geography or number, e.g. "what do we know about the Nordic logistics market?", "har vi någon marknadsstorlek för…", "vad vet vi om…", "find facts on…".
---

# find-facts

Answers from `core/knowledge/` only. Never from cells (they are client-confidential and isolated) unless the user explicitly names a cell.

## 1. Search
Search `core/knowledge/topics/`, `facts/` and `benchmarks/` for the subject. Match on frontmatter (`industry`, `geography`, `topic`, `claim`) and file names, and include obvious synonyms in both languages (e.g. *vård* ↔ *healthcare*, *marknadsstorlek* ↔ *market size*, *Norden* ↔ *Nordics*). Read any topic page first – it is the synthesis.

## 2. Answer
Answer in the user's language. Lead with the direct answer, then a table:

| Claim | Value | Period | Source | Confidence | File |
|---|---|---|---|---|---|

Then flag, briefly:
- **Stale** – `review_by` is before today
- **Conflicts** – different values for the same claim and period
- **Weak** – `confidence: low` or `origin: estimate`
- **Gaps** – what was asked but isn't in the base

## 3. Never fill gaps silently
If the base has nothing or too little, say so plainly. You may then offer to research it (web search or the user's SharePoint) and save results with `capture-fact` – but keep anything you find clearly separate from what the brain already knew.
