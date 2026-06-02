# Note contract

The shared convention that lets every skill in this collection compose. **Capture**
skills (everlearn, decide, log) write notes that follow this contract; **maintenance**
(thread) and **retrieval** (recall) read it. Change it here, once.

## Frontmatter (every note)

```yaml
---
type: concept | decision | log   # which capture skill owns this note
created: YYYY-MM-DD               # absolute date
tags: [topic, ...]               # what it's about — thread colors by these
context: <one line>              # what you were doing when this was captured
---
```

- **`type`** — the note's kind. Drives the folder it lives in and how thread/recall treat it.
- **`tags`** — topic tags (e.g. `js`, `async`, `devops`). The unit of coloring and recall.
- **`created`** — absolute date, never relative.
- **`context`** — one line tying the note to the moment it came from.

## Types → folders

| type       | skill     | folder        | what it captures                          |
|------------|-----------|---------------|-------------------------------------------|
| `concept`  | everlearn | `concepts/`   | a concept you're learning, with examples  |
| `decision` | decide    | `decisions/`  | a technical decision + its context (ADR)  |
| `log`      | log       | `logs/`       | a quick learning, error, or reflection    |

All folders live under the same vault root (resolved once, shared via
`~/.config/everlearn/config.json` → `conceptsDir` is the concepts folder; sibling
folders derive from it).

## Connections

Every note links into the graph via `[[wikilinks]]`. A note with no links is lost.
Skills may add a single contextual link into a clearly-related existing note
automatically (never rewriting it).

## How the skills use this

- **thread** (maintenance) — colors the graph and notes by `type` and `tags`
  (graph color-groups + CSS, zero-plugin). It only reads frontmatter; it never
  rewrites note bodies.
- **recall** (retrieval) — answers "why do I do X?" (→ `decision`) and "what did I
  learn about Y?" (→ `concept` / `log`) by filtering on `type`, `tags`, and content.
