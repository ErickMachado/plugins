# Changelog

All notable changes to this plugin will be documented here.

## 1.0.2 — setup form copy

- Plugin variables: `DATABRICKS_HOST` is titled "Workspace hostname" and takes only the bare hostname (leave out `https://`, any path, and any port). Added placeholder examples for `DATABRICKS_HOST`, `CLIENT_ID`, and `CLIENT_SECRET`. Variable keys, types, and required fields are unchanged; `CLIENT_SECRET` stays optional for public clients.

## 1.0.1 — Genie icon

- Logo: replaced the Databricks mark with Databricks' official Genie icon from https://www.databricks.com/sites/default/files/2026-05/icon-genie.svg, rendered at 192×192 on a transparent background. No server or client-version changes.

## 1.0.0 — initial release

- Added the `databricks-genie-one` MCP server pointing at `https://${DATABRICKS_HOST}/ai-gateway/mcp-services/system.ai.genie_one_mcp`.
- Declared `DATABRICKS_HOST`, `CLIENT_ID`, and optional `CLIENT_SECRET` plugin variables for the team's Databricks OAuth app connection, since Databricks has no dynamic client registration.
- Requests the `ai-gateway` and `offline_access` scopes.
- Logo: Databricks' official mark, from the `databricks` GitHub organization.
