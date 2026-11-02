---
name: event-prep-sheet
description: Build a prep sheet for the coming days' events from Excellent — host, timing, rooms, party size, the menu the documents state (and where they disagree), what's still owed, and the staff on shift. Use for "prep sheet for this week's events", "what do we need to know for Saturday's wedding", "BEO rundown".
---

# Event prep sheet

Read-only. To draft a missing or stale BEO, proposal or contract, use the `build-event-documents` skill.

## 1. Collect

1. `agenda` — default 7 days, or the window the person names (`from`, `days`, `location`). Take every event in
   `dates`.
2. For each event, `get_event` with its `event_id`. Use:
   - the event's date, time window, party size, venue and rooms;
   - its contacts, host first;
   - the menu: the contract's or proposal's menu of record and each BEO's, and the `differences` where they
     disagree;
   - its documents with status and signature;
   - its money: each invoice's total, paid and balance, and installments still owed.
3. For staffing, `schedule_week` (or `schedule_today` for a single day) at that venue. If the schedule module
   is not switched on, skip staffing and say so.

## 2. Write one sheet per event

- **Header**: title, date and time at the venue's clock, venue and rooms, party size.
- **Host and contacts**: name, role, how to reach them.
- **Menu**: the menu of record; then a clear **Menu mismatch** list if any document disagrees.
- **Paperwork**: contract signed or not, latest BEO version and status.
- **Money**: total, paid, balance, next installment due. If `price_tbc_count` is above zero,
  `total_is_partial` is true or `rates_pending` is true, say the total is not final; never quote it as the
  whole price.
- **Staffing**: who is on during the event by role, open shifts, uncovered stretches.
- **Watch-outs**: unsigned contract, menu mismatch, balance due before the date, open shifts.

Amounts arrive in minor units (cents): divide by 100. Mark sample data (`is_sample: true`).

Offer, don't do: fixes happen in Excellent by a person (chasing a signature, finalizing a document). If an
event has no BEO, or its BEO disagrees with the contract, offer to draft a fresh one with the
`build-event-documents` skill.
