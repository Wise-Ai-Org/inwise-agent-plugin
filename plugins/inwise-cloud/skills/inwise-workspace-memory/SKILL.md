---
name: inwise-workspace-memory
description: Use authenticated Inwise workspace memory to retrieve source-linked meeting, people, project, goal, action-item, and briefing context. Use when a request asks what changed, why a decision was made, who owes what, how a project is doing, what to discuss in a meeting, or any other question that should be grounded in the connected user's Inwise workspace.
---

# Inwise Workspace Memory

Use Inwise as the source of record and retrieve only the context needed for the current request. The hosted tools are read-only and operate within the connected user's workspace permissions.

## Establish identity and scope

1. Call `whoami` at the start of a new connection, after authentication changes, or when workspace identity is uncertain.
2. If authentication is required, ask the user to connect Inwise through the client's OAuth flow. Never request, display, or store a personal access token in conversation or source files.
3. Do not infer access from a plan name. Treat the tool result as authoritative for identity, workspace, and capabilities.
4. Read [references/tools.md](references/tools.md) when selecting a retrieval path or handling errors and pagination.

## Route the request

### Build a briefing

Use `get_briefing` for reader-specific preparation or a compact cross-entity update. Supplement it with entity tools only when the user needs more detail or source verification.

### Find meeting evidence

1. Call `search_meetings` with a narrow phrase or topic.
2. Call `get_meeting` for the strongest candidate records.
3. Preserve source timestamps and links. Request transcript-level material only when exact wording is necessary and the live tool schema supports it.

### Review a person

1. Resolve the person with `search_people`.
2. Call `get_person` for meeting history, unresolved work, commitments, and follow-up context.
3. Do not merge people solely because their display names match; use stable identities.

### Review a project

1. Call `list_projects` to resolve the project.
2. Call `get_project_status` for health, milestones, blockers, forecast signals, and linked evidence.
3. Separate the recorded status from recommendations or risk interpretation.

### Review work or goals

- Use `list_action_items` with the narrowest useful owner, status, meeting, person, or project filter supported by the live schema.
- Use `list_goals` for declared outcomes and the evidence affecting their current status.
- Do not claim that a task was changed or completed; this hosted surface is read-only.

### Search across entity types

Use `search` when the request spans entity types or the relevant type is unknown, then use `fetch` with the selected stable result identity. Prefer the entity-specific tools when the entity type is already clear.

## Preserve evidence and freshness

- Lead with the answer, briefing, or status—not a narration of tool calls.
- Attach source titles, timestamps, and links to consequential facts.
- Treat processing states as incomplete data rather than final empty results.
- If sources conflict, describe the conflict and dates instead of silently selecting one.
- Label inference and recommendations explicitly.
- Stop retrieving once the request has enough evidence; do not bulk-fetch an entire workspace.

## Recover correctly

- On `401 unauthorized`, reconnect once; do not loop on the same credential.
- On `403 insufficient_scope`, explain the missing permission and do not retry automatically.
- On `404 not_found`, search again or confirm that access still exists.
- On `429 rate_limited`, honor `Retry-After` and back off.
- Retry transient server errors only a bounded number of times.
