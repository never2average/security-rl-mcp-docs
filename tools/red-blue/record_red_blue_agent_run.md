# `record_red_blue_agent_run`

Records a summary of one Red or Blue worker run.

## Use This When

Use this when a worker finishes a role loop and needs to submit run-level metadata separate from individual issues or fixes.

## Inputs

- Environment ID.
- Experiment ID.
- Role.
- Assignment ID.
- Run summary, status, metrics, and artifact references.

## What Changes In The RL Environment

A run record is attached to the experiment and can be used for evaluation and audit.

## What The Agent Gets Back

Run ID, stored status, linked events, and evaluation readiness.

## Security Boundary

Run summaries should respect role visibility and should not mix Red-only and Blue-only internal state. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `log_red_team_issue`
- `record_blue_team_fix`
- `record_agent_experiment_event`
