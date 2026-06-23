# `get_agent_experiment_episode`

Reads the state and results for one experiment episode.

## Use This When

Use this when evaluating a specific run, exporting training data, or diagnosing a failed agent episode.

## Inputs

- Experiment ID.
- Episode ID or episode index.

## What Changes In The RL Environment

This is a read operation.

## What The Agent Gets Back

Episode metadata, assignments, events, Red issues, Blue fixes, scores, and linked state versions allowed for the caller.

## Security Boundary

Role-private content must still be filtered according to caller permissions. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `list_agent_experiment_events`
- `evaluate_agent_experiment`
- `export_blue_team_training_dataset`
