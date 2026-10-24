---
name: wedding-check-in
description: Give the couple a short briefing on their wedding plan from Aisley. Use when someone asks what needs them this week, where the planning stands, how long until the wedding, or what to do next.
---

# Wedding check-in

Build the briefing from the Aisley connector's tools, in this order:

1. Call `get_wedding` for the date, guest count, region and budget. Count the days to the date if one is set.
2. Call `list_conversations` and pick out venues and vendors with an unread reply or a drafted reply waiting on the couple.
3. Call `list_follow_ups` for anyone the couple is waiting on, and how many days each has been quiet.
4. Call `list_tasks` for open to-dos, most urgent and soonest due first.
5. Call `get_budget` only when the couple asks about money or a booking changed this week.

Reply with at most five lines, most pressing first:

- Days to the wedding, if the date is set
- Replies waiting on the couple, by venue or vendor name
- Follow-ups ready to send, with how long each has waited
- The two or three to-dos that matter most this week

Each line names the next step: "Read the reply from Hartwell Barn", "Send the follow-up to Oak Hall". Offer to do it; never send an email or change a task as part of the briefing.

When the plan is empty, with no venues, conversations or tasks, say so and offer to start a venue search (the `venue-search` skill) or draft a starter to-do list with `draft_task_plan`, which uses the couple's Aisley credit.

For a question the tools don't answer directly, such as "what did the Old Rectory say about corkage?", call `ask_aisley` with the question.
