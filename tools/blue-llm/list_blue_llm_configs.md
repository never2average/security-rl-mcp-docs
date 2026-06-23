# `list_blue_llm_configs`

Lists available Blue-team model configurations.

## Use This When

Use this before choosing an active Blue model or comparing past configs.

## Inputs

- Optional environment, provider, active status, or owner filters.

## What Changes In The RL Environment

This is a read operation.

## What The Agent Gets Back

Config summaries, active status, model labels, and timestamps.

## Security Boundary

Responses should not include raw provider credentials. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `get_active_blue_llm_config`
- `set_active_blue_llm_config`
