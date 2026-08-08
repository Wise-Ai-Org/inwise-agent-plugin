# Inwise Desktop Agent Plugin

This package connects compatible AI clients to the meeting memory stored by Inwise Desktop and bundles a workflow for meeting preparation, decision retrieval, relationship context, and commitment follow-through.

## Requirements

- Inwise Desktop with the local MCP server feature
- **Settings > Connect to AI** enabled
- Inwise running on the same computer as the AI client

The MCP endpoint is `http://127.0.0.1:43117/mcp` and accepts loopback connections only.

## Package formats

- `plugin.json`, `mcp.json`, and `skills/` implement Agent Plugins 1.0.0.
- `.codex-plugin/plugin.json` and `.mcp.json` provide current ChatGPT and Codex packaging compatibility.

Reading is local to the Inwise server, but any retrieved result is processed according to the selected AI client's data practices. Full transcript access is separate from summary access. Optional action writeback is disabled by default and requires explicit approval.
