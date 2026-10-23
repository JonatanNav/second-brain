# Knowledge (horizontal)

Cross-project knowledge such as market sizes, statistics, benchmarks and regulation.

| Folder | Holds | Template |
|---|---|---|
| `facts/` | One number or claim per file | `core/templates/fact.md` |
| `topics/` | Synthesis pages linking many facts | `core/templates/topic.md` |
| `benchmarks/` | Anonymised comparables from engagements (via `harvest/`) | `core/templates/fact.md` with `origin: client-derived` |
| `sources/` | Reports and databases we rely on, with reliability | `core/templates/source.md` |

**Golden rule:** no number without `source`, `period` and `origin`.

Fact file names: `<topic>-<geography>-<subject>-<period>.md`, e.g. `market-size-se-healthcare-it-2025.md`.
