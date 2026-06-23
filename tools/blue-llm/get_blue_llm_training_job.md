# `get_blue_llm_training_job`

Reads status and metadata for one Blue LLM training job.

## Use This When

Use this to monitor progress, inspect failures, or collect output model references.

## Inputs

- Training job ID.

## What Changes In The RL Environment

This is a read operation.

## What The Agent Gets Back

Job status, progress, dataset reference, logs or error summary, and output model metadata when complete.

## Security Boundary

Provider secrets and raw training records should not be exposed in status output. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `start_blue_llm_training_job`
- `list_blue_llm_training_jobs`
