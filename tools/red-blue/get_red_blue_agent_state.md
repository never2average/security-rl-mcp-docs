# `get_red_blue_agent_state`

Retrieves the role-scoped state view for a Red or Blue worker.

## Use This When

Use this when an agent needs application state during inference.

## Inputs

- Environment ID.
- Role.
- Optional state version and assignment ID.

## What Changes In The RL Environment

This is a read operation.

## What The Agent Gets Back

A sanitized state view appropriate for the role, plus state version metadata.

## Security Boundary

Red sees public attack-facing state. Blue sees defender state and can receive sanitized application context and Red issues when allowed. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `get_red_blue_agent_brief`
- `log_red_team_issue`
- `get_blue_team_fix_queue`
