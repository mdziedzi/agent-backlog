# agent-backlog

A skill for managing AI agent work via a simple markdown backlog kept in a `.backlog/` folder at the project root.

## How it works

- **Goals** live as individual markdown files — one focused effort per file.
- **Tasks** are checkbox items inside a goal; **subtasks** nest one level under them.
- **Phases** optionally group tasks into stages.
- **`INDEX.md`** lists active goals in priority order; completed goals move to `done/`.

## Install

### Using npx skills
```sh
npx skills add https://github.com/mdziedzi/agent-backlog --skill agent-backlog
```

Or manually: copy `skills/agent-backlog/` into your project's `skills/` directory or your agent's config.

## Status markers

- `[ ]` todo
- `[~]` in progress
- `[x]` done
- `[!]` blocked (with inline reason)

## Workflow

Each session follows **Review → Work → Update**: open `INDEX.md`, pick the first active goal, refine or decompose its tasks, work top-down, then mark progress and move finished goals to `done/`.

See [skills/agent-backlog/SKILL.md](skills/agent-backlog/SKILL.md) for the full specification.
