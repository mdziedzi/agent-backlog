# agent-backlog

A skill for AI coding agents that gives them a persistent, markdown-based backlog to track their own work across sessions.

## The problem

AI coding agents lose context between sessions. Tasks discussed in one conversation are forgotten in the next. There's no persistent record of what's done, what's in progress, and what's next — so agents re-discover work, repeat mistakes, or silently drop tasks.

## How it works

The skill teaches your agent a simple workflow: **Review → Work → Update**.

- **Goals** are markdown files in `.backlog/goals/` — one per feature, bugfix, or refactor
- **Tasks** are checkbox items inside a goal, worked top-down
- **Phases** optionally group tasks into session-sized stages
- **`BACKLOG.md`** lists goals in priority order
- Each session the agent reads the backlog, picks up where it left off, works through tasks, and updates progress before ending

Everything is plain markdown. No database, no tooling, no lock-in — just files you can read, edit, and version-control yourself.

## Install

```sh
npx skills add https://github.com/mdziedzi/agent-backlog --skill agent-backlog
```

Or manually: copy `skills/agent-backlog/` into your project's `skills/` directory or your agent's config.

## Quick start

1. Install the skill and start a coding session
2. Tell your agent what you want to build or fix
3. The agent creates `.backlog/`, adds a goal with tasks, and starts working

You can also create goals yourself or plan them with your AI Agent.

## Status markers

| Marker | Meaning |
|--------|---------|
| `[ ]`  | todo |
| `[~]`  | in progress |
| `[x]`  | done |
| `[!]`  | blocked (with inline reason) |

These markers apply to goals in `BACKLOG.md`, tasks, and subtasks alike.

## Full spec

See [skills/agent-backlog/SKILL.md](skills/agent-backlog/SKILL.md) for the complete specification — taxonomy, goal file format, workflow rules, and conventions.
