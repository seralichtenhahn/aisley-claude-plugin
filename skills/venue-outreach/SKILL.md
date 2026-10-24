---
name: venue-outreach
description: Write to wedding venues through Aisley from the couple's Gmail. Use when someone wants to enquire about availability or prices, contact one or several shortlisted venues, or ask a venue a question.
---

# Venue outreach

Every email goes from the couple's own Gmail. Nothing is sent until the couple has read the exact email and said yes.

## Check Gmail first

Call `get_gmail_status`. If Gmail isn't connected or a setup step is left, call `connect_gmail` and give the couple the link; they finish the setup in their browser. Drafting can go ahead while they do, sending can't.

## One venue

1. Get the `venueId` from `list_venues`.
2. Call `draft_venue_email`. It uses the couple's Aisley credit.
3. Show the draft in full: to, cc, subject and body.
4. Apply the couple's edits to the text yourself and show the result again.
5. Call `send_venue_email` with exactly the approved to, cc, subject and body. The venue moves to contacted.

If the venue has already written back, the email belongs in that thread: use `reply_to_vendor` from the `vendor-inbox` skill.

## Several venues

1. Call `start_batch_outreach` with the `venueId`s. Aisley writes one personal email per venue, which takes about a minute and uses the couple's Aisley credit.
2. Call `get_batch_outreach` until the drafts are ready. Venues without an email address are listed without a draft; say which.
3. Show every draft in full, one after another.
4. Save each edit with `update_batch_draft`, and drop any draft the couple doesn't want with `discard_batch_draft`.
5. Call `send_batch_outreach` with only the `draftId`s the couple approved. Then call `get_batch_outreach` and report which were sent and why any failed.

## Never

- Send an email the couple hasn't seen in its final form
- Treat "looks good" for one draft as approval for the others
- Invent prices, dates or availability in an email; write only what the couple or Aisley's plan gives you
