# `create_blue_llm_config`

Creates a configuration for Blue-team model evaluation or training.

## Use This When

Use this when defining which model, provider, prompt policy, reward policy, and harness settings Blue training should use.

## Inputs

- Config name.
- Provider and model settings.
- Harness mode.
- Reward policy.
- Optional system prompt or tool policy references.

## What Changes In The RL Environment

A Blue LLM config is stored and can be activated for future training or evaluation runs.

## What The Agent Gets Back

Config ID, status, active flag, and validation diagnostics.

## Security Boundary

Provider credentials should be referenced through secure config, not embedded in the MCP payload. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `set_active_blue_llm_config`
- `evaluate_blue_team_agent`
- `start_blue_llm_training_job`
