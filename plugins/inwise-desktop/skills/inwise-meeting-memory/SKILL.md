---
name: inwise-meeting-memory
description: Use local Inwise Desktop meeting memory to prepare for upcoming meetings, retrieve past meeting context, trace decisions and blockers, review people and relationships, and inspect or act on commitments. Use when a request mentions meetings, attendees, transcripts, decisions, action items, follow-ups, relationship history, or meeting preparation and Inwise data can supply the answer.
---

# Inwise Meeting Memory

Use the Inwise MCP tools as a durable meeting-memory layer. Retrieve the minimum context needed and keep every factual claim traceable to Inwise records.

## Start safely

1. Call `get_connection_status` when connection state or capabilities are uncertain.
2. If Inwise is unavailable, ask the user to open Inwise Desktop, then enable **Settings > Connect to AI**. Do not silently substitute chat history or invented context.
3. Treat read operations as the default. Do not use action-writeback tools unless the user explicitly asks to perform an action and approves the exact plan.
4. Prefer summaries and structured insights over verbatim transcripts. Use `get_transcript` only when exact wording is material or the user requests it; transcript text will be sent wherever the MCP client sends model context.

Read [references/tools.md](references/tools.md) when selecting tools, constructing inputs, or handling optional action writeback.

## Route the request

### Prepare for an upcoming meeting

1. Call `list_upcoming_meetings` to resolve the event.
2. Call `prepare_meeting` with its `eventId`.
3. Present recent context, decisions, unresolved blockers, mutual commitments, and suggested discussion points.
4. Include the meeting title and date behind each consequential point.

For a named 1:1 without a calendar event, resolve the person with `list_people`, then call `prepare_meeting` with `personId`.

### Find what happened or why

1. Call `search_meetings` with the user's key phrase.
2. Call `get_meeting` for the best candidate records.
3. Use `get_transcript` only when the exact words are necessary.
4. Separate recorded facts from inference. If records conflict, show the conflict and dates instead of choosing silently.

### Review a person or relationship

1. Resolve the person with `list_people`.
2. Call `get_person` for relationship context, recent meetings, commitments, and nudges.
3. Avoid inferring sentiment, intent, or relationship health beyond the returned evidence.

### Review commitments

1. Call `list_action_items` with the narrowest useful status or meeting filter.
2. Call `get_action_item` before recommending action on an individual item.
3. Distinguish explicit owners from inferred or missing owners.
4. Never mark an item complete merely because work was proposed.

## Produce useful answers

- Lead with the answer or briefing, not a narration of tool calls.
- Use compact sections appropriate to the request: context, changes, decisions, commitments, blockers, and next questions.
- Attach dates and source meeting titles to important facts.
- State when no supporting record was found.
- Label recommendations as recommendations rather than recorded decisions.

## Guard action execution

When the user asks to carry out an Inwise action item:

1. Retrieve the full action item and current `updatedAt` value.
2. Show the exact objective, steps, external tools, targets, and meeting-derived data that would be shared.
3. Obtain explicit approval for that exact scope before calling `start_action_execution`.
4. Perform only the approved external work through the client's separately available tools.
5. Call `append_action_outcome` with verified results and artifact links.
6. Call `update_action_status` only when the verified outcome supports the new status; pass `expectedUpdatedAt` when available.

Do not broaden approval, fabricate an approving identity, or claim an external action succeeded without evidence.
