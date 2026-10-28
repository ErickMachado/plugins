# Changelog

All notable changes to this plugin will be documented here.

## 1.0.0 — initial release

- Added the `regdatalab` MCP server pointing at RegDataLab's hosted Streamable HTTP endpoint (`https://www.regdatalab.com/mcp`).
- Auth uses a RegDataLab API key supplied by the user as an `Authorization: Bearer` header (`${REGDATALAB_API_KEY}`).
- Logo: references the publisher-submitted URL. The file could not be downloaded when this plugin was added, so no local copy is committed yet.
