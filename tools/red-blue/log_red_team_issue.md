# `log_red_team_issue`

Records a Red-team finding against an environment and state version.

## Use This When

Use this when a Red worker has a reproducible issue with evidence and impact.

## Inputs

- Environment ID.
- State version.
- Issue title, severity, affected assets, reproduction steps, evidence, and confidence.
- Optional assignment ID and run ID.

## What Changes In The RL Environment

A Red issue is created and becomes available to Blue according to the experiment policy.

## What The Agent Gets Back

Issue ID, status, linked environment, and fix-queue visibility.

## Security Boundary

The issue should be based on permitted Red observations, not private Blue state or leaked internal secrets. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `list_red_blue_issues`
- `get_blue_team_fix_queue`
- `record_red_blue_agent_run`
