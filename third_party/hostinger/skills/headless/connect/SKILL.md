---
name: hostinger-headless-connect
description: "Connect step for the Hostinger Headless flow. In Cursor and Grok the Hostinger plugin already serves https://mcp.hostinger.com and the client handles OAuth — confirm that session and do not install a second server. Other coding tools run the bundled bootstrap.mjs (never a copy downloaded from GitHub), then the matching file under tools/. Triggers: connect to Hostinger, set up the Hostinger connector, start a headless build."
---

# Hostinger Headless Skill — connect

You are a coding agent, and this is a skill for you to execute. Follow the phases below in order.

In Cursor and Grok, connection is the Hostinger plugin's hosted MCP. Other coding tools (Claude Code, Codex, VS Code, and so on) still run the bundled bootstrap, then the matching file under `tools/`.


## Phase 0 — Plugin server (Cursor, Grok, Grok Bot)

The Hostinger plugin registers one MCP server:

- name: `hostinger`
- url: `https://mcp.hostinger.com`
- auth: the client's OAuth prompt. There is no API key to configure.

If this session is Cursor or Grok, **this phase is the whole connect step**:

1. Call a Hostinger tool (for example `hosting_orders_list`, or `search`). A successful call means the user is signed in — write `connect.json` and continue to Phase 3.
2. If the tools are missing, or the call asks for sign-in, ask the user to enable the Hostinger plugin and finish the sign-in card the client shows. Wait for that, then retry once.
3. Do **not** download `bootstrap.mjs`, run `npx @hostinger/mcp`, spawn `hostinger-api-mcp`, or write a `hostinger` entry into `.cursor/mcp.json` or `~/.cursor/mcp.json`. A stdio server with that name shadows the plugin and signs in again to `~/.config/hostinger-mcp/credentials.json`, which is not the plugin OAuth session.
4. Do **not** open `connect/tools/cursor.md` to install a local server. That file says the same thing: use the hosted server only.
5. Node is not required for the hosted server. Skip Phase 1 and Phase 2.

`API_TOKEN` and `HOSTINGER_API_TOKEN` are not how this plugin authenticates. Leave them unset and use the OAuth session.


## Phase 1 — Other tools: bundled bootstrap

Only for a coding tool that has no Hostinger plugin server (Claude Code, Codex, VS Code, Antigravity, Devin, or anything else not covered by Phase 0).

### Node (the single prerequisite)

The local Hostinger MCP server requires Node ≥ 20. Check it:

```bash
node -v
```

If that errors (Node not installed) or prints a version below 20, install or upgrade Node and re-check — do not try to work around it:

- macOS: `brew install node` (or `nvm install 22 && nvm use 22`)
- Linux: `nvm install 22 && nvm use 22` (or your distro's Node 20+ package)
- Windows: `winget install OpenJS.NodeJS.LTS` (or download from nodejs.org)

### Run the bundled bootstrap

Run the `bootstrap.mjs` that ships in this folder, next to this file. Do not download another copy from GitHub. It verifies the MCP server and handles sign-in, emitting one JSON event per line on stdout. Run it as a background/streaming process and relay its events to the user.

```bash
node "<directory of this SKILL.md>/bootstrap.mjs"
```

### Relay these events

The script emits one JSON object per line:

| Event | What to do                                                                                                                                                                                                                           |
| --- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `mcp_ok` | MCP server reachable — continue.                                                                                                                                                                                                     |
| `logged_in` | Already authenticated (`HOSTINGER_API_TOKEN` or a previous sign-in) — continue.                                                                                                                                                      |
| `awaiting_user` (`verificationUri`) | A browser window should have opened on the user's machine. Show the URL in plain prose and wait for the user to finish signing in. The OAuth callback lands on a localhost port, so the sign-in must be completed on this same machine. |
| `success` | Bootstrap done — continue to Phase 2. |
| `mcp_unreachable` / `login_failed` (with `detail`) | Stop and show the user the `detail`. Do not improvise a parallel setup by hand. |

If the environment has a `HOSTINGER_API_TOKEN` set (for example CI), the bootstrap reports `logged_in` immediately — no browser needed. A generic `API_TOKEN` is not a Hostinger credential and does not skip sign-in.

### Sign in or out manually

The bootstrap runs the sign-in for you. To run it directly, or to switch accounts, use the MCP's own commands. `--login` opens the browser to the Hostinger sign-in page, waits for the localhost callback, stores the credentials and exits. `--logout` revokes the stored credentials, so the next sign-in opens the browser again.

```bash
# With a global install (npm install -g @hostinger/mcp):
hostinger-api-mcp --login
hostinger-api-mcp --logout

# Without a global install:
npx --yes --package=@hostinger/mcp@latest hostinger-api-mcp --login
npx --yes --package=@hostinger/mcp@latest hostinger-api-mcp --logout
```

Credentials live in `~/.config/hostinger-mcp/credentials.json` (macOS/Linux) or `%APPDATA%\hostinger-mcp\credentials.json` (Windows) and are shared by every Hostinger MCP binary. OAuth works only in stdio mode; `--http` needs `HOSTINGER_API_TOKEN`. This credential store is for these non-plugin tools only. Do not use it, or these commands, in Cursor or Grok — Phase 0's OAuth session is the one that counts there.

## Phase 2 - Route to the specific tool instructions

Skip this phase in Cursor and Grok. Phase 0 already connected the hosted server.

| Tool        | Route                           |
|-------------|---------------------------------|
| Claude Code | `connect/tools/claude-code.md`  |
| Codex       | `connect/tools/codex.md`        |
| VS Code     | `connect/tools/vscode.md`       |
| Antigravity | `connect/tools/antigravity.md`  |
| Devin       | `connect/tools/devin.md`        |

If the user's tool isn't listed yet, and it is not Cursor or Grok, connect it the generic way (register the Hostinger MCP server for that tool, or drive `npx --yes --package=@hostinger/mcp@latest hostinger-api-mcp` over stdio) and continue. Never register that stdio server under the name `hostinger` in Cursor's MCP config.

## Phase 3 - Continue to Headless Hosting steps

After the hosted plugin server (Phase 0) or the tool route (Phase 2) is verified and you have access to the Hostinger MCP, go back to `headless/SKILL.md` and follow the steps section. The headless skills already ship with this plugin — do not download them from GitHub.


## Reference Sources

- https://mcpservers.org/servers/hostinger/api-mcp-server
- https://www.hostinger.com/connector
