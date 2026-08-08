# Inwise Agent Plugins

Portable packages that connect supported AI clients to Inwise meeting and workspace memory.

- [`inwise-desktop`](plugins/inwise-desktop/): local meeting memory from Inwise Desktop on the same computer.
- [`inwise-cloud`](plugins/inwise-cloud/): authenticated, source-linked memory from an Inwise workspace.

Both packages include Agent Plugins 1.0.0 manifests and compatibility manifests for Codex, Claude Code, Cursor, Gemini CLI, GitHub Copilot CLI, and Grok Build. Each package should be installed separately because its endpoint, authentication model, and tool surface differ.

## Install from this repository

### Codex

```text
codex plugin marketplace add Wise-Ai-Org/inwise-agent-plugin
```

### Claude Code

```text
/plugin marketplace add Wise-Ai-Org/inwise-agent-plugin
```

### GitHub Copilot CLI

```text
copilot plugin marketplace add Wise-Ai-Org/inwise-agent-plugin
```

### Gemini CLI

The repository root installs Inwise Cloud:

```text
gemini extensions install https://github.com/Wise-Ai-Org/inwise-agent-plugin
```

### Cursor and Grok Build

Use the repository URL in the client's plugin or marketplace installation flow. The repository includes native marketplace manifests for both clients.

## Public submission

[`SUBMISSION.md`](SUBMISSION.md) contains the reusable listing copy, tool annotations, prompts, review tests, and final human checks for public marketplace review.

[`submissions/README.md`](submissions/README.md) is the final-action handoff for each directory, registry, and review workflow.

Canonical repository: https://github.com/Wise-Ai-Org/inwise-agent-plugin
