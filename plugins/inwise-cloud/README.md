# Inwise Cloud Agent Plugin

This package connects compatible AI clients to an authenticated Inwise workspace and bundles a source-grounded workflow for meetings, people, projects, goals, action items, and briefings.

## Connection

The Streamable HTTP endpoint is:

```text
https://inwise-mcp.azurewebsites.net/mcp
```

Interactive clients should use the endpoint's OAuth discovery flow. Do not put bearer tokens in plugin files or prompts.

## Package formats

- `plugin.json`, `mcp.json`, and `skills/` implement Agent Plugins 1.0.0.
- `.codex-plugin/plugin.json` and `.mcp.json` provide current ChatGPT and Codex packaging compatibility.

The hosted tools are read-only and enforce the connected user's workspace permissions. Retrieved information is processed according to the selected AI client's data practices.
