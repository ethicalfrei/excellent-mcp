---
name: lead-follow-up
description: Triage the private-event and catering inquiries waiting on a reply in Excellent — who asked, for what date and party size, whether a room fits — and draft reply text in the chat for a person to send themselves. Use for "which leads haven't we answered", "follow up on new inquiries", "lead triage".
---

# Lead follow-up triage

Read-only. This skill never contacts a guest and never changes a lead. Reply text is drafted in this chat
only; a person copies it and replies from their own inbox or from Excellent.

## 1. Collect

1. `list_leads` with `status: "new"` (and, if the person asks, a second call with `status: "contacted"`).
   Keep paging with the answer's `next_offset` until it is null.
2. `agenda` (default 7 days) — its `leads_waiting` names the inquiries nobody has answered yet, which is the
   most urgent set.
3. For each inquiry that names a date and a party size, call `space_availability` with that `date` and
   `party_size`. Each room says `fits_party` and lists its `free` stretches. A free stretch is not a
   reservation: only a person books, in Excellent.
4. If an inquiry looks like a returning host, `search` their name or email to find past events.

## 2. Write the triage

Sort oldest first. For each inquiry, one line: name, event type, date asked for, party size, source, days
waiting, and one of:

- **Room fits and is free** — name the rooms.
- **Fits, but the date is busy** — name what is in the way (a booking, a hold or a block).
- **No room fits the party size.**
- **No date given** — the reply needs to ask for one.

## 3. Draft replies (in chat only)

If the person asks, draft a short reply per inquiry in the venue's voice: thank them, answer the date and
room question with what the tools showed, and ask for anything missing (date, headcount, budget). Never
promise a room is held or booked, and never quote a price the tools did not return.

Say plainly that these are drafts for them to send. Nothing in this skill sends anything.
