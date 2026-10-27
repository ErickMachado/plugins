# Scale4

Cursor plugin that connects agents to [Scale4](https://scale4.app/agent4) CRM through Scale4's hosted [Model Context Protocol](https://modelcontextprotocol.io/) server.

Look up and update Scale4 CRM leads, review conversations, and access users, products, and CRM reports.

## Install

1. Open **Cursor Settings → Plugins**.
2. Search for **Scale4**.
3. Click **Install**, then authorize your Scale4 account when prompted.

Or run `/add-plugin scale4-ai` in chat.

## MCP

```json
{
  "mcpServers": {
    "scale4-ai": {
      "type": "http",
      "url": "https://mcp.scale4.app/mcp_scale4_plugin",
      "placement": "server"
    }
  }
}
```

## Before you connect

You need a Scale4 account. Actions run under the Scale4 account you authorize.

## What agents can do

| Category | Capabilities |
| --- | --- |
| Leads | Look up and update leads |
| Conversations | Review lead conversations |
| Users and products | Look up users and products |
| Reports | Access CRM reports |

The hosted runtime is the source of truth for tool names and schemas.

## Notes

- Write actions such as lead updates change records in your Scale4 account. Use a sandbox account and disposable records when testing.

## Docs

- Scale4: https://scale4.app/agent4
- Server URL: https://mcp.scale4.app/mcp_scale4_plugin

Logo is the image Scale4 submitted at `https://mcp.scale4.tools/playstore.svg`, referenced by URL. No local logo file is committed because the image could not be downloaded when this plugin was added.

## License

MIT
