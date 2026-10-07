---
description: Draft your answer to a Basecamp automatic check-in, like "What did you work on this week?", from your own recent activity.
argument-hint: "[check-in question link or project]"
---

# Draft a check-in answer

Which check-in: $ARGUMENTS

1. **Find the question.** A link: `get_by_url`. A project: `get_project`
   for its dock, then `get_questionnaire` and `list_questions`. If they
   didn't say, ask which check-in.
2. **Read their voice.** `get_me`, then `get_answers_by_person` with the
   question and their `person_id` for their last few answers: length, tone,
   format.
3. **Gather what they did** over the question's period (a week, unless the
   question says otherwise): `get_catchup` with `days` (its finished to-dos
   are scoped to that window), and `get_project_timeline` on the projects
   they were active in. Timelines and the catch-up's activity counts include
   teammates' work: count an event as theirs only when its creator is the
   person from `get_me`, and use the rest as context. `get_catchup` reaches back 14 days at most, so for a
   longer period, such as a monthly check-in, say the draft covers only the
   last 14 days. `get_my_completed_assignments` carries no completion dates,
   so don't count its items as done in this period. For what's in
   progress, next, and blocked, read `get_my_assignments`: current work
   with no recent activity shows up only there.

Draft the answer the way they write: what they finished, what's in
progress, what's next, and anything blocked, linking to the work. Show the
draft and ask what to change.

Post only when they say to: `create_answer` with the question and the
answer as HTML in `content`. Then link to it.
