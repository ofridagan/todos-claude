# todos-claude Setup

⚠️ **IMPORTANT: At the very start of each session, before anything else, ask the user which todos space they want to work in. Do this immediately as your first message.**

```
Which todos space would you like to work in? (work, home, life, etc.)
Or type a new space name to create one.
```

Once they respond, load that space's `todos.md` into context and proceed.

---

## Project Overview

This is a personal, Claude-powered todos management system. It supports organizing tasks across multiple "spaces" (work, home, life, etc.) — each space is a separate folder with its own `todos.md` and `done-todos.md` files.

## How It Works

- Each space is a self-contained folder with `todos.md` (active tasks) and `done-todos.md` (completed tasks)
- Tasks are stored as markdown with inferred metadata (deadline, duration, priority, tags)
- Claude intelligently parses natural language descriptions to extract and structure metadata
- All commands are documented in `commands.md`

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

### Natural Language Commands
Users may attempt to use natural language to perform actions (e.g., "show me urgent tasks", "what's due today?", "mark task 3 complete").

When you detect a natural language command that maps to a built-in slash command, **kindly remind the user about the equivalent slash command**. For example:
- User: "Show me urgent tasks" → Respond helpfully, then mention: "You can also use `/list` to see all tasks"
- User: "I finished task 5" → Mark it done, then mention: "Next time, use `/done 5`"

This gently guides users toward the explicit command format without being prescriptive.

## Reference
See `commands.md` for the full command reference and examples.
