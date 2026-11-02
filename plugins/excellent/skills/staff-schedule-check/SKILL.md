---
name: staff-schedule-check
description: Check a restaurant group's staff schedule in Excellent — who is on today, the week's coverage per venue, open shifts, stretches of opening hours nobody covers, scheduling warnings and what staff can't see yet. Use for "who's on tonight", "is the week covered", "any open shifts", "check next week's schedule", "add a closing server on Friday", "fill the open Saturday brunch shift".
---

# Staff schedule check

This skill reads, and can add draft shifts. It never publishes a week or tells staff anything: shifts it
adds stay in the week's draft until a person publishes the week in Excellent.

## 1. Collect

- Today (or one named day): `schedule_today`, with `date` and `location` if given. Per venue it lists who is
  on (person, role, start and end on the venue's clock, break), the open shifts and each shift's warnings.
- A week: `schedule_week` with any `date` in the week wanted (default this week). Per venue and day it gives
  shifts, people, open shifts, planned minutes, shifts by role and the `uncovered` stretches of opening hours
  (null when the venue has no hours on file).
- If events are on, `agenda` for the same days shows the bookings and party sizes the staff is there for.

If the tool answers that this part of Excellent is not switched on, say so and stop.

## 2. Write the check

Per venue:

- **Publish state** — draft (staff can't see it), published, or published with changes staff don't see yet
  (`unpublished_changes`). Say how many.
- **Gaps** — open shifts and uncovered stretches, by day and time on the venue's clock.
- **Warnings** — in plain words: overlap, double booked at another venue, short rest between shifts,
  inactive or archived staff still scheduled.
- **Busy days** — days with large events next to the people scheduled by role.

End with the three most important fixes for a person to make in Excellent, most urgent first.

## 3. Fill a gap (if asked)

To cover an open stretch, `draft_shift` with the `location`, the venue `date`, `start` and `end` on the
venue's clock (HH:MM; an end at or before the start runs past midnight), the `role`, and the person's
`staff_id` from the schedule tools' roster (leave it out for an open shift). Read each shift back before
adding it. Give back the review link, and say staff see nothing until someone publishes the week in
Excellent.
