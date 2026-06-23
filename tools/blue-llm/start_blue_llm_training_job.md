# `start_blue_llm_training_job`

Starts a Blue LLM training job from an exported dataset or selected trajectories.

## Use This When

Use this when the user has enough scored data and wants to launch a training pipeline.

## Inputs

- Dataset ID or experiment filter.
- Blue LLM config ID.
- Training parameters and destination.

## What Changes In The RL Environment

A training job record is created and the backend provider or harness begins work if configured.

## What The Agent Gets Back

Training job ID, status, dataset reference, provider metadata, and polling guidance.

## Security Boundary

The job should consume sanitized data only and should not receive environment secrets. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `get_blue_llm_training_job`
- `list_blue_llm_training_jobs`
- `export_blue_team_training_dataset`
