---
description: Turn a goal, brief, or meeting notes into a Basecamp plan — to-do lists and to-dos with owners and dates, or cards on a Card Table.
argument-hint: <project name or link, and what to plan>
---

# Plan it in Basecamp

What to plan, and where: $ARGUMENTS

1. **Find the project.** A link: `get_by_url`. A name: `list_projects` or
   `search`. If none fits, offer to create one with `create_project`, and
   only create it once they agree.
2. **Read its dock.** `get_project` lists its tools. Plan into to-dos unless
   they asked for cards or the project works from a Card Table
   (`get_card_table` shows its columns).
3. **Find the people.** `list_project_people` for who can own each piece.
   Don't guess an owner they didn't name.
4. **Propose the plan first**, as an outline: lists (or columns) with their
   to-dos (or cards), each with an owner and a due date where one is clear.
   Ask what to change.
5. **Create it once they approve.**
   - To-dos: `create_todolist` in the project's to-do set (`todoset_id` from
     the dock), then `create_todo` for each, with `assignee_ids` and
     `due_on` (`YYYY-MM-DD`).
   - Cards: `create_card` in the right column (`column_id`), then
     `update_card` to set `assignee_ids`.
   For to-dos, leave `notify` off unless they want people notified now.
   Cards can't do that: `create_card` takes no assignees, so its `notify`
   reaches no one, and `update_card` has no `notify`. If they want card
   owners told, say so and offer to post or comment instead.

Reply with what was created, linked, and anything you skipped and why. The
`posting-and-mentions` topic of `get_basecamp_guide` says who each post
notifies.
