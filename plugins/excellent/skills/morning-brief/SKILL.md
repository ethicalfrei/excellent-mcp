---
name: morning-brief
description: The morning brief for a restaurant group on Excellent — today's and tomorrow's events per venue, holds that need a decision, payments coming due, unanswered inquiries and who is on shift. Use for "what's on today", "morning brief", "what needs me today", "give me the rundown across our venues", "draft today's pre-shift note".
---

# Morning brief across venues

Read-only, except the optional pre-shift note at the end, which is staged as a draft for a person to publish.

## 1. Collect

1. `overview` — the group's name, its venues (`locationList`) and the headline figures. If `dataBasis` says
   the figures are sample (demo) data, say so at the top of the brief.
2. `agenda` with `days: 2` — today and tomorrow at the group's clock. If the person named one venue, pass its
   id from `locationList` as `location`. From the answer use:
   - `dates`: each day's events (time, rooms, party size, host, balance);
   - `holds`: a hold with `lapses_in_window: true` needs a decision before it lapses;
   - `payments_due`: installments still owed that fall due in the window, overdue ones included;
   - `leads_waiting`: the inquiries nobody has answered yet (a count and the newest few).
3. `schedule_today` — who is on at each venue, the open shifts nobody is on yet, and each shift's warnings.
   If it answers that the module is not switched on, skip the staff section and say so in one line.

## 2. Write the brief

One line of totals first: "N events today, M tomorrow, K holds to decide, J inquiries waiting."

Then one short section per venue, today first:

- **Events** — time (venue's clock), title, party size, rooms, host; flag any with a balance still owed.
- **Holds to decide** — who holds which room, and when the hold lapses.
- **Payments due** — invoice, what's left, due date; overdue ones first.
- **On shift** — people by role, open shifts, and any warning in plain words (for example "double booked at
  another venue").

End with **Inquiries waiting**: name, date asked for, party size, and how long they have waited.

Amounts arrive in minor units (cents): divide by 100 and show them as money. Mark anything with
`is_sample: true` as sample data.

## 3. Offer next steps

Offer, don't do: open one event in full with `get_event`, triage the waiting inquiries (the lead-follow-up
skill), or check the staff week (the staff-schedule-check skill).

## Pre-shift note (if asked)

If the person wants today's pre-shift note, write it from what the brief found (the events, guest counts,
VIPs and timings) and show it first. Then stage it with `draft_preshift_note` (`date`, `body_en`, and
`body_es` when the team reads Spanish). A day that already has a note is left as it is. Give back the review
link: the note reaches staff only when a person publishes it in Excellent.
