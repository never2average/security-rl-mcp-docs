# `get_mcp_diagnostics`

Checks MCP server health, auth discovery, tool registration, and control-plane readiness.

## Use This When

Use this when a coding agent can reach the endpoint but tool calls or OAuth behavior are failing.

## Inputs

- Optional environment or organization context.

## What Changes In The RL Environment

This is a read operation.

## What The Agent Gets Back

MCP health, auth metadata status, registered tool count, database connectivity, and error summaries.

## Security Boundary

Diagnostics must not expose tokens or private OAuth material. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `get_provider_diagnostics`
- `get_daemon_status`
