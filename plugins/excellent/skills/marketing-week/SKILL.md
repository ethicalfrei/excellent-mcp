---
name: marketing-week
description: Plan a restaurant group's marketing week in Excellent — what's already queued, a post plan per venue and channel, social post and guest email drafts staged for a person to approve. Use for "plan this week's posts", "draft an Instagram post about the patio room", "marketing plan for the week", "email past hosts".
---

# Marketing week plan

This skill stages drafts only. Nothing is approved, published or emailed until a person approves it in
Excellent under Portfolio → Marketing; only Excellent's own engine sends, behind the group's live and consent
gates.

## 1. See what's already there

1. `marketing` — recent social posts (channel, status, slot) and guest campaigns (segment, status, delivery
   progress). Note what is already scheduled this week so you don't double up.
2. `overview` — the venues in `locationList` (their ids are what `draft_marketing_post` takes as
   `location`).
3. `agenda` with `days: 14` — upcoming events worth a teaser, and `list_events` with `status: "completed"`
   for recent ones worth a recap.

## 2. Propose a plan

A short table: day, venue (or group-wide), channel (instagram, facebook or linkedin), angle (for example "recap
of Saturday's rehearsal dinner", "patio room for fall parties"). Two to four posts a venue is plenty. If a
guest email fits, propose one with its segment: `past_event_hosts`, `recent_guests` or
`inquiries_never_booked`. Ask the person to confirm or change the plan before drafting.

## 3. Stage the drafts the person confirmed

- Social: `draft_marketing_post` with `channel`, `location` (omit for group-wide), `notes` (the angle) and,
  if the person gave a time, `schedule_at` as an ISO instant with a timezone. Leave `image_url` out unless
  they gave a specific picture; Excellent picks one from the group's own uploads. An Instagram post needs an
  image before it can be approved.
- Email: `draft_marketing_campaign` with `segment`, `notes` and optional `schedule_at`. It drafts in English
  and Spanish.

Each call stages a new draft, grounded only in the group's own events, recaps and reviews. Give back each
draft's review link. If a draft tool answers that the connection lacks draft access or the module is not
switched on, tell the person what the message says to do.

End with: "These are drafts in Portfolio → Marketing. Nothing goes out until you approve it there."
