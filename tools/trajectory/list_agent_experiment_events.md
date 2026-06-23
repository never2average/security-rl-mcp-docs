# `list_agent_experiment_events`

Lists trajectory events for an experiment, episode, or assignment.

## Use This When

Use this to debug runs, review agent behavior, or prepare training dataset exports.

## Inputs

- Experiment ID.
- Optional episode ID, assignment ID, event type, or time range.

## What Changes In The RL Environment

This is a read operation.

## What The Agent Gets Back

Ordered events with role, event type, payload summaries, timestamps, and linked state versions.

## Security Boundary

Event payloads should be filtered for the caller and export purpose. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `record_agent_experiment_event`
- `get_agent_experiment_episode`
- `export_blue_team_training_dataset`
