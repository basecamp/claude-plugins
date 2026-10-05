---
name: basecamp
description: Work with Basecamp through the Basecamp tools — find, read, create, and update projects, to-dos, cards, messages, comments, documents, schedules, and Campfire chats. Use for any Basecamp question or action, and for any basecamp.com link.
---

# Basecamp

Every Basecamp action is its own tool, named for what it does: `get_*` and
`list_*` read; `create_*`, `update_*`, `complete_*`, `move_*`, `trash_*` and
the rest change data. Everything runs as the signed-in person and sees only
what they can see.

The server keeps the reference notes on how Basecamp works:
`get_basecamp_guide` returns the core concepts with no `topic`, or one
topic — `concepts` (accounts, projects, the dock, and the IDs each tool
takes), `finding-things`, `my-work`, `posting-and-mentions` (HTML, mentions,
who is notified), and `deleting-and-trash`. Read the topic before a task it
covers that you have not done in this conversation.

## Where to start

- **A Basecamp link?** Pass it to `get_by_url` as `url`. It returns the IDs
  the link names, the record itself, and, for anything that takes comments
  when this connection can post them, `reply_target`: the tool and IDs a
  reply goes to. A link to a comment answers with the comment and its
  parent as the reply target, since comments are not threaded. No
  `reply_target` means no reply can be posted from here. Don't read IDs out
  of the link yourself.
- **By keyword?** `search`, then `get_by_url` with a result's `app_url` for
  the full record.
- **Mine?** `get_my_assignments` (priorities first), `get_my_day` (today's
  schedule and due to-dos), `get_overdue_todos`, `get_upcoming_schedule`,
  `get_my_notifications` (the Hey! menu: unreads first), `get_catchup`
  (what happened while away).
- **In a project?** `list_projects` or `search` to find it, then
  `get_project` for its dock: each dock tool's ID is what that tool's
  `list_*` and `create_*` calls take.
- **Long results** come a page at a time. A result carrying `next_cursor`
  or `next_page` has more: pass that value back as `cursor` or `page` to
  continue.

## Accounts and projects

Each connection works in one Basecamp account; `get_me` names the
signed-in person and that account. A link into another account is out of
reach from this connection — `get_by_url` says so; tell the person rather
than guess. When a request needs a project and doesn't name one, ask which
— don't pick one for them.

## Writing

- **Rich text** — message bodies, comments, documents, to-do and card notes
  — is HTML; titles, to-do names and Campfire lines are plain text. The
  `posting-and-mentions` topic lists the tags Basecamp keeps.
- **@-mentions.** `create_comment` takes `mentions`: person IDs from
  `list_pingable_people` or `list_project_people`.
- **Assigning.** `assignee_ids` replaces the whole list; include everyone
  who stays assigned. Dates are `YYYY-MM-DD`.
- **Notifications.** Posting can notify people, but not always: a message
  or document created without `status: "active"` is an unposted draft, and
  a to-do or event notifies only when `notify` is true. The
  `posting-and-mentions` topic says who each post notifies; report what was
  actually sent. Confirm with the person before posting on their behalf to
  others, and quote what will be posted.

## Removing things

`trash_*` tools move an item to the Basecamp trash, where it can be
restored. Tools whose description says "Permanently" cannot be undone: run
one only when the person asked for exactly that deletion. The
`deleting-and-trash` topic covers the difference, and archiving.

## Replying well

Link to what you mention: every item carries an `app_url`. Name the project
and, when the person has several accounts, the account. Say plainly when
something could not be found or read rather than filling the gap.
