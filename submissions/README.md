# Submission handoff

This folder contains the values needed to finish each public-directory submission. The repository and immutable `v0.1.0` release are already public. Final submission actions, legal attestations, reviewer credentials, and any marketplace-specific publisher identity remain for an authorized Inwise representative.

## Destinations

| Destination | Prepared input | Final action intentionally left undone |
| --- | --- | --- |
| OpenAI Plugin Directory | [`../SUBMISSION.md`](../SUBMISSION.md), hosted MCP URL, OAuth metadata, positive/negative tests, and logos | Sign in, select the verified Wise.ai identity, add reviewer credentials, complete domain verification and attestations, then submit for review |
| Claude community marketplace | Valid `.claude-plugin` manifests, public repository, release tag, and listing copy | Sign in to the Console or Team/Enterprise form and submit `plugins/inwise-cloud` |
| Cursor Marketplace | Valid `.cursor-plugin` manifests and public repository | Sign in, enter the repository URL, accept publisher terms, and submit the application |
| Awesome Copilot | [`awesome-copilot.md`](awesome-copilot.md) | Sign in, paste the prepared issue-form values, personally check the policy attestations, and create the issue |
| Grok Build official marketplace | A validated branch is pushed to `Shravani889/plugin-marketplace`; see [`grok-build.md`](grok-build.md) | Open the prepared compare page, review the diff, and create the pull request |
| MCP Registry | Valid root [`../server.json`](../server.json) | Authenticate `mcp-publisher` with GitHub and run `mcp-publisher publish` |
| Gemini CLI Extension Gallery | Valid root [`../gemini-extension.json`](../gemini-extension.json) | Add the GitHub topic `gemini-cli-extension`; the gallery crawler discovers it automatically |
| skills.sh | Both installable Agent Skills are present in the public repository | No publisher form; discovery follows public installation activity |
| Codex, Claude, Cursor, Copilot, and Grok custom marketplaces | Root marketplace manifests are already public | Users can add the repository directly; no central-review action is required |

## Canonical release

- Repository: https://github.com/Wise-Ai-Org/inwise-agent-plugin
- Release: https://github.com/Wise-Ai-Org/inwise-agent-plugin/releases/tag/v0.1.0
- Release tag: `v0.1.0`
- Release commit: `97192fab47aa43a69ab0345b68e7881b011a5aa9`
- Hosted plugin path: `plugins/inwise-cloud`
- Desktop plugin path: `plugins/inwise-desktop`
