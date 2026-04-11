# Add Optional Goal Description and Developer Notes

Goal files currently only have a title and tasks. Add optional support for a **goal description** (why it exists, what it covers — scope, definition of done, acceptance criteria) and **developer notes** (architectural/technical decisions, e.g. "chose SQLite over Postgres because this runs embedded"). All optional — users choose their level of detail. A goal with just a title and tasks is perfectly valid.

## Tasks
- [x] Add optional goal description to goal file format → freeform block after the title covering motivation, scope, DoD, acceptance criteria — as lightweight or detailed as the user wants
- [x] Add optional developer notes support → `> [!NOTE]` callouts anywhere in the goal file for architectural decisions, technical rationale, trade-offs
- [x] Document that the goal structure is: title → description (optional) → tasks (required), with developer notes anywhere → `skill.md`
- [x] Update the Goal File Format example in `skill.md` to show both minimal (tasks-only) and rich (description + notes) variants → `skill.md`
- [x] Update the example backlog goal if one exists to demonstrate the optional metadata → no examples directory exists yet, covered by separate "Add Example Backlog" goal
