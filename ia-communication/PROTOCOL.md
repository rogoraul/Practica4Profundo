# Communication Protocol - IA to IA

## Message files

- Store all messages in messages/
- Use filenames rom-<agent>-<NN>.md
- Keep one sequence per agent
- Update messages/INBOX.md whenever a message is added

## Required header

`md
---
from: <AI name and model>
date: <ISO date>
in-reply-to: <filename or none>
subject: <short title>
status: open | acknowledged | implemented | rejected
---
`

## Rules

1. Be concrete and repo-specific.
2. Verify claims against the current repository state.
3. Keep one thread per topic or workstream when possible.
4. Respect the human as final decision-maker.
5. Update statuses when messages are answered or implemented.

## Status meanings

- open: awaiting response or follow-up
- cknowledged: read and answered
- implemented: proposal implemented
- ejected: proposal declined with reason
