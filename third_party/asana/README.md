# Asana

Cursor plugin that connects agents to [Asana](https://asana.com) through Asana's official V2 [Model Context Protocol](https://modelcontextprotocol.io/) server.

Create, search, and update tasks, projects, and portfolios in the signed-in Asana account.

## Install

1. Open **Cursor Settings → Plugins**.
2. Search for **Asana**.
3. Click **Install**, then set the Client ID and Client Secret (below) and complete the Asana sign-in prompt.

Or run `/add-plugin asana` in chat.

## MCP

```json
{
  "mcpServers": {
    "asana": {
      "type": "http",
      "url": "https://mcp.asana.com/v2/mcp",
      "auth": {
        "CLIENT_ID": "${CLIENT_ID}",
        "CLIENT_SECRET": "${CLIENT_SECRET}"
      }
    }
  }
}
```

The server is `https://mcp.asana.com/v2/mcp`. Leave `scopes` unset. Asana MCP apps authorize with the default grant, and an explicit `scope` parameter is rejected.

## Setup

Asana's V2 server does not support Dynamic Client Registration. Each connection uses an MCP app you register, and that app's client id and client secret.

1. Sign in at the [Asana developer console](https://app.asana.com/0/my-apps) and click **Create new app**.
2. Choose the app type **MCP app**. Tokens from a standard API app are rejected by this server.
3. Under **OAuth**, add every redirect URL for the surfaces you use. Asana matches the redirect exactly, including the path and with no trailing slash:

   | Surface | Redirect URL |
   | --- | --- |
   | Desktop | `http://localhost:8787/callback` |
   | Web and Cloud Agents | `https://www.cursor.com/agents/mcp/oauth/callback` |
   | Older desktop builds | `cursor://anysphere.cursor-mcp/oauth/callback` |

4. Under **Manage distribution**, choose **Any workspace** or **Specific workspaces** and add each workspace people will connect from. Save. An app with no workspace selected reports that it is not available to that workspace.
5. Copy the **Client ID** and **Client Secret**.
6. In **Dashboard → Plugins → Configure**, set **Asana Client ID** and **Asana Client Secret**.
7. Complete the Asana sign-in when Cursor prompts.

Asana asks for a unique client id and secret per developer. On a team marketplace an admin can enter one app for the team; each member still signs in with their own Asana account, and tool calls run with that member's permissions.

Resetting the client secret in Asana invalidates the old one. Enter the new secret in Cursor before connecting again.

## What agents can do

Actions run as the signed-in Asana user. An MCP app has no read-only mode and no granular scopes: authorizing grants the tools the server exposes, and Asana still limits each call to what that user can already see.

| Area | Capabilities |
| --- | --- |
| Tasks | Search, read, create, update, comment on, and delete tasks |
| Projects | Read and create projects, and post project status updates |
| Portfolios | Read portfolios and status |
| Account | List the signed-in user's workspaces |

`search_tasks` requires a Premium workspace. Other plans use the task-list tools instead. The hosted server is the source of truth for tool names and schemas.

## Troubleshooting

| Symptom | What to check |
| --- | --- |
| `redirect_uri` does not match | The Asana app is missing the exact redirect for that surface. Register the URLs in the table above and save. |
| `invalid_client` | The Client ID or Client Secret does not match the MCP app, or the secret was reset in Asana and not updated in Cursor. |
| Invalid scope | The request is sending a `scope` value. This plugin leaves scopes unset on purpose. |
| App is not available to your workspace | **Manage distribution** does not include that workspace. |
| Tools never appear | In **Cursor Settings → Tools & MCP**, confirm **asana** is listed and enabled. |

If a workspace uses Asana app management, a super admin may need to allow the MCP app before sign-in can finish.

## Docs

- Connecting Cursor to Asana's V2 server: https://developers.asana.com/docs/connecting-mcp-clients-to-asanas-v2-server#cursor
- Asana developer console: https://app.asana.com/0/my-apps
- Server URL: https://mcp.asana.com/v2/mcp

Logo is Asana's official mark, from [Asana's Cursor plugin](https://github.com/Asana/cursor-marketplace-plugin).

## License

MIT
