---
name: money-owed
description: A digest of what's still owed on events in Excellent — deposits and installments coming due or overdue, partly paid and unpaid invoices, by venue and event date. Use for "which deposits are outstanding", "unpaid invoices", "who owes us money", "payments due this week", "draft the invoice for the Adler wedding".
---

# Money owed digest

This skill reads, and can draft an invoice. It never charges, records a payment, sends an invoice or contacts
a guest.

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

## 3. Draft a missing invoice (if asked)

For a booked event with no invoice, `get_event` shows what was agreed (the contract's or proposal's menu and
client total). Draft the invoice with `draft_invoice`: the `event_id`, its `lines` (each a `label`, a whole
`qty` and a `unit_price_minor` in cents, taken from what was agreed — never an invented price), and any
`tax_minor` / `fee_minor` the agreement states. Excellent computes the totals and the deposit from the
group's deposit schedule. Give back the figures and the review link: the person checks it and sends it from
the invoice page in Excellent. Nothing is sent from here.
