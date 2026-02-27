# todos-claude

A personal, Claude-powered todos management system with support for multiple spaces (work, home, life, etc.).

## Quick Start

### 1. Create Your First Space

```bash
todo init work "Work-related tasks"
todo init home "Personal tasks at home"
```

This creates `work/` and `home/` folders, each with `todos.md` and `done-todos.md`.

### 2. Add Tasks (Just Talk Naturally)

```bash
todo add "Finish Q1 report"
todo add "Quick 30-minute bug fix"
todo add "Email client by Friday"
todo add "Urgent: fix login page"
```

Claude automatically infers:
- Deadlines from "by Friday", "by March 15", etc.
- Duration from "quick", "30 minutes", "2 hours", etc.
- Priority from "urgent", "critical", "nice to have", etc.
- Tags from context clues

### 3. View Your Tasks

```bash
todo list              # Show active tasks in current space
todo list work         # Show tasks in work space
todo list-done         # Show completed tasks
```

### 4. Update Task Status

```bash
todo done 3            # Mark task #3 as complete
todo start 5           # Mark task #5 as in-progress
todo rm 7              # Remove task #7
```

### 5. Manage Spaces

```bash
todo spaces            # List all spaces
todo archive           # Archive completed tasks (moves done-todos to history)
```

## Natural Queries

You can also ask questions naturally:

```bash
todo show urgent tasks
todo what's due this week?
todo list work tasks from home
```

Claude will parse and respond intelligently.

## File Structure

```
todos-claude/
  README.md
  commands.md           # Full command reference
  .claude/
    CLAUDE.md          # Claude behavior instructions
    settings.json      # Model configuration (Haiku)
  work/
    todos.md           # Active work tasks
    done-todos.md      # Completed work tasks
  home/
    todos.md           # Active home tasks
    done-todos.md      # Completed home tasks
```

## Tips

- Tasks support inline metadata: dates, times, priorities, tags
- Keep task descriptions natural and conversational
- Use `list` or `list-done` frequently to stay on top of things
- Archive periodically to keep files manageable

## Commands

See `commands.md` for the complete reference.
