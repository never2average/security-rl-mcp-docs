# `get_blue_team_fix_queue`

Retrieves unresolved or retryable issues assigned to Blue workers.

## Use This When

Use this when a Blue agent is ready to fix Red findings or defender-harness tasks.

## Inputs

- Environment ID or experiment ID.
- Optional Blue worker ID, severity filter, or state-version window.

## What Changes In The RL Environment

This is usually a read operation. The control plane may record queue observation metadata.

## What The Agent Gets Back

Fixable issues, priority, target state version, evidence summaries, and expected output format.

## Security Boundary

Only Blue-authorized workers should receive this queue. Red workers should not see defender queues. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `record_blue_team_fix`
- `get_red_blue_agent_state`
- `list_red_blue_issues`
