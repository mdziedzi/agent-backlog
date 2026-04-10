# Fix INDEX Linking Format

Update INDEX.md to use markdown links for goals and status markers for goal-level tracking.

## Phase 1: Spec changes
- [x] Add goal status markers to INDEX.md spec
  - [x] Document that goals use same `[ ] [~] [x] [!]` markers as tasks
  - [x] Update INDEX.md example in SKILL.md
- [x] Change goal entries from plain filenames to markdown links
  - [x] Update INDEX.md format description in SKILL.md
  - [x] Update goal lifecycle section to mention link format
- [x] Update INDEX_TEMPLATE.md to use links + status markers → `skills/agent-backlog/assets/INDEX_TEMPLATE.md`
- [x] Consolidate status markers into single section in SKILL.md
- [x] Add `blocked by:` format to blocked status

## Phase 2: Align examples
- [x] Update goal file example in SKILL.md → already uses correct format
- [x] Update PROJECT_TODO_TEMPLATE.md → no changes needed, it's a goal template not INDEX
