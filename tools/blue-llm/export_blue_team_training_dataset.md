# `export_blue_team_training_dataset`

Exports Blue-team trajectories into a training dataset.

## Use This When

Use this after enough evaluated Blue runs exist for training, preference modeling, or offline analysis.

## Inputs

- Experiment ID or environment ID.
- Optional filters for model, score range, date, issue type, or state version.
- Output format options.

## What Changes In The RL Environment

A dataset artifact is created or refreshed.

## What The Agent Gets Back

Dataset ID, record count, export location, schema version, and sanitization summary.

## Security Boundary

Export must remove raw secrets and respect Red/Blue visibility boundaries. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `list_agent_experiment_events`
- `evaluate_blue_team_agent`
- `start_blue_llm_training_job`
