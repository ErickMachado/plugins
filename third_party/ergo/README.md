# Ergo

Cursor plugin that connects agents to [Ergo](https://joinergo.com) through Ergo's hosted [Model Context Protocol](https://modelcontextprotocol.io/) server.

Ask Ergo about your pipeline, deals, accounts, and meetings, with answers grounded in your own CRM records, call transcripts, notes, and email.

## Install

1. Open **Cursor Settings → Plugins**.
2. Search for **Ergo**.
3. Click **Install**, then complete the Ergo sign-in prompt.

Or run `/add-plugin ergo` in chat.

## MCP

```json
{
  "mcpServers": {
    "ergo": {
      "type": "http",
      "url": "https://api.joinergo.com/api/mcp"
    }
  }
}
```

Auth is OAuth with dynamic client registration. Sign in with Google or a one-time email code; there is no API key to configure.

## Before you connect

You need an Ergo account. Ergo only shows data you can already see in the Ergo dashboard.

## What agents can do

| Tool | Capability |
| --- | --- |
| Ask Ergo | Ask questions and follow-ups about pipeline, deals, accounts, and meetings |
| Get Ergo Result | Fetch the answer to an Ask Ergo request when it is ready |
| Query Meeting Transcripts | Find meetings by title, attendee, or date and read their transcripts |

The hosted runtime is the source of truth for tool names and schemas.

## Notes

- Ergo may search the web and draft emails.
- CRM and calendar changes apply only after you approve them in Ergo.

## Docs

- Ergo: https://joinergo.com
- MCP docs: https://support.joinergo.com/articles/6631055248-integrations-mcp-external-agent-tools
- Server URL: https://api.joinergo.com/api/mcp

## License

MIT
