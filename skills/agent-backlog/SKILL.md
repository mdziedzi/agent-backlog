---
name: agent-backlog
description: Manage AI agent work via a markdown backlog in `.backlog/`. Use this skill whenever the agent starts a coding session, needs to plan work, track progress, or update task status. Trigger on any mention of "todo", "task list", "tasks", "goals", "backlog", "what's left to do", "plan the work", or when beginning/ending a coding session. Also trigger when the user asks to break down, prioritize, or review remaining work.
---

# Agent Backlog

This describes agent task management system. All agent work is tracked in a `.backlog/` folder at the project root.

## Taxonomy

```
.backlog/                      ← backlog root
  BACKLOG.md                   ← ordered list of active goals
  goals/
    auth-refactor.md           ← goal
      ## Phase 1: Name         ← phase (optional)
      - [ ] Do the thing       ← task
        - [ ] Sub-step         ← subtask
    done/
      payment-integration.md   ← completed goal
```

- **Backlog** — the `.backlog/` folder. Contains `BACKLOG.md` and a `goals/` subfolder with all goal files.
- **Goal** — a single markdown file. One focused effort (a feature, user story, refactor, bugfix, etc.).
- **Task** — a checkbox item inside a goal. One concrete action.
- **Subtask** — a checkbox indented under a task. One atomic step.
- **Phase** — optional `##` header grouping tasks into stages within a goal.

## Status markers

These markers apply to goals, tasks, and subtasks alike:
- `[ ]` — todo
- `[~]` — in progress
- `[x]` — done
- `[!]` — blocked (add reason inline, e.g. `→ blocked by: waiting for API keys`)

## BACKLOG.md

Lists active goals in priority order with status markers and markdown links. The agent works on the first active goal. Completed goals move to the `Done` section and their files move into `goals/done/`. The Done section is stacked with the most recently completed goal on top.

```markdown
# Active Goals
- [~] [Auth Refactor](goals/auth-refactor.md)
- [ ] [User Registration](goals/user-registration.md)

# Done
- [x] [Payment Integration](goals/done/payment-integration.md)
```

## Workflow: Review → Work → Update

### Before starting work
1. Read `.backlog/BACKLOG.md` (create `.backlog/`, `.backlog/goals/`, and `BACKLOG.md` if missing)
2. Open the first active goal file
3. Review tasks — still relevant? Scoped correctly?
4. Decompose vague or large tasks into subtasks
5. Add any newly discovered tasks
6. Refine descriptions and context links

### During work
1. Mark current task `[~]` in progress
2. Work top-down — task order defines priority, first incomplete task is next
3. If blocked → mark `[!]` with reason, move to next task

### After finishing work
1. Mark completed tasks `[x]`
2. Add tasks discovered during work
3. Update context links if files moved or changed
4. Re-assess remaining tasks for relevance and scope
5. If all tasks in a goal are done → move the goal to the `Done` section in BACKLOG.md and move the file into `goals/done/`

Always update the goal file and BACKLOG.md before and after each work session.

## Goal File Format

A goal file has the structure: **title → description (optional) → tasks (required)**. Developer notes can appear anywhere.

- **Description** — optional freeform text after the title. Covers motivation, scope, definition of done, acceptance criteria — as lightweight or detailed as you want.
- **Developer notes** — optional `> [!NOTE]` callouts anywhere in the goal file. Use for architectural decisions, technical rationale, or trade-offs that aren't obvious from the tasks.

A goal with just a title and tasks is perfectly valid. See `assets/GOAL_TEMPLATE.md` for the full structure.

## Rules

### Ordering
Task order defines priority. The first incomplete task in the current phase is the next to work on. Reorder tasks to reprioritize.

### Subtasks
- Indent 2 spaces under parent
- Max 2 nesting levels
- Each subtask = one atomic action
- Parent is done only when all children are `[x]`

### Context links
Append `→` after the description to link context. Use only when the task title alone isn't clear enough.
- File path: `→ src/auth/jwt.ts`
- URL: `→ https://docs.example.com/api`
- Inline note: `→ uses the strategy pattern from the auth refactor`

### Task creation
- Agent adds tasks when it discovers work (bugs, missing tests, TODOs in code, refactors)
- Decompose any task that requires 3+ distinct steps
- Never delete tasks — only mark done
- New tasks go under the relevant section, or create a new section

### Goal lifecycle
- Create a new `.md` file in `.backlog/goals/` for each new goal — add a description and developer notes if useful, or just start with tasks
- Add it to BACKLOG.md under Active Goals as `- [ ] [Goal Title](goals/goal-file.md)`
- Mark `[~]` when work begins on a goal
- Mark `[!]` with reason if the goal is blocked
- When all tasks are done → mark `[x]`, move to Done section in BACKLOG.md and into `goals/done/` folder
