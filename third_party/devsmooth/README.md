# AI Chat for Website

Cursor plugin that connects agents to [AI Chat for Website](https://www.aichatforwebsite.com) by DevSmooth Softwares Inc through its hosted [Model Context Protocol](https://modelcontextprotocol.io/) server.

AI Chat for Website adds an AI assistant and live chat to your site. This plugin lets agents see your sites, visitors, conversations, leads, and unanswered questions, reply to or close live chats, update leads, add Q&A answers, and recrawl your site.

## Install

1. Open **Cursor Settings → Plugins**.
2. Search for **AI Chat for Website**.
3. Click **Install**, then complete the AI Chat for Website sign-in prompt.

Or run `/add-plugin devsmooth` in chat.

## MCP

```json
{
  "mcpServers": {
    "devsmooth": {
      "type": "http",
      "url": "https://app.aichatforwebsite.com/mcp"
    }
  }
}
```

Auth is OAuth 2.1 with PKCE and dynamic client registration, so Cursor prompts for AI Chat for Website sign-in when the plugin connects. There is no client ID or API key to configure.

## Before you connect

You need an AI Chat for Website account. The connector acts with your own portal role, so it sees exactly what your portal shows. Untick **Write** on the consent screen for read-only access.

## What agents can do

| Category | Capabilities |
| --- | --- |
| Sites | List your sites and recrawl site content |
| Conversations | Read conversations, reply to live chats, and close them |
| Visitors | Look up site visitors |
| Leads | List and update leads |
| Knowledge | Review unanswered questions and add Q&A answers |

The hosted runtime is the source of truth for tool names and schemas.

## Docs

- AI Chat for Website connectors: https://www.aichatforwebsite.com/docs/connectors/
- Server URL: https://app.aichatforwebsite.com/mcp

The logo points at the publisher's hosted favicon (`https://app.aichatforwebsite.com/favicon.svg`). The publisher's domains were unreachable when this plugin was added, so no image file was downloaded.

## License

MIT
