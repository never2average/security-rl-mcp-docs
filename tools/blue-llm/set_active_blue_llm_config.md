# `set_active_blue_llm_config`

Marks a Blue-team model configuration as active.

## Use This When

Use this when switching the defender model used by Blue evaluation or training runs.

## Inputs

- Config ID.
- Optional environment or organization scope.

## What Changes In The RL Environment

The selected config becomes the active Blue LLM configuration for the target scope.

## What The Agent Gets Back

Active config metadata and previous active config if one existed.

## Security Boundary

Changing the active model should be auditable because it affects reward comparability. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `create_blue_llm_config`
- `get_active_blue_llm_config`
