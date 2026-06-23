# `requeue_agent_experiment_assignments`

Requeues stale, failed, or abandoned assignments for an experiment.

## Use This When

Use this when workers crash, leases expire, or an operator wants to retry incomplete work.

## Inputs

- Experiment ID.
- Optional assignment status filters and retry limits.

## What Changes In The RL Environment

Matching assignments are moved back to a claimable queue or marked retryable.

## What The Agent Gets Back

Counts of requeued assignments, skipped assignments, and any blocked reasons.

## Security Boundary

Requeue should preserve audit history rather than overwriting previous failed attempts. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `get_agent_worker_queue`
- `claim_next_agent_assignment`
- `heartbeat_agent_assignment`
