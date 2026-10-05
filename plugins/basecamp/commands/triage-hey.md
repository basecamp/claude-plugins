---
description: Triage your Basecamp Hey! menu — sort what needs a reply from what's just FYI, draft replies, and clear what's handled.
---

# Triage my Hey!

1. `get_my_notifications`: unreads first. Use `page` for more if the first
   page is all unread.
2. Open anything you can't judge from its excerpt with `get_by_url` on its
   `app_url`.
3. Sort each unread into one of three groups:
   - **Needs you:** a direct question, a mention asking for something, an
     assignment, a decision waiting on them.
   - **Worth knowing:** announcements and updates on their work.
   - **Nothing to do:** boosts, automatic notices, threads that already
     moved on.

Reply with the three groups, each item a line with who, the project, the
gist, and a link. For **Needs you**, offer a short draft reply for each.

Act only when the person says so:

- **Reply:** `get_by_url` on the item gives the `reply_target`; post the
  reply there, quoting it back to them first. Use `mentions` with person IDs
  to @-mention someone. No `reply_target` means a reply can't be posted from
  here; say so.
- **Clear:** `mark_as_read` with the `readables` of the items they choose.
