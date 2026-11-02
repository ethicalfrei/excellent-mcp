---
name: money-owed
description: A digest of what's still owed on events in Excellent — deposits and installments coming due or overdue, partly paid and unpaid invoices, by venue and event date. Use for "which deposits are outstanding", "unpaid invoices", "who owes us money", "payments due this week".
---

# Money owed digest

Read-only. This skill never charges, records a payment or contacts a guest.

## 1. Collect

1. `agenda` with `days: 14` (or the window the person names) — `payments_due` lists every installment still
   owed that falls due before the window ends, overdue ones included, with `left_minor`. If
   `payments_due_truncated` is true, say there are more than shown.
2. `list_invoices` with `status: "partial"`, then `status: "sent"` — paging with `next_offset` until null.
   Each row carries the total, deposit due, amount paid and linked event.
3. For an invoice the person asks about, `get_event` on its event shows each installment and every payment.
   Take the `event_id` from `payments_due`; an invoice row names its event by title only, so otherwise find
   the id with `search` (`kind: "event"`).

## 2. Write the digest

One line of totals first: "$X owed across N invoices; $Y overdue."

Then:

- **Overdue** — event, event date, installment, what's left, days late. Most overdue first.
- **Due in the window** — the same, soonest first.
- **Sent, nothing paid yet** — invoice, event, total, deposit due.
- **Partly paid** — invoice, paid, balance.

Flag events that happen before their balance is due-dated or paid. Amounts arrive in minor units (cents):
divide by 100. Mark sample data (`is_sample: true`) and keep it out of the totals unless the person wants it.

Offer, don't do: reminder wording can be drafted in this chat for a person to send; collecting payment
happens in Excellent.
