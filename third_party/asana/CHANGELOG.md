# Changelog

All notable changes to this plugin will be documented here.

## 1.0.0 — initial release

- Logo: Asana's official mark, from Asana's Cursor plugin.
- Added the `asana` MCP server pointing at `https://mcp.asana.com/v2/mcp`.
- Declared required `CLIENT_ID` and `CLIENT_SECRET` plugin variables and forwarded them through MCP auth, since Asana's V2 server requires a pre-registered MCP app and does not support Dynamic Client Registration.
