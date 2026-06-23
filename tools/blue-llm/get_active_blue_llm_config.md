# `get_active_blue_llm_config`

Reads the active Blue-team model configuration.

## Use This When

Use this before a Blue training or evaluation run to confirm which model is in effect.

## Inputs

- Optional environment or scope selector.

## What Changes In The RL Environment

This is a read operation.

## What The Agent Gets Back

Active config ID, model/provider metadata, harness settings, and reward policy summary.

## Security Boundary

Secret provider values remain hidden. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `list_blue_llm_configs`
- `set_active_blue_llm_config`
