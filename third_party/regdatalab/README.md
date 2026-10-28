# RegDataLab

Cursor plugin that connects agents to [RegDataLab](https://www.regdatalab.com) through RegDataLab's hosted [Model Context Protocol](https://modelcontextprotocol.io/) server (FDA Data MCP).

Search FDA facilities, inspections, recalls, warning letters, 510(k)s, and drug labels for a company.

## Install

1. Open **Cursor Settings → Plugins**.
2. Search for **RegDataLab**.
3. Click **Install**, then set your RegDataLab API key (below).

Or run `/add-plugin regdatalab` in chat.

## MCP

```json
{
  "mcpServers": {
    "regdatalab": {
      "type": "http",
      "url": "https://www.regdatalab.com/mcp",
      "headers": {
        "Authorization": "Bearer ${REGDATALAB_API_KEY}"
      }
    }
  }
}
```

Auth is a RegDataLab **API key** sent as a bearer token. Create an account at https://www.regdatalab.com and copy a key from your dashboard, then set it in **Dashboard → Plugins → Configure**. Do not commit the key. Never put an API key in the URL.

RegDataLab documents OAuth (paste the key on a consent page) for claude.ai and ChatGPT. This plugin follows the Cursor and Grok path: `Authorization: Bearer`.

## Before you connect

Create an account at [regdatalab.com](https://www.regdatalab.com) and copy an API key from your dashboard.

## What agents can do

| Category | Capabilities |
| --- | --- |
| Companies | Resolve a company to its FDA-registered facilities |
| Inspections | Look up inspections, NAI / VAI / OAI outcomes, and Form 483 observations |
| Enforcement | Search warning letters, recalls, and import alerts |
| Products | Look up 510(k), PMA, Drugs@FDA, NDC, and drug label records |
| Risk | Summarize manufacturing and compliance risk for a company |

The hosted runtime is the source of truth for tool names and schemas.

## Docs

- RegDataLab: https://www.regdatalab.com
- Connect guide: https://www.regdatalab.com/connect.md
- Server URL: https://www.regdatalab.com/mcp
- Privacy: https://www.regdatalab.com/privacy
- Terms: https://www.regdatalab.com/terms
- Support: https://www.regdatalab.com/support

## License

MIT
