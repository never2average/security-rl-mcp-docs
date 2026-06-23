# `claim_next_agent_assignment`

Claims one assignment for a worker and creates a lease.

## Use This When

Use this when a worker is ready to perform one unit of experiment work.

## Inputs

- Worker role.
- Optional experiment ID, environment ID, and worker identity.

## What Changes In The RL Environment

One assignment moves from queued to leased, with ownership and lease expiry recorded.

## What The Agent Gets Back

Assignment ID, lease metadata, role-specific brief, environment ID, state version, and next instructions.

## Security Boundary

The returned assignment content must match the worker role. Red and Blue cannot receive the same state I/O. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `heartbeat_agent_assignment`
- `record_agent_assignment_result`
- `get_red_blue_agent_state`
