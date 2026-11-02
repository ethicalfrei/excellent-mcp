# Excellent for Claude

Ready-made workflows for restaurant groups on [Excellent](https://beexcellent.ai), the operating platform
for private dining and events, marketing and staff. The plugin connects Claude to your Excellent workspace
and adds nine skills that know how to answer the questions an events, marketing or operations lead asks
every week, using Excellent's own tools.

You ask as yourself, with your own Excellent role. Claude reads your group's live data and stages drafts
for a person to review and approve in Excellent.

## Skills

| Skill | Ask it like |
|---|---|
| `morning-brief` | "What's on today across our venues?" |
| `lead-follow-up` | "Which inquiries haven't we answered, and do we have room for them?" |
| `private-event-space-check` | "Is the Garden Room free next Saturday evening for 60?" |
| `event-prep-sheet` | "Prep sheet for this week's events." |
| `thank-you-cards` | "Draft a thank-you card for last Saturday's rehearsal dinner." |
| `marketing-week` | "Plan this week's posts and draft an Instagram post about the patio room." |
| `money-owed` | "Which deposits are still outstanding?" |
| `weekly-owner-report` | "How are we pacing against this year's goal, and which location is behind?" |
| `staff-schedule-check` | "Is next week covered? Any open shifts?" |

## What it will and won't do

- Every skill but two is read-only. `thank-you-cards` and `marketing-week` stage drafts in Excellent's
  review queues and give you a link to each.
- Nothing is published, approved, emailed or sent from Claude. A thank-you card is published from the event
  page; a post or guest email is approved in Portfolio → Marketing, and only Excellent's consent-gated
  engine sends it.
- It never books, holds or blocks a room, records a payment, edits or publishes a shift, contacts a guest or
  deletes anything. Reply text for an inquiry is drafted in the chat for you to send yourself.
- Drafting needs a connection approved with draft access and a role that may draft marketing or event
  content; without them the draft tools refuse and say why.

## Use it

1. Install the plugin. In Claude Code:

   ```
   /plugin install excellent --marketplace ethicalfrei/excellent-mcp
   ```

   Then connect the **Excellent** connector (in Claude Code, run `/mcp`) and sign in to
   Excellent. You need an Excellent account on your group's team.
2. Ask in your own words, like the examples above.

## Data handling

This plugin sends data to exactly one place: **Excellent** (`https://beexcellent.ai`), through the connector
at `https://beexcellent.ai/api/mcp`, only when Claude calls an Excellent tool on your behalf. What it sends
is the tool's input (for example, a date and party size, or a status filter); what comes back is your
group's Excellent data that your account may see. You sign in with OAuth; no API key or password is stored
in the plugin. The skills are instructions only: they contain no code and send nothing on their own.

- Privacy policy: <https://beexcellent.ai/privacy>
- Security: <https://beexcellent.ai/security>
- Connector guide: <https://beexcellent.ai/mcp>
- Support: <support@beexcellent.ai>

## License

MIT — see [LICENSE](LICENSE).
