# `get_red_blue_agent_brief`

Retrieves the role-specific instructions for a Red or Blue worker.

## Use This When

Use this after an assignment is claimed or when a worker needs its operating brief.

## Inputs

- Environment ID or assignment ID.
- Role, such as `red` or `blue`.
- Optional brief ID.

## What Changes In The RL Environment

This is a read operation.

## What The Agent Gets Back

Role instructions, scope, constraints, objective, expected output format, and linked environment metadata.

## Security Boundary

A Red brief must not include defender-only state, hidden issues, private credentials, or Blue fix history. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `get_red_blue_agent_state`
- `claim_next_agent_assignment`
