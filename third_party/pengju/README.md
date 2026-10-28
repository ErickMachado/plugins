# LitSource

Cursor plugin that connects agents to [LitSource](https://litsource.net) through LitSource's hosted [Model Context Protocol](https://modelcontextprotocol.io/) server.

Biomedical reverse literature search and citation verification for AI agents. Search PubMed/Crossref evidence for a claim, or verify a reference list for fabricated or mismatched citations.

## Install

1. Open **Cursor Settings → Plugins**.
2. Search for **LitSource**.
3. Click **Install**, then complete the LitSource sign-in prompt.

Or run `/add-plugin pengju` in chat.

## MCP

```json
{
  "mcpServers": {
    "pengju": {
      "type": "http",
      "url": "https://litsource.net/mcp"
    }
  }
}
```

The server supports OAuth 2.1. It also accepts a LitSource Agent Token sent as `Authorization: Bearer <token>`.

## Before you connect

You need a LitSource account. Sign up at https://litsource.net. To use a token instead of OAuth, create an Agent Token in LitSource (include the `usage:read` scope to check your credit balance).

## What agents can do

| Category | Capabilities |
| --- | --- |
| Evidence search | Find PubMed/Crossref literature supporting or refuting a biomedical claim |
| Citation verification | Check a reference list for fabricated or mismatched citations |
| Usage | Show your LitSource credit balance |

Searches that return results consume LitSource credits. The hosted runtime is the source of truth for tool names and schemas.

## Docs

- LitSource: https://litsource.net
- Server URL: https://litsource.net/mcp

Logo is the LitSource mark submitted by the publisher (https://pengju-marketplace-assets.vercel.app/litsource-marketplace.svg).

## License

MIT
