# Excellent for Claude

Ready-made workflows for restaurant groups on [Excellent](https://beexcellent.ai), the operating platform
for private dining and events, marketing and staff. The plugin connects Claude to your Excellent workspace
and adds seventeen skills that know how to answer the questions an events, marketing or operations lead asks
every week, using Excellent's own tools — the connector's 73: 71 for your group's records (20 that read, 20
that draft, 31 that make changes you can undo) and two free read tools.

You ask as yourself, with your own Excellent role. Claude reads your group's live data, stages drafts for a
person to review and decide in Excellent, and — on a connection you allowed to — makes changes you can undo.

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
| `book-this-inquiry` | "Book the Kim inquiry into the Garden Room for Saturday." |
| `move-the-pipeline` | "Move this lead to tentative." / "They're 80 now, not 60." |
| `build-event-documents` | "Build the BEO for the Adler wedding." |
| `review-drafts` | "What's waiting for my approval?" |
| `undo-a-change` | "Undo that." / "What did you change in Excellent?" |
| `train-the-team` | "Add Maria as a server and build a wine-service course from our SOPs." |
| `build-partner-documents` | "Draft the Q3 investor update." / "Build a pro forma for a second location." |
| `import-a-list` | "Import these contacts from our old system." |

## What it will and won't do

- **Drafts** go to Excellent for a person: replies to inquiries, proposals, BEOs and contracts, invoices and
  their payment schedules, thank-you cards, posts and guest emails, pre-shift notes and shifts, training
  courses, event emails, Partner pro formas, pitch decks and investor updates, and staged imports. Claude can
  also revise a post, a campaign or an invoice that is still a draft. Each answer carries a review link that
  works only for you, signed in to Excellent; nothing is sent, published, finalized, shared or added until you
  decide it there.
- **Changes** (`book-this-inquiry`, `move-the-pipeline`, `train-the-team`, and the change steps in the space
  check, prep sheet, staff schedule, marketing week and Partner skills) commit in Excellent as you, one narrow
  change at a time, only on a connection approved with change access. Claude says what it will change before
  it does, and every change returns a `change_id` that `undo` puts back, once, for 30 days unless the record
  has changed since.
- In Partner documents Claude writes the words and Excellent computes every figure from your own records; a
  number in Claude's text never becomes a figure in a table.
- It never sends an email or text, takes or records a payment, publishes anything, approves its own drafts,
  commits an import, deletes a record or changes settings. Those stay with a person in Excellent.
- Each tool needs the access your connection was approved with (read; drafts; changes) and the role in
  Excellent the same action needs in the app; without them the tool refuses and says why.

## Use it

1. Install the plugin. In Claude Code:

   ```
   /plugin marketplace add ethicalfrei/excellent-mcp
   /plugin install excellent@excellent
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
