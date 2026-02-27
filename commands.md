# Commands Reference

All commands are invoked via the `todo` alias: `todo <command> [options]`

## help

Show the help documentation with quick start guide, command summary, and usage examples.

**Usage:**
```bash
todo help
```

Shows the contents of `help.md` with an overview of the system and all available commands.

---

## init \<space\> \<description\>

Create a new space for organizing tasks.

**Usage:**
```bash
todo init work "Work-related tasks and projects"
todo init home "Personal tasks and errands"
```

**Creates:**
- `<space>/todos.md` — for active tasks
- `<space>/done-todos.md` — for completed tasks

---

## add \<task\>

Add a new task to the current space. Claude automatically infers metadata from natural language.

**Usage:**
```bash
todo add "Finish quarterly report"
todo add "Quick 30-minute bug fix in login"
todo add "Email client by Friday"
todo add "Urgent: review pull requests"
```

**Metadata Inference:**
- **Deadline:** "by Friday", "before March 15", "end of month", "ASAP"
- **Duration:** "quick", "30 minutes", "2 hours", "full day"
- **Priority:** "urgent", "critical", "important", "low priority", "nice to have"
- **Tags:** Work, home, health, learning, etc. (inferred from context)

---

## done \<task-number\>

Mark a task as complete. Moves it from `todos.md` to `done-todos.md` with a completion timestamp.

**Usage:**
```bash
todo done 3
todo done 7
```

---

## start \<task-number\>

Mark a task as in-progress (currently being worked on).

**Usage:**
```bash
todo start 2
```

---

## list \[space\]

View active tasks in a space. If no space specified, shows the current space.

**Usage:**
```bash
todo list              # Show current space's active tasks
todo list work         # Show active tasks in work space
todo list home         # Show active tasks in home space
```

---

## list-done \[space\]

View completed tasks in a space.

**Usage:**
```bash
todo list-done         # Show completed tasks in current space
todo list-done work    # Show completed tasks in work space
```

---

## rm \<task-number\>

Remove a task permanently.

**Usage:**
```bash
todo rm 5
todo rm 10
```

---

## archive

Move completed tasks from `done-todos.md` to an archive, keeping the file clean. (Creates `done-todos-YYYY-MM.md` archive files if multiple archives exist.)

**Usage:**
```bash
todo archive
```

---

## spaces

List all available spaces.

**Usage:**
```bash
todo spaces
```

---

## Natural Queries

You can also ask Claude questions naturally without using explicit commands:

**Examples:**
```bash
todo show urgent tasks
todo what's due this week?
todo list all work items
todo show overdue tasks
todo which tasks should I start today?
```

Claude will parse these intelligently and provide relevant information from the current space.
