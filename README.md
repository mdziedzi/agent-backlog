# agent-backlog

A skill for managing AI agent work via a simple markdown backlog kept in a `.backlog/` folder at the project root.

## How it works

- **Goals** live as individual markdown files (`.backlog/auth-refactor.md`) — one focused effort per file.
- **Tasks** are checkbox items inside a goal; **subtasks** nest one level under them.
- **Phases** (`##` headers) optionally group tasks into stages.
- **`INDEX.md`** lists active goals in priority order; completed goals move to `done/`.

## Status markers

- `[ ]` todo
- `[~]` in progress
- `[x]` done
- `[!]` blocked (with inline reason)

## Workflow

Each session follows **Review → Work → Update**: open `INDEX.md`, pick the first active goal, refine or decompose its tasks, work top-down, then mark progress and move finished goals to `done/`.

See [skills/agent-backlog/SKILL.md](skills/agent-backlog/SKILL.md) for the full specification.
