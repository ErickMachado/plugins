# Levea

Cursor plugin that connects agents to [Levea](https://www.livecore.ai) through Levea's hosted [Model Context Protocol](https://modelcontextprotocol.io/) server.

Edit videos from plain-language prompts: clips, captions, reframing, voiceover, and export.

## Install

1. Open **Cursor Settings → Plugins**.
2. Search for **Levea**.
3. Click **Install**, then set your Levea API key (below).

Or run `/add-plugin levea` in chat.

## MCP

```json
{
  "mcpServers": {
    "levea": {
      "type": "http",
      "url": "https://api.livecore.ai/api/v1/misc/mcp",
      "headers": {
        "Authorization": "Bearer ${LEVEA_API_KEY}"
      },
      "placement": "server"
    }
  }
}
```

Auth is a Levea **API key** sent as `Authorization: Bearer`. Generate one at https://livecore.ai, then set it in **Dashboard → Plugins → Configure**. Do not commit the key. Listing tools works without a key; video edits require it.

## Before you connect

You need a Levea account and an API key from https://livecore.ai.

## What agents can do

| Category | Capabilities |
| --- | --- |
| Editing | Describe an edit in plain language and get a finished MP4 |
| Clips | Cut short clips from long videos and reframe to 9:16 with face tracking |
| Captions | Add word-by-word animated captions from caption templates |
| Effects | Chroma key, background removal, B-roll, and silence removal |
| Audio | AI voiceover and music |
| Export | Export for multiple platforms |

The hosted runtime is the source of truth for tool names and schemas.

## Docs

- Levea: https://www.livecore.ai
- Source and docs: https://github.com/brajendrak00068/agentic-ai-video-production
- Server URL: https://api.livecore.ai/api/v1/misc/mcp

## License

MIT
