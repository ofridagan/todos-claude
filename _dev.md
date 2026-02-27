# todos-claude — Dev Notes

> Temporary file. Remove when the project is complete.

## What this project is

A personal Claude-powered todos management project. A single repository that supports todos across multiple "spaces" (work, home, life, etc.). Each space is a subfolder with its own `todos.md` and `done-todos.md`.

## Project structure (target)

```
todos-claude/
  _dev.md              # this file — remove when done
  rules.md             # Claude behavior rules (shared across spaces)
  commands.md          # available commands and their conventions (e.g. init)
  .claude/
    CLAUDE.md          # instructs Claude to ask which space at session start
    settings.json      # sets model to claude-haiku-4-5-20251001
  <space>/             # created via `init` command, e.g. work/, home/, life/
    todos.md
    done-todos.md
```

## Design decisions

- **Spaces** (not areas/zones) — the name for each context (work, home, life)
- **No pre-defined spaces** — user creates them with the `init` command
- **`init` is a Claude command** — not a shell script. Documented in `commands.md`, Claude executes it when asked
- **`todo` alias** in `.zshrc`: `todo() { (cd ~/dev/todos-claude && command claude "$@"); }`
- **Model** set in `.claude/settings.json` (Haiku — cheapest, sufficient for todos)
- **CLAUDE.md** should instruct Claude to ask which space to work in at the start of each session, then load that space's `todos.md`
- **`done-todos.md`** — completed tasks move here to keep `todos.md` clean

## What's done

- [x] Folder created at `~/dev/todos-claude`
- [x] `rules.md`, `commands.md` created (empty scaffolding)
- [x] `.claude/settings.json` with Haiku model
- [x] `todo` alias added to `~/.zshrc`
- [x] Git repo initialized (not yet pushed to GitHub)

## What's left

- [x] Write `.claude/CLAUDE.md` — space selection prompt + behavioral instructions
- [x] Write `README.md` — quick start guide with examples
- [x] Write `commands.md` — document all commands
- [ ] Push to GitHub as a new repo (`todos-claude`)
- [ ] Source `.zshrc` / test the `todo` alias
- [ ] Create first space(s) to validate the flow

## Design Notes

- **No rules.md** — behavioral rules are in `.claude/CLAUDE.md` instead
- **Commands:** `init`, `add`, `done`, `start`, `list`, `list-done`, `rm`, `archive`, `spaces`
- **Metadata inference:** Claude automatically infers deadline, duration, priority, tags from natural descriptions
- **No explicit `edit` command** — users can `rm` and `add` instead to keep it simple
