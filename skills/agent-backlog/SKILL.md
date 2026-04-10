---
name: agent-backlog
description: Manage AI agent work via a markdown backlog in `.backlog/`. Use this skill whenever the agent starts a coding session, needs to plan work, track progress, or update task status. Trigger on any mention of "todo", "task list", "tasks", "goals", "backlog", "what's left to do", "plan the work", or when beginning/ending a coding session. Also trigger when the user asks to break down, prioritize, or review remaining work.
---

# Agent Backlog

This describes agent task management system. All agent work is tracked in a `.backlog/` folder at the project root.

## Taxonomy

```
.backlog/                      ← backlog root
  INDEX.md                     ← ordered list of active goals
  auth-refactor.md             ← goal
    ## Phase 1: Name           ← phase (optional)
    - [ ] Do the thing         ← task
      - [ ] Sub-step           ← subtask
  done/
    payment-integration.md     ← completed goal
```

- **Backlog** — the `.backlog/` folder. Contains all goals.
- **Goal** — a single markdown file. One focused effort (a feature, user story, refactor, bugfix).
- **Task** — a checkbox item inside a goal. One concrete action.
- **Subtask** — a checkbox indented under a task. One atomic step.
- **Phase** — optional `##` header grouping tasks into stages within a goal.

## Status markers

These markers apply to goals, tasks, and subtasks alike:
- `[ ]` — todo
- `[~]` — in progress
- `[x]` — done
- `[!]` — blocked (add reason inline, e.g. `→ blocked by: waiting for API keys`)

## INDEX.md

Lists active goals in priority order with status markers and markdown links. The agent works on the first active goal. Completed goals move to the `done/` section.

```markdown
# Active Goals
- [~] [Auth Refactor](auth-refactor.md)
- [ ] [User Registration](user-registration.md)

# Done
- [x] [Payment Integration](done/payment-integration.md)
```

## Workflow: Review → Work → Update

### Before starting work
1. Read `.backlog/INDEX.md` (create `.backlog/` folder and index if missing)
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
5. If all tasks in a goal are done → move the goal to `done/` section in INDEX.md

Always update the goal file and INDEX.md before and after each work session.

## Goal File Format

```markdown
# JIRA-1234: Implement User Registration

## Phase 1: Setup
- [x] Initialize project structure → `src/`
- [x] Configure linting and formatting

## Phase 2: Core Features
- [~] Implement auth module → `src/auth/`
  - [x] Add JWT token generation
  - [~] Add refresh token flow → see RFC 6749
  - [ ] Add rate limiting
- [ ] Build REST API endpoints → `src/api/routes.ts`
- [!] Integrate payment provider → blocked by: waiting for API keys

## Phase 3: Polish
- [ ] Add integration tests → `tests/integration/`
- [ ] Write API docs
```

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
- Create a new `.md` file in `.backlog/` for each new goal
- Add it to INDEX.md under Active Goals as `- [ ] [Goal Title](goal-file.md)`
- Mark `[~]` when work begins on a goal
- Mark `[!]` with reason if the goal is blocked
- When all tasks are done → mark `[x]`, move to Done section in INDEX.md and into `done/` folder
