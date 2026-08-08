# Grok Build official-marketplace submission

The validated submission branch is already pushed to the user's fork:

- Upstream: https://github.com/xai-org/plugin-marketplace
- Fork branch: https://github.com/Shravani889/plugin-marketplace/tree/inwise-cloud
- Start PR: https://github.com/xai-org/plugin-marketplace/compare/main...Shravani889:plugin-marketplace:inwise-cloud?expand=1

The branch adds the following remote, immutable catalog entry and the generated component index:

```json
{
  "name": "inwise-cloud",
  "description": "Inwise meeting and workspace memory integration. Prepare source-linked briefs, trace decisions, review commitments, and understand project context through an authenticated read-only MCP server.",
  "category": "productivity",
  "source": {
    "source": "url",
    "url": "https://github.com/Wise-Ai-Org/inwise-agent-plugin.git",
    "sha": "97192fab47aa43a69ab0345b68e7881b011a5aa9",
    "path": "plugins/inwise-cloud"
  },
  "homepage": "https://inwise.ai/agents",
  "keywords": ["inwise", "inwise meetings", "inwise workspace", "inwise briefing"],
  "domains": ["inwise.ai"]
}
```

Upstream validation completed successfully:

- `python scripts/generate-plugin-index.py`
- `python scripts/validate-catalog.py`
- `python scripts/generate-plugin-index.py --check`

Suggested PR title: `Add Inwise Cloud plugin`

Suggested PR body:

> Adds Inwise Cloud as a third-party productivity plugin. It combines a source-grounded meeting/workspace-memory skill with an authenticated, read-only Streamable HTTP MCP server. The hosted tools respect the connected user's Inwise workspace permissions. Source: https://github.com/Wise-Ai-Org/inwise-agent-plugin/tree/v0.1.0/plugins/inwise-cloud

Review the fork diff and create the pull request from the compare link; no PR has been opened yet.

