# `list_agent_experiments`

Lists experiments visible to the authenticated user or organization.

## Use This When

Use this to find recent runs, monitor active work, or select an experiment for evaluation or export.

## Inputs

- Optional filters such as environment ID, status, experiment type, or time range.

## What Changes In The RL Environment

This is a read operation and does not mutate experiments.

## What The Agent Gets Back

Experiment summaries with IDs, statuses, environment IDs, role counts, and timestamps.

## Security Boundary

Only experiments authorized for the caller should be returned. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `get_agent_experiment`
- `evaluate_agent_experiment`
- `list_agent_experiment_events`
