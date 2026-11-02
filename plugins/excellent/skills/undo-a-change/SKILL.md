---
name: undo-a-change
description: See and undo the changes Claude made in Excellent through this connection — a status moved, a room booked, a guest count changed, a contact or event added. Use for "undo that", "put the guest count back", "what did you change in Excellent?", "take back the booking you just made".
---

# Undo a change

## 1. Find the change

If this conversation made the change, use the `change_id` it returned. Otherwise call `recent_changes`: it
lists this person's changes, newest first, each with its `change_id`, a one-line summary, when it was made,
and whether it can still be undone. Read the matching ones back and ask which to undo when it isn't clear.

## 2. Undo it

Call `undo` with the `change_id`. A value it replaced is put back; a record it added is removed again.

It is refused, and the change stands, when:

- the record has changed since (someone edited it after) — say so; the later edit is kept on purpose;
- it was undone already, or is more than 30 days old;
- the person no longer has the permission the change needed.

Say what was undone, in the summary's words. Undo only what the person asks for, one change at a time.
