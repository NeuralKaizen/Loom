# Note contract

The shared convention that lets every skill in this collection compose. **Capture**
skills (everlearn, decide, log) write notes that follow this contract; **maintenance**
(thread) and **retrieval** (recall) read it. Change it here, once.

## Frontmatter (every note)

```yaml
---
type: concept | decision | log | project   # which skill owns this note
created: YYYY-MM-DD               # absolute date
tags: [topic, ...]               # what it's about — thread colors by these
context: <one line>              # what you were doing when this was captured
project: "[[project-name]]"      # optional — the project this note belongs to (arc gathers it)
---
```

- **`type`** — the note's kind. Drives the folder it lives in and how thread/recall treat it.
- **`tags`** — topic tags (e.g. `js`, `async`, `devops`). The unit of coloring and recall.
- **`created`** — absolute date, never relative.
- **`context`** — one line tying the note to the moment it came from.
- **`project`** *(optional)* — a quoted `"[[wikilink]]"` to the project this note belongs to. Lets **arc** aggregate it (via backlinks) and lets recall/thread filter by project. Capture skills set it when the note clearly belongs to an active project. Quote it — YAML reads a bare `[[...]]` as a nested list.

## Types → folders

| type       | skill     | folder        | what it captures                            |
|------------|-----------|---------------|---------------------------------------------|
| `concept`  | everlearn | `concepts/`   | a concept you're learning, with examples    |
| `decision` | decide    | `decisions/`  | a technical decision + its context (ADR)    |
| `log`      | log       | `logs/`       | a quick learning, error, or reflection      |
| `project`  | arc       | `projects/`   | a project's context + lifecycle (living hub) |

All folders live under the same vault root. The root is resolved once and cached in a
shared config at `~/.config/loom/config.json` (`{ "vault": "<abs path>" }`); every skill
reads it and writes to `<vault>/<folder>/`. (everlearn still caches `conceptsDir` in
`~/.config/everlearn/config.json`; new skills bootstrap the vault root from it —
`dirname(conceptsDir)` — when the shared config isn't there yet.)

## Connections

Every note links into the graph via `[[wikilinks]]`. A note with no links is lost.
Skills may add a single contextual link into a clearly-related existing note
automatically (never rewriting it).

## How the skills use this

- **arc** (project hub) — maintains one living note per project: tracks lifecycle/status
  and gathers the notes that point at it via `project:`. It *updates* its note over time
  rather than capturing once.
- **thread** (maintenance) — colors the graph and notes by `type` and `tags`
  (graph color-groups + CSS, zero-plugin). It only reads frontmatter; it never
  rewrites note bodies.
- **recall** (retrieval) — answers "why do I do X?" (→ `decision`) and "what did I
  learn about Y?" (→ `concept` / `log`) by filtering on `type`, `tags`, and content.
