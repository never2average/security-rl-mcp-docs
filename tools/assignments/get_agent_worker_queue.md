# `get_agent_worker_queue`

Lists assignments available to a worker role.

## Use This When

Use this when an external Codex, Claude Code, or Vercel Eve worker wants to know what it can claim.

## Inputs

- Worker role.
- Optional environment ID, experiment ID, or queue filter.

## What Changes In The RL Environment

This is a read operation.

## What The Agent Gets Back

Queue summaries, available assignment counts, role labels, and claim hints.

## Security Boundary

Queues are role-scoped. A Red worker should not see Blue-only assignments. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `claim_next_agent_assignment`
- `get_agent_assignment_readiness`
