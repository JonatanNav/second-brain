# Second Brain

A consulting second brain, built to be used with Claude.

- **Core** (`core/`) – what the firm knows across all projects: methods, templates, facts such as market sizes, and who knows what.
- **Cells** (`cells/`) – one per engagement, created from `cells/_template/`. Client documents stay in SharePoint; cells hold links and distilled notes.
- **Harvest** (`harvest/`) – anonymised lessons from cells, reviewed before they are promoted into Core.

The rules Claude follows are in [`CLAUDE.md`](CLAUDE.md).

## Skills

| Skill | Use it to |
|---|---|
| `new-cell` | Start a new engagement under a codename: "start a new cell for …" |
| `capture-fact` | Save a market size, statistic or benchmark: "capture this fact: …" |
| `find-facts` | Ask what we know: "what do we know about the Nordic logistics market?" |

## Confidentiality levels

| Level | Meaning | Claude may |
|---|---|---|
| C1 Open | Internal / non-sensitive | Read and process sources freely |
| C2 Client-confidential (default) | Normal engagement | Read sources in-session; store notes and links only |
| C3 Restricted | NDA or client forbids AI | Never touch sources; only what you write in the cell |

## Roadmap

0. **Foundation** – structure, templates, `new-cell`, `capture-fact`, `find-facts` ← *we are here*
1. **Core seed** – move in existing skills (navigio-format, interview-insights, …), write first methods
2. **Cell lifecycle** – `ingest` (Fireflies / mail → notes), `cell-status`, `close-cell`
3. **Harvest loop** – `harvest` skill and review
4. **Retrieval** – search across Core and permitted cells; `fact-review` for stale facts
5. **Scale** – MCP server over this repo, per-cell access control, UI
