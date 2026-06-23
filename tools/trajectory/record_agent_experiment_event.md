# `record_agent_experiment_event`

Records an event in an experiment trajectory.

## Use This When

Use this for observations, actions, tool results, evaluator notes, state patches, and important decisions that should become training data.

## Inputs

- Experiment ID.
- Episode ID or assignment ID.
- Event type.
- Timestamp or ordering key.
- Structured event payload.

## What Changes In The RL Environment

The event is appended to the experiment trajectory and can later be scored or exported.

## What The Agent Gets Back

Event ID, ordering metadata, and storage status.

## Security Boundary

Events should be sanitized according to role and dataset policy before export. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `list_agent_experiment_events`
- `export_blue_team_training_dataset`
- `evaluate_agent_experiment`
