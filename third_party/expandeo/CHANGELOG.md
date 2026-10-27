# Changelog

All notable changes to this plugin will be documented here.

## 1.0.1 — hosted placement

- Declares `"placement": "server"` on the MCP server so Grok Bot (desktop and mobile) dials it through the hosted MCP path. Without it the row stays UNDECIDED and never shows a connect / sign-in card in Grok Bot.

## 1.0.0 — initial release

- Added the `expandeo` MCP server pointing at Expandeo's hosted Streamable HTTP endpoint (`https://mcp.expandeo.com`).
- No auth: the server is read-only and needs no account or API key.
