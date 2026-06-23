# `get_agent_assignment_readiness`

Checks whether a claimed or queued assignment has all required prerequisites.

## Use This When

Use this before a worker spends time on an assignment that may be blocked by missing state, provider config, or auth.

## Inputs

- Assignment ID or queue context.

## What Changes In The RL Environment

This is primarily a read operation. It may record readiness diagnostics.

## What The Agent Gets Back

Ready or blocked status, missing dependencies, provider status, state version availability, and suggested next step.

## Security Boundary

Readiness messages should describe blockers without revealing hidden secrets. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `get_provider_diagnostics`
- `get_mcp_diagnostics`
- `claim_next_agent_assignment`
