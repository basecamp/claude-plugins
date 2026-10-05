---
description: Prep for a meeting about a Basecamp project — recent decisions, open questions, what's late, and a draft agenda.
argument-hint: <project name or link, and the meeting's topic>
---

# Prep for a meeting

The project and the meeting: $ARGUMENTS

1. **Find the project.** A link: `get_by_url`. A name: `list_projects` or
   `search`. If none was named, ask.
2. **Read the state of things.**
   - `get_project_timeline` for what happened since the last meeting (a
     week, unless they say).
   - `get_project` for its dock, then `list_messages` on its message board,
     and `get_by_url` on the threads that matter.
   - Open work: `list_todolists` and `list_todos`, or `get_card_table`, for
     what's overdue, unassigned, or stuck.
   - `list_schedule_entries` on its schedule (`schedule_id` from the dock)
     for dates coming up.
   - `search` for the meeting's topic, to find the docs and threads behind
     it.

Reply with a one-page brief, linking every item to its `app_url`:

- **Since last time:** decisions and changes, a line each.
- **Open questions:** each with who raised it.
- **At risk:** what's late or blocked, and who owns it.
- **Agenda:** five or fewer items, in order, each with the decision the
  meeting needs to make.

If they want it in Basecamp, offer to save the agenda as a document
(`create_document` in the project's Docs & Files, `vault_id` from the
dock), as a draft unless they say to publish it.
