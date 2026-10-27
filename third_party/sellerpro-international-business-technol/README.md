# SellerPro 360

Cursor plugin that connects agents to [SellerPro 360](https://sellerpro360.com) through SellerPro 360's hosted [Model Context Protocol](https://modelcontextprotocol.io/) server.

SellerPro 360 is an Amazon seller platform for review request automation and other seller tools. Agents can use the supported SellerPro 360 features on the seller accounts you connect.

## Install

1. Open **Cursor Settings → Plugins**.
2. Search for **SellerPro 360**.
3. Click **Install**, then complete the SellerPro 360 sign-in prompt.

Or run `/add-plugin sellerpro-international-business-technol` in chat.

## MCP

```json
{
  "mcpServers": {
    "sellerpro-international-business-technol": {
      "type": "http",
      "url": "https://sellerpro360-mcp-proxy-v2.vercel.app/mcp"
    }
  }
}
```

## Before you connect

You need a SellerPro 360 account. Some tools also need an Amazon Seller Central account connected to SellerPro 360.

The hosted runtime is the source of truth for tool names and schemas.

## Docs

- SellerPro 360: https://sellerpro360.com
- Server URL: https://sellerpro360-mcp-proxy-v2.vercel.app/mcp

## License

MIT
