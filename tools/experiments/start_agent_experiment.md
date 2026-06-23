# `start_agent_experiment`

Starts an experiment and enqueues role-specific assignments.

## Use This When

Use this after preflight passes and the user is ready for agents to run.

## Inputs

- Experiment ID.
- Optional start options such as concurrency limits or target episode count.

## What Changes In The RL Environment

Assignments are created, queues become visible to workers, and the experiment moves into a running state.

## What The Agent Gets Back

Experiment status, created assignment counts, queue names, and start timestamp.

## Security Boundary

Assignments must be generated with role-scoped state access so concurrent Red and Blue workers do not share the same state I/O. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `claim_next_agent_assignment`
- `get_agent_worker_queue`
- `requeue_agent_experiment_assignments`
