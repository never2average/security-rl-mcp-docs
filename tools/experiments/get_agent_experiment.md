# `get_agent_experiment`

Reads the full metadata and status for one experiment.

## Use This When

Use this when an agent or operator needs the current experiment plan, state, and progress.

## Inputs

- Experiment ID.

## What Changes In The RL Environment

This is a read operation.

## What The Agent Gets Back

Experiment definition, target environment, status, episodes, assignments summary, and evaluation status.

## Security Boundary

The response should not leak role-private assignment content to callers that only need experiment metadata. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `list_agent_experiments`
- `get_agent_experiment_episode`
- `start_agent_experiment`
