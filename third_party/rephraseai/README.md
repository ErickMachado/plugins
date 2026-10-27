# Rephrase AI

Cursor plugin that connects agents to [Rephrase AI](https://www.rephraseai.com/) through Rephrase AI's hosted [Model Context Protocol](https://modelcontextprotocol.io/) server.

Turn a rough draft into what you meant to say without leaving Grok Bot or Cursor. Rephrase AI rewrites your text in the voice you pick, keeps your meaning, and saves every rewrite to your Rephrase AI History.

## Install

1. Open **Cursor Settings → Plugins**.
2. Search for **Rephrase AI**.
3. Click **Install**, then complete the Rephrase AI sign-in prompt.

Or run `/add-plugin rephraseai` in chat.

## MCP

```json
{
  "mcpServers": {
    "rephraseai": {
      "type": "http",
      "url": "https://www.rephraseai.com/cursor/mcp",
      "placement": "server"
    }
  }
}
```

Auth is OAuth sign-in to Rephrase AI. There is no client ID, client secret, or API key to configure.

## Before you connect

You need a Rephrase AI account.

## Example

> Use Rephrase AI to make this more professional: hey, can u send me the report by friday?

The hosted runtime is the source of truth for tool names and schemas.

## Docs

- Rephrase AI: https://www.rephraseai.com/
- Server URL: https://www.rephraseai.com/cursor/mcp

The logo points at Rephrase AI's hosted icon (`https://www.rephraseai.com/icon0.svg`). rephraseai.com was unreachable from the build environment when this plugin was added, so no local logo file is committed yet.

## License

MIT
