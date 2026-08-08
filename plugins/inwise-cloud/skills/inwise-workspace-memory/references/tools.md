# Inwise Cloud MCP tools

The live MCP schemas are authoritative. Use this routing guide without inventing unsupported parameters.

| Tool | Use |
|---|---|
| `whoami` | Confirm the authenticated identity, workspace, and available capabilities |
| `get_briefing` | Build compact reader-specific context across relevant entities |
| `search` | Search across entity types when the relevant type is unknown or mixed |
| `fetch` | Retrieve a selected general-search result by stable identity |
| `search_meetings` | Find meetings by title, summary, or transcript text |
| `get_meeting` | Retrieve meeting summary, decisions, blockers, commitments, and source evidence |
| `search_people` | Resolve people available to the connected user |
| `get_person` | Retrieve meeting history, commitments, unresolved work, and follow-up context |
| `list_projects` | Resolve projects accessible to the connected user |
| `get_project_status` | Retrieve project health, milestones, blockers, forecast signals, and evidence |
| `list_action_items` | Retrieve owned work using filters supported by the live schema |
| `list_goals` | Retrieve goals and evidence affecting their status |

## Authentication and permissions

- Prefer the client's OAuth flow. The endpoint advertises OAuth protected-resource metadata and authorization-code flow with PKCE.
- Never embed bearer tokens in `mcp.json`, prompts, logs, or source control.
- All results remain subject to the connected user's workspace and object authorization.

## Pagination and errors

- Follow returned cursors while preserving the original filters.
- Stop when enough evidence exists for the request.
- Do not turn an authorization error into a plan-upgrade recommendation.
- Do not expose meeting text, transcript text, prompts, or tool arguments in analytics or troubleshooting reports.
