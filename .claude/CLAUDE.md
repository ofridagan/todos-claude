# todos-claude Setup

## Project Overview

This is a personal, Claude-powered todos management system. It supports organizing tasks across multiple "spaces" (work, home, life, etc.) — each space is a separate folder with its own `todos.md` and `done-todos.md` files.

## How It Works

- Each space is a self-contained folder with `todos.md` (active tasks) and `done-todos.md` (completed tasks)
- Tasks are stored as markdown with inferred metadata (deadline, duration, priority, tags)
- Claude intelligently parses natural language descriptions to extract and structure metadata
- All commands are documented in `commands.md`

## Session Initialization

**At the start of each session, ask the user which space they want to work in:**

```
Which todos space would you like to work in? (work, home, life, etc.)
Or type a new space name to create one.
```

Once they choose (or if only one exists), load that space's `todos.md` into context.

## Behavioral Rules for Commands

### Metadata Inference
When processing the `add <task>` command, intelligently infer metadata from the natural description:
- **Deadline:** "by Friday", "before March 15", "end of month" → extracts date
- **Duration:** "quick 30-minute task", "takes 2 hours" → extracts time estimate
- **Priority:** "urgent", "critical", "low priority", "nice to have" → infers level
- **Tags:** Context clues about domain (@work, @home, @health, etc.) → infers tags

Format inferred metadata into the todo structure automatically without requiring explicit tags.

### Task Numbering
Tasks in `todos.md` are numbered sequentially (1, 2, 3...) for easy reference with commands like `done 5` or `start 3`. When displaying tasks, always show the number.

### State Changes
- `done <num>` — moves task to `done-todos.md` with completion date
- `start <num>` — marks task as in-progress (✓ or [*] or similar marker)
- `rm <num>` — removes task (ask for confirmation if not explicitly confirmed)

### Flexible Queries
Users can ask natural questions like:
- "Show me urgent tasks"
- "What's due this week?"
- "List work tasks"
- "Show overdue items"

Claude should parse these intelligently without requiring explicit commands.

## Reference
See `commands.md` for the full command reference and examples.
