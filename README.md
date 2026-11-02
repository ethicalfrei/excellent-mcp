<p align="center"><img src="logo-400.png" alt="Excellent" width="200"></p>

# Excellent MCP connector

Run your restaurant group's events, leads, invoices, staff schedule and marketing drafts from Claude and
other AI assistants.

[Excellent](https://beexcellent.ai) is the operating platform for restaurant groups: private dining and
events (inquiries, proposals, e-signed contracts, banquet event orders, deposits and invoices), room
availability, staff scheduling and training, and guest marketing. The Excellent connector is a hosted
[MCP](https://modelcontextprotocol.io) server that lets an AI assistant read your group's workspace and
stage drafts for your review when you ask it to.

| Server | URL | Sign-in | MCP Registry |
|---|---|---|---|
| Excellent | `https://beexcellent.ai/api/mcp` (Streamable HTTP) | OAuth with your Excellent account | `ai.beexcellent/excellent` |
| Excellent Reference (free) | `https://beexcellent.ai/api/mcp/public` (Streamable HTTP) | None | `ai.beexcellent/reference` |

- **Docs:** [beexcellent.ai/mcp](https://beexcellent.ai/mcp)
- **Claude plugin:** [`plugins/excellent`](plugins/excellent) adds nine ready-made workflows on top of the
  connector.

This repository holds documentation and the Claude plugin only. The connector is a hosted service, so there
is nothing to install or run.

## What you can ask for

- What the coming days hold by venue: bookings, holds about to lapse, payments coming due and inquiries
  nobody has answered
- One event in full: host and contacts, menu (and where the contract, proposal and BEOs disagree),
  documents and signatures, invoices, installments and payments
- Which rooms fit a party size and when they are free on a given day
- Search across events, leads, contacts, invoices, documents and rooms
- Lists of events, leads, contacts, rooms, invoices and documents
- The Events report: revenue booked, collected and outstanding, pace against goal, pipeline, win rate, lead
  sources and the per-venue rollup
- Who is on shift today, and the week's coverage, open shifts and warnings
- The marketing queue, and drafts of social posts (Instagram, Facebook, LinkedIn), bilingual guest emails
  and post-event thank-you cards

Every write is a **draft**. Nothing is published, approved or sent until a person does it in Excellent.
Booking, holding rooms, payments, publishing schedules and deleting anything stay in the Excellent app.

The **free reference server** needs no account. It answers how Excellent works from its own help text
(`excellent_help`), searches Excellent's public feature, comparison and blog pages
(`search_excellent_pages`), and can start a sample workspace with a one-time link for a person to claim
(`start_excellent_workspace`). It reads no restaurant group's data.

## Example prompts

> What does the next two weeks of private events look like across all our locations?

> Which new leads haven't been contacted yet, and what dates and party sizes are they asking about?

> Is the Garden Room free next Saturday evening for 60 people?

> Pull up the Adler gala: who's hosting, what's on the menu, and what's still owed?

> How are we pacing against this year's events revenue goal, and which location is behind?

> Draft an Instagram post about our patio room using our recent events.

## Connect

You need an Excellent account on the team of the group you want to connect. The assistant sees only that
group, acts as you with your role, and only after you approve the connection. To draft, tick draft access
when you approve.

### Claude

In Claude, go to **Settings → Connectors**, find Excellent in the directory and choose **Connect**. Or add a
custom connector with the URL `https://beexcellent.ai/api/mcp`. Sign in to Excellent and approve access.

For the free reference server, add a custom connector with `https://beexcellent.ai/api/mcp/public` and no
sign-in.

### Claude Code

Install the plugin:

```
/plugin marketplace add ethicalfrei/excellent-mcp
/plugin install excellent@excellent
```

Or add the connector on its own:

```sh
claude mcp add --transport http excellent https://beexcellent.ai/api/mcp
```

Then run `/mcp` in Claude Code and sign in.

### Cursor

Add to `~/.cursor/mcp.json` (or `.cursor/mcp.json` in a project):

```json
{
  "mcpServers": {
    "excellent": {
      "url": "https://beexcellent.ai/api/mcp"
    }
  }
}
```

### VS Code

Add to `.vscode/mcp.json`:

```json
{
  "servers": {
    "excellent": {
      "type": "http",
      "url": "https://beexcellent.ai/api/mcp"
    }
  }
}
```

### Other MCP clients

Any client that supports remote MCP servers with OAuth sign-in can use `https://beexcellent.ai/api/mcp`. A
client that only accepts a bearer token can use a scoped, expiring token you mint for yourself in Excellent
(see the [connector guide](https://beexcellent.ai/mcp)). The connector is tested in Claude.

## Your data

- You sign in with your own Excellent account and approve the connection. Each connection sees exactly one
  group and can only read and draft what your role allows.
- Connections use OAuth 2.1 with PKCE and short-lived access tokens. No tool takes or returns a password.
- You can see and disconnect your connections in Excellent under **Settings → AI assistant access**, or
  remove the connector from your AI app's settings.
- What you type in a chat is handled by your AI provider under its own terms. Excellent's
  [privacy policy](https://beexcellent.ai/privacy) and [security page](https://beexcellent.ai/security)
  cover your Excellent data.

## Support

Email [support@beexcellent.ai](mailto:support@beexcellent.ai) or see the
[connector guide](https://beexcellent.ai/mcp#support). Every error the connector returns ends with a code
in parentheses; include it when you write.
