# `get_provider_diagnostics`

Checks provider connectivity and configuration needed by the RL environment.

## Use This When

Use this when experiments cannot start, model calls fail, or training providers appear misconfigured.

## Inputs

- Optional provider name, environment ID, or experiment ID.

## What Changes In The RL Environment

This is primarily a read operation. It may record diagnostic timestamps.

## What The Agent Gets Back

Provider readiness, missing configuration, last error summaries, and safe remediation hints.

## Security Boundary

Diagnostics should report whether credentials exist, not reveal their values. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `preflight_agent_experiment`
- `get_mcp_diagnostics`
