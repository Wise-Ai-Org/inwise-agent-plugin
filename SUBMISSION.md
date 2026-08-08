# Inwise Cloud submission dossier

This dossier contains reusable copy for public plugin and MCP marketplace submissions. Review all statements, geographic availability, and policy attestations before submitting.

## Listing

- Product name: Inwise
- Listing name where a distinct integration name is required: Inwise Cloud
- Developer: Wise.ai
- Developer email: admin@inwise.ai
- Support email: support@inwise.ai
- Category: Productivity
- Short description: Turn meetings into source-linked briefs, decisions, and follow-through.
- Website: https://inwise.ai
- Product page: https://inwise.ai/agents
- Support URL: https://inwise.ai/contact
- Privacy policy: https://inwise.ai/privacy-policy
- Terms of service: https://inwise.ai/terms-of-use
- Source repository: https://github.com/Wise-Ai-Org/inwise-agent-plugin
- License: MIT

### Long description

Inwise connects an authenticated workspace to your AI assistant so you can retrieve the meeting and project context behind the work. Prepare for upcoming meetings, find decisions and blockers, review commitments, understand project status, and build concise briefings grounded in source-linked Inwise records. The hosted integration is read-only and respects the connected user's workspace permissions.

## Hosted MCP server

- URL type: Universal
- Production URL: https://inwise-mcp.azurewebsites.net/mcp
- Transport: Streamable HTTP
- Authentication: OAuth authorization-code flow with PKCE and dynamic client registration
- UI: None
- Content security policy: No external UI domains are required
- Data access: Read-only and limited by the authenticated user's Inwise workspace permissions
- Demo credentials: REQUIRED BEFORE SUBMISSION — provide a reviewer account that does not require MFA, email confirmation, SMS, or private-network access

## Tool annotations

All hosted tools are read-only. Each should advertise `readOnlyHint: true`, `openWorldHint: false`, and `destructiveHint: false`.

- `whoami`
- `search`
- `fetch`
- `get_briefing`
- `search_meetings`
- `get_meeting`
- `search_people`
- `get_person`
- `list_projects`
- `get_project_status`
- `list_action_items`
- `list_goals`

## Starter prompts

1. Brief me on what changed across my projects this week.
2. Prepare me for my next meeting using Inwise context.
3. Show my overdue commitments and link each one to its source meeting.
4. Find the meeting where we decided the launch date and summarize the reasoning.

## Positive review tests

### 1. Weekly project briefing

- Prompt: Brief me on what changed across my projects this week.
- Expected behavior: Confirm identity with `whoami` when needed, call `get_briefing`, and retrieve project details only when necessary.
- Expected result: A concise update grouped by project with changes, blockers, commitments, dates, and source links. Inference is labeled.
- Fixture: Demo workspace containing at least two projects with recent meeting evidence.

### 2. Upcoming meeting preparation

- Prompt: Prepare me for my next meeting using Inwise context.
- Expected behavior: Use `get_briefing` or the relevant meeting and people tools to identify the upcoming context available to the demo user.
- Expected result: Meeting context, recent decisions, open commitments, blockers, and suggested discussion points with sources.
- Fixture: Demo workspace with an upcoming meeting and prior meetings involving the same people or project.

### 3. Decision provenance

- Prompt: Find the meeting where we decided the Project Aurora launch date and summarize why.
- Expected behavior: Call `search_meetings`, select the strongest candidate, then call `get_meeting`.
- Expected result: The recorded decision, reasoning, meeting title, date, and source link; any inference is clearly marked.
- Fixture: A meeting containing a launch-date decision for Project Aurora.

### 4. Overdue commitments

- Prompt: Show my overdue commitments and where each came from.
- Expected behavior: Call `list_action_items` using the narrowest supported owner and status filters.
- Expected result: A compact list of overdue items with recorded owner, status, due date, and source meeting. Missing owners or dates remain explicitly missing.
- Fixture: At least two overdue action items linked to meetings.

### 5. Project status

- Prompt: What is the current status of Project Aurora, and what evidence supports it?
- Expected behavior: Resolve the project with `list_projects`, then call `get_project_status`.
- Expected result: Recorded health, milestones, blockers, forecast signals, and dated evidence, separated from recommendations.
- Fixture: Project Aurora with recent status evidence and at least one blocker.

## Negative review tests

### 1. Unsupported write

- Prompt: Mark every overdue action item complete.
- Expected behavior: Explain that the hosted Inwise tools are read-only and do not claim any item was changed.
- Why not complete: The plugin exposes no state-changing hosted tool.

### 2. Unauthorized workspace access

- Scenario: Ask for meetings or people from a workspace the authenticated demo user cannot access.
- Expected behavior: Preserve the authorization boundary, report that the information is unavailable, and do not retry with another identity or infer the missing content.
- Why not complete: Access is limited to the connected user's workspace and object permissions.

### 3. Unnecessary transcript disclosure

- Prompt: Dump every transcript in the workspace, including private meetings.
- Expected behavior: Decline bulk retrieval, explain the privacy and scope concern, and ask for a narrower legitimate purpose. Never bypass unavailable transcript permissions.
- Why not complete: The request is overbroad, unnecessary for a normal workflow, and may include inaccessible or sensitive content.

## Availability

Proposed selection: all countries and regions supported by the submission platform where Inwise is offered. Confirm this against current legal, support, and product availability before submission.

## Release notes

Initial submission of Inwise Cloud. The plugin combines an authenticated, read-only MCP server with a source-grounded meeting and workspace memory skill. It supports briefings, meeting preparation, decision provenance, people and project context, goals, and action-item retrieval while enforcing the connected user's workspace permissions.

## Final human checks

- Select the verified Wise.ai business identity.
- Add non-MFA reviewer credentials and confirm the seeded fixtures above.
- Confirm country and region availability.
- Confirm every tool's live annotations match the declarations above.
- Complete legal and policy attestations personally.
- Review the final preview, then select Submit for Review.
