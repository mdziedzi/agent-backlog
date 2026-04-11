# Restructure .backlog Output Folder

Rename INDEX.md to BACKLOG.md and move goal files into a `goals/` subfolder with `done/` nested inside it.

**Current structure:**
```
.backlog/
  INDEX.md
  goal1.md
  done/
    completed-goal.md
```

**Target structure:**
```
.backlog/
  BACKLOG.md
  goals/
    goal1.md
    done/
      completed-goal.md
```

## Tasks

- [x] Rename `INDEX.md` to `BACKLOG.md` in SKILL.md (all references)
- [x] Update SKILL.md taxonomy diagram to show `goals/` and `goals/done/` structure
- [x] Update SKILL.md workflow and rules to reference new paths
- [x] Rename `assets/INDEX_TEMPLATE.md` → `BACKLOG_TEMPLATE.md` with new `goals/` path (GOAL_TEMPLATE.md had no path refs)
- [x] Verify AGENTS.md — no path references, no change needed
- [x] Update README.md references to old structure
- [x] Rename actual `.backlog/INDEX.md` → `.backlog/BACKLOG.md`
- [x] Move active goal files into `.backlog/goals/`
- [x] Move `.backlog/done/` into `.backlog/goals/done/`
- [x] Update all links in BACKLOG.md to reflect new `goals/` paths
