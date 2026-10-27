# Greenland AI

Cursor plugin that connects agents to [Greenland AI](https://greenlandai.ai) through Greenland AI's hosted [Model Context Protocol](https://modelcontextprotocol.io/) server.

The physical world as queryable data: companies, resource deposits, infrastructure assets, projects, and commodities, with graph traversal across supply chains, ownership, and dependencies.

## Install

1. Open **Cursor Settings → Plugins**.
2. Search for **Greenland AI**.
3. Click **Install**, then set your Greenland AI API key.

Or run `/add-plugin greenlandai` in chat.

## MCP

```json
{
  "mcpServers": {
    "greenlandai": {
      "type": "http",
      "url": "https://mcp.greenlandai.ai/mcp",
      "headers": {
        "X-API-Key": "${GREENLANDAI_API_KEY}"
      }
    }
  }
}
```

Tool calls send a Greenland AI API key as the `X-API-Key` header (`${GREENLANDAI_API_KEY}`). Set the key in **Dashboard → Plugins → Configure**. Without one, calls return a 401 message explaining how to get a key.

## Before you connect

You need a Greenland AI account and API key with a platform credit balance.

## What agents can do

| Category | Capabilities |
| --- | --- |
| Companies | Search companies and read company profiles |
| Assets | Look up resource deposits, infrastructure assets, projects, and commodities |
| Graph | Traverse supply chains, ownership, and dependency relationships |
| Billing | Get a price quote before running a call |

The hosted runtime is the source of truth for tool names and schemas.

## Notes

- Calls are priced per call in platform credits. `billing_quote` returns the maximum price before a call runs, and undelivered work is refunded automatically.

## Docs

- Greenland AI: https://greenlandai.ai
- Server URL: https://mcp.greenlandai.ai/mcp

## License

MIT
