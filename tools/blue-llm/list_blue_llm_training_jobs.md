# `list_blue_llm_training_jobs`

Lists Blue LLM training jobs.

## Use This When

Use this for operations dashboards, model lineage, or selecting a job to inspect.

## Inputs

- Optional status, config, dataset, environment, or date filters.

## What Changes In The RL Environment

This is a read operation.

## What The Agent Gets Back

Job summaries with IDs, statuses, dataset references, config IDs, and timestamps.

## Security Boundary

Only jobs visible to the authenticated organization or user should be returned. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `get_blue_llm_training_job`
- `start_blue_llm_training_job`
