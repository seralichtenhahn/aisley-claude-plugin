---
name: venue-search
description: Find wedding venues with Aisley and build the couple's shortlist. Use when someone wants venue ideas, asks for venues in an area, for a guest count or under a budget, or wants to add, compare, rule out or move a venue along.
---

# Venue search and shortlist

## Before searching

Call `get_wedding`. Fill the gaps in the couple's request from it: region, guest count, budget, date and vibe. Ask only for what is missing from both, one question at a time.

Call `list_venue_searches`. A search runs on the couple's Aisley credit and search allowance, so when a recent search covers the same thing, read its results instead of starting another.

## Running a search

1. Call `search_venues` with one plain description, such as "barn venues near Bath for 120 guests under £15k".
2. The search takes a minute or two. Tell the couple it is running, then call `get_venue_search` with the `searchId` until its status is complete.
3. Show each result with its name, why it fits, and its price signal. Leave out results the couple already saved or dismissed.
4. Save the ones the couple picks with `save_venue` and the `resultId`. Drop the ones they reject with `dismiss_venue_result`; `undo_venue_dismissal` brings one back.
5. Use `load_more_venue_results` when the couple wants more.

A venue the couple found themselves goes in with `save_venue` and its name or website. Aisley fills in the rest from the website.

## Working the shortlist

- `show_venue_shortlist` shows the shortlist as a card where the client renders one; `list_venues` returns the `venueId` of each venue.
- Move a venue along with `set_venue_status`: shortlisted, contacted, in_conversation, viewing_booked, booked or ruled_out. Booking a venue also adds it to the budget, so confirm with the couple before setting booked.
- Record what the couple liked or disliked with `update_venue` or `add_venue_note`.
- Prefer ruled_out to `remove_venue`. Removing deletes the venue's record and notes; ask first.

When the couple is ready to contact venues, hand over to the `venue-outreach` skill.
