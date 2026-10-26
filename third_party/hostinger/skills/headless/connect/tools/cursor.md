---
name: headless-connect-cursor
description: "Cursor and Grok use the Hostinger plugin's hosted MCP. Do not install a second local server or write a hostinger entry into mcp.json."
---

## Goals

- Use the Hostinger plugin's hosted MCP. It is already registered.
- Sign-in is the client's OAuth prompt for `https://mcp.hostinger.com`. Do not start a second login.
- Don't provision hosting, create stores, install WordPress, or deploy by hand here — the skill does all of that. This entry stops once the hosted server answers.

## Step 1 — Use the plugin server

The plugin's `mcp.json` registers one server:

- name: `hostinger`
- url: `https://mcp.hostinger.com`
- placement: `server` (so Grok Bot dials the hosted path)

Call that server's tools (`search`, `execute`, `multi-execute`, or the operation tools it exposes). Do not install `@hostinger/mcp`, do not run `npx`, and do not spawn `hostinger-api-mcp`.

Do **not** add a `hostinger` entry to `.cursor/mcp.json` or `~/.cursor/mcp.json`. That name belongs to the plugin. A local stdio entry (`npx … hostinger-api-mcp`) collides with it and stores credentials in `~/.config/hostinger-mcp/credentials.json` instead of the plugin OAuth session.

Node is not required for this hosted server. Do not download `bootstrap.mjs`.

## Step 2 — Sign in

If a Hostinger tool call succeeds, you are signed in. Continue to Step 3.

If the client has not connected yet, ask the user to finish the Hostinger sign-in prompt Cursor or Grok shows for this plugin. Wait for that. Do not run `hostinger-api-mcp --login`.

`HOSTINGER_API_TOKEN` and a generic `API_TOKEN` are not this plugin's session. Leave them unset and use the OAuth prompt.

## Step 3 — Hand off

The headless skills are already installed with this plugin. Do not download them from GitHub. Open `headless/SKILL.md` next to `connect/` and follow its steps. The connect stage is done once the hosted server answers.
