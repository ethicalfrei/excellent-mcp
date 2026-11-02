---
name: private-event-space-check
description: Check whether a private event fits — which rooms at which venues hold the party size, and when they are free on the date asked — from Excellent's room capacity, bookings, holds and blocks. Use for "is the Garden Room free Saturday for 60", "where can we put a party of 40 on the 14th", "space check for this inquiry".
---

# Private-event space check

Read-only. A free stretch is not a reservation: only a person books, holds or blocks a room, in Excellent.

## 1. Pin down the ask

Get the date (or a range of up to 14 days), the guest count, a rough time (lunch, evening, a start and end)
and, if named, the venue or room. Don't guess a date: if the person says "next Saturday", state the date you
take it to be.

## 2. Look it up

1. If a venue is named, call `overview` and find its id in `locationList`. If a room is named, call
   `list_spaces` with `match` set to its name to get the room's id and capacity.
2. Call `space_availability` with `date`, `days` (for a range), `party_size`, and `location` or `space` if
   known.
3. For each room read `capacity`, `fits_party`, the day's `open` hours, `busy` (bookings, holds and blocks,
   each with its from–to at the venue's clock) and `free`. A booking under `untimed_bookings` has a date but
   no time window: treat that room as uncertain that day and say so.
4. Room turnover time (`turnover_minutes`) is already subtracted around timed bookings.

## 3. Answer

Lead with the answer: "Yes — the Garden Room (seats 80) is free 17:00–24:00 on Sat 14 Nov." Then list the
other rooms that fit, then the ones that would fit but are busy (and with what), then the ones too small.
If nothing fits, say the nearest alternatives: a bigger room on another day in the range, or two rooms at
the same venue.

If a hold is in the way, give the holder's name and when it lapses, so the person can decide in Excellent.
