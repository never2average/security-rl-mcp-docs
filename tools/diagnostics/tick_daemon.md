# `tick_daemon`

Manually advances daemon maintenance work such as stale assignment handling.

## Use This When

Use this in development, smoke tests, or controlled operations when the scheduled daemon needs to run immediately.

## Inputs

- Optional daemon scope and dry-run flag.

## What Changes In The RL Environment

The daemon may requeue expired assignments, update background job statuses, and record maintenance events.

## What The Agent Gets Back

Actions performed, skipped actions, errors, and next scheduled work.

## Security Boundary

This is an operational action and should require appropriate authorization. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `get_daemon_status`
- `requeue_agent_experiment_assignments`
