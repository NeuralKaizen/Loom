# everlearn

A Claude skill that generates learning material **while you build** — without breaking your flow.

When you're constructing something and get stuck on a concept, everlearn gives you exactly
what you need to understand and keep going — not a full course. It's built for fast-moving,
AI-assisted developers who reach unfamiliar territory and need the concept explained **in the
terms of what they're already building**, then saved so they can return to it.

## When it activates

- You're mid-development and don't understand something
- You ask "how does X work", "explain Y", "I don't get Z"
- You want to save a concept into your vault

## What it produces — two files

- `concepts/<concept>.md` — a structured Obsidian note: what it is (no filler), why it
  matters in *your* context, the key code pattern, an embedded interactive HTML demo, the
  design decisions behind the pattern, and common mistakes.
- `concepts/<concept>-demo.html` — a self-contained interactive demo (≤80 lines) that shows
  the concept visually using *your* domain, *your* variable names, *your* problem.

Both are saved to `~/Sophia/concepts/` — your Obsidian vault, ready to open and render the
demo inline.

## Structure

```
everlearn/
├── SKILL.md                      # skill definition + instructions
└── reference/
    ├── note-template.md          # structure of the concept note
    └── demo-template.html        # structure/constraints of the HTML demo
```

## Install

Make the skill available to Claude Code by linking it into your skills directory:

```bash
ln -s "$(pwd)" ~/.claude/skills/everlearn
```

Then it triggers automatically when you get stuck mid-build, or invoke it explicitly with
`/everlearn`.

## Philosophy

Learning shouldn't interrupt building. The material arrives contextualized to what you're
doing, it's interactive, and it stays in Obsidian for when you need it again.
