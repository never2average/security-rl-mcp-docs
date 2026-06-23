# `heartbeat_agent_assignment`

Keeps a claimed assignment lease alive while the worker is still active.

## Use This When

Use this during long-running tasks so the daemon does not requeue active work.

## Inputs

- Assignment ID.
- Worker ID or lease token.
- Optional progress note.

## What Changes In The RL Environment

The assignment lease timestamp and optional progress metadata are updated.

## What The Agent Gets Back

Lease status, next heartbeat deadline, and whether the assignment is still owned by the caller.

## Security Boundary

Heartbeat should not include sensitive intermediate reasoning or secrets. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `claim_next_agent_assignment`
- `record_agent_assignment_result`
- `requeue_agent_experiment_assignments`
