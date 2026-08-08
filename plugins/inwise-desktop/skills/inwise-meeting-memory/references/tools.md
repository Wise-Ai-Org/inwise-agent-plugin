# Inwise Desktop MCP tools

Use the smallest tool sequence that can answer the request.

## Read tools

| Tool | Use | Important inputs and notes |
|---|---|---|
| `get_connection_status` | Confirm the local server, version, calendar connection, and capabilities | No inputs |
| `search_meetings` | Find recorded or imported meetings by title, summary, or transcript text | `query`; optional `limit` |
| `get_meeting` | Read one meeting's metadata, attendees, summary, decisions, blockers, commitments, and excerpt | `meetingId` from `search_meetings` |
| `get_transcript` | Read an exact transcript in pages | `meetingId`; optional `offset`. Prefer `get_meeting` unless exact wording matters |
| `list_action_items` | Review tasks extracted from meetings or created manually | Optional `status`, `meetingId`, and `limit` |
| `get_action_item` | Read one complete action item and its execution history | `actionItemId` from `list_action_items` |
| `list_people` | Resolve a person and review contact frequency | Optional `search` and `limit` |
| `get_person` | Read relationship context, meetings, commitments, action items, and nudges | `personId` from `list_people` |
| `list_upcoming_meetings` | Resolve calendar events for near-term preparation | Optional `withinHours` and `limit` |
| `prepare_meeting` | Produce sourced preparation for a 1:1 or team meeting | Pass one of `personId`, `eventId`, or `title` plus `attendees` |

## Optional action writeback

These tools change local Inwise state. Action writeback is disabled by default in Inwise Desktop.

| Tool | Use | Required guardrail |
|---|---|---|
| `start_action_execution` | Record an explicitly approved execution plan | Approval must cover the objective, plan, tools, targets, and data shared |
| `append_action_outcome` | Store verified progress, completion, failure, and artifact links | Report only observed results; keep the same client identity |
| `update_action_status` | Change the linked action item's local status | Link the execution, use optimistic concurrency, and mark completed only with evidence |

Generate a stable, unique idempotency key for each write operation and reuse it only when retrying that exact operation.

## Evidence and privacy

- Preserve meeting titles and dates from returned `sources`.
- Do not expose internal IDs unless they help the user troubleshoot or continue a workflow.
- Do not fetch full transcripts speculatively.
- Remember that the server reads local data, but tool results are processed wherever the selected MCP client sends model context.
