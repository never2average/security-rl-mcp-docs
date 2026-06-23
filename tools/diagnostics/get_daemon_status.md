# `get_daemon_status`

Reads the RL daemon status for assignment requeueing, scheduled work, and background maintenance.

## Use This When

Use this when assignments are stuck, episodes are not advancing, or background jobs are delayed.

## Inputs

- Optional daemon name or environment scope.

## What Changes In The RL Environment

This is a read operation.

## What The Agent Gets Back

Daemon heartbeat, last tick, queue counts, requeue status, and recent errors.

## Security Boundary

Status output should stay operational and avoid leaking worker secrets. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `tick_daemon`
- `requeue_agent_experiment_assignments`
