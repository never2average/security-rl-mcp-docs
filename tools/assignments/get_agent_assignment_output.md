# `get_agent_assignment_output`

Reads the stored output for an assignment.

## Use This When

Use this when evaluating results, debugging a run, or exporting trajectory data.

## Inputs

- Assignment ID.

## What Changes In The RL Environment

This is a read operation.

## What The Agent Gets Back

Assignment result, status, evidence references, linked events, and timestamps.

## Security Boundary

Output visibility should follow the experiment role and organization permissions. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `record_agent_assignment_result`
- `get_agent_experiment_episode`
