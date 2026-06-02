# thread

loom's maintenance layer: **color** your vault by topic and **tend** its health. Part of
[loom](../README.md). Run it on demand — it's deliberate, not in-the-flow.

## Paint

Gives each topic a stable color (palette in `~/.config/loom/colors.json`) and applies it
to the Obsidian **graph view** and to your **notes** (a CSS snippet + `cssclasses`).
Zero plugins.

## Tend

Reports vault health — orphan notes, contract gaps (missing `type` / `tags`), dangling
`project:` links, heavy uncreated ghost links — with handoffs to arc / everlearn. Reads
and suggests; fixes only when you ask.

## Triggers

- "thread", "coloreá / ordená el vault", "pintá el grafo"

- "revisá la salud del vault"

> Heads up: paint edits `.obsidian/` config and adds a `cssclasses` field to your notes,
> and you'll need to reload Obsidian to see the graph colors.

## Install

Ships with loom — see the [collection README](../README.md).

## License

MIT — see [../LICENSE](../LICENSE).
