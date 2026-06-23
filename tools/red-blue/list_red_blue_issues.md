# `list_red_blue_issues`

Lists Red/Blue issues for an environment or experiment.

## Use This When

Use this for dashboards, Blue triage, evaluation, or audit review.

## Inputs

- Environment ID or experiment ID.
- Optional status, severity, role, or state-version filters.

## What Changes In The RL Environment

This is a read operation.

## What The Agent Gets Back

Issue summaries, status, severity, affected state version, linked fixes, and timestamps.

## Security Boundary

Issue details may be filtered by caller role and experiment policy. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `log_red_team_issue`
- `get_blue_team_fix_queue`
- `record_blue_team_fix`
