---
name: build-event-documents
description: Draft a private event's proposal, banquet event order (BEO) or contract in Excellent from the event's own facts and the venue's own menu prices, for a person to review, finalize and send in Excellent. Use for "build the BEO for the Adler wedding", "draft a proposal for this event", "generate the contract for Saturday's party", "the BEO is out of date, redo it".
---

# Build event documents

This skill stages document drafts only. Excellent's document engine writes each one from the event's date,
guest count, venue, rooms and host, and prices it from the venue's own menu for that date — never from a
number in this chat. Nothing is finalized, shared with the guest or sent until a person does it in Excellent.

## 1. Find the event

`search` what the person names (`kind: "event"`) or take the id from `agenda`, then `get_event` to read back
the event: title, date, guest count, venue, rooms, host, and the documents it already has (type, status,
signed or not).

- If the event has **no venue**, say so: the draft would be priced from sample menus and cannot be finalized
  until the event has a venue in Excellent.
- If it already has a document of that type, ask whether to draft another; each call stages a new draft. A
  signed contract or proposal is never redrafted: an amendment happens in Excellent.
- A contract carries what the client agreed to: if the event has a finalized proposal, the contract draft
  takes its menu and prices.

## 2. Draft

Call `draft_event_document` with the `event_id` and the `kind` — `proposal`, `beo` or `contract`. Give back
what was staged (title, type, the menu lines and the client total the answer states) and the review link.

- Lines marked as needing a price, or a bill with no service charge, fees or tax set yet, are flagged in the
  draft: say so, and never quote a partial total as the whole price.
- If the answer says the venue's menus or the event could not be loaded, nothing was drafted or spent: try
  again in a moment rather than drafting from something else.
- If it says the AI budget is reached, say so; it frees up as its window rolls forward.

## 3. Hand off

End with the link and one line: "This is a draft. Open it in Excellent to check it, then finalize it there;
nothing reaches the guest until you share or send it."
