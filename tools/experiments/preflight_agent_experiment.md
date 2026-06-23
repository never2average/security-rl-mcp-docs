# `preflight_agent_experiment`

Checks whether an experiment can safely start.

## Use This When

Use this after creating an experiment and before queueing assignments.

## Inputs

- Experiment ID.

## What Changes In The RL Environment

The control plane may record preflight status and diagnostics, but it should not start agent work.

## What The Agent Gets Back

Readiness result, missing prerequisites, provider diagnostics, environment validation status, and queue readiness.

## Security Boundary

Preflight should surface operational blockers without exposing secrets or role-private state. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `create_agent_experiment`
- `start_agent_experiment`
- `get_provider_diagnostics`
