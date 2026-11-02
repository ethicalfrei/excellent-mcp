---
name: weekly-owner-report
description: The owner's weekly read on a restaurant group's events business from Excellent — revenue booked, collected and outstanding, booking pace against goal, pipeline and win rate, lead sources and the per-venue rollup, plus the week ahead. Use for "weekly report", "how are we pacing against goal", "which location is behind", "owner update".
---

# Weekly owner report

Read-only. This skill changes nothing in Excellent.

## 1. Collect

1. `report` with `period: "month"`, and again with `period: "year"` (or the window the person asks for:
   month, quarter, year or all). It returns revenue (booked, collected, outstanding), pace against the last
   period with an on-track verdict and the percentage of the annual goal, the pipeline by stage and win rate,
   the lead funnel, booking sources and the per-location rollup.
2. `overview` — the group's headline figures and venues.
3. `agenda` with `days: 7` — the week ahead.

Read `dataBasis` and `dataBasisNote`: say at the top whether the figures count real records, sample records,
or real records with sample rows set aside. Booked and outstanding include draft invoices; say so once.

## 2. Write the report

Keep it to one screen:

- **Headline** — the on-track verdict in one sentence, with the percentage to goal.
- **Money** — booked, collected, outstanding for the month and the year to date.
- **Pipeline** — events by stage, win rate, the lead funnel.
- **Where bookings come from** — top sources.
- **By venue** — one line each; name the venue that is behind and by how much.
- **The week ahead** — event count, the biggest events, holds to decide, payments due.

Amounts arrive in minor units (cents): divide by 100. Use the report's figures as given; don't recompute
them.
