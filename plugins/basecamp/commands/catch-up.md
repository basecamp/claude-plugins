---
description: Catch up on a Basecamp project — what changed, what was decided, what's still open, and what needs you.
argument-hint: <project name or link>
---

# Catch up on a project

The project to catch up on: $ARGUMENTS

1. **Find the project.** A link: `get_by_url`. A name: `list_projects`, or
   `search` if the list is long. If several match, ask which; if none was
   named, ask.
2. **Read what happened.** `get_project_timeline` for the recent activity.
   It returns the latest 100 events and can't page, so if its oldest event
   is newer than the start of the window, say the catch-up starts there.
   `get_project` for its dock, then `list_messages` on its message board for
   the latest discussions. Open what matters with `get_by_url` on its
   `app_url`: a decision, a long thread, a document that changed.
3. **Who's asking.** `get_me` names the person, so you can tell what's
   theirs.
4. **What's open now.** The timeline only shows what moved recently, so read
   current state too, keeping this project's group from each:
   `list_everything_todos` with `state` set to overdue, then to unassigned;
   `list_everything_cards` with `state` set to overdue; and `get_my_assignments`
   for what's on them.

Reply in four short parts, linking every item to its `app_url`:

- **What changed** in about the last week, or since the date they give: the
  handful of things that matter, not every event.
- **Decided:** each decision, quoting the line that settled it.
- **Open:** unanswered questions, overdue or unassigned to-dos, stuck cards.
- **Needs you:** what's assigned to them, mentions them, or waits on their
  answer.

This is a read: post nothing and change nothing. Offer to dig into any
thread.
