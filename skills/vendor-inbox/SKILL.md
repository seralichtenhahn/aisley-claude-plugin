---
name: vendor-inbox
description: Read and answer the couple's emails with venues and suppliers through Aisley, and chase the ones that went quiet. Use when someone asks who has replied, who they are waiting on, what a venue said, or wants to reply or follow up.
---

# Vendor inbox and follow-ups

Aisley reads the replies that reach the couple's Gmail and drafts answers and follow-ups. The couple approves every email before it goes.

## Who is waiting on whom

- `show_vendor_conversations` shows the inbox as a card where the client renders one. Pass the filter needs_you for replies waiting on the couple.
- `list_conversations` returns every conversation with its `counterpartId`, unread replies, and whether Aisley has drafted a reply or follow-up.

## Answering a reply

1. Call `get_conversation` with the `counterpartId`. Summarise what the venue or supplier said: prices, dates, conditions and questions they asked.
2. Start from Aisley's suggested reply when there is one and it fits; otherwise draft one with the couple.
3. Show the exact to, cc, subject and body. The to address must be the reply address from `get_conversation`.
4. Call `reply_to_vendor` with only what the couple approved. It continues the same email thread.
5. Call `mark_conversation_read` once the couple has seen a reply they don't need to answer. If they don't want Aisley's suggested reply, `dismiss_reply_suggestion` clears it.

## Chasing

1. Call `list_follow_ups`. It lists each conversation waiting on the other side, the days waited, and Aisley's drafted follow-up with its `followUpId`.
2. Show each follow-up's to, subject and body.
3. Call `send_follow_up` with the approved follow-up unchanged; a changed follow-up is refused. To send different words, use `reply_to_vendor` instead.
4. Use `dismiss_follow_up` to skip one, and `mute_follow_ups` to stop chasing a counterpart.
5. A conversation that went quiet after two follow-ups needs the couple's decision. Close it with `resolve_quiet_conversation` once they've made it.

How soon and how often Aisley chases is set with `set_follow_up_settings`; `get_wedding` shows the current settings.
