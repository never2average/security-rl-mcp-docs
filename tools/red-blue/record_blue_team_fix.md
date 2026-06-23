# `record_blue_team_fix`

Records a Blue-team fix or attempted fix for a Red issue or training task.

## Use This When

Use this after the Blue agent has produced a patch, state change, mitigation, or documented fix decision.

## Inputs

- Environment ID.
- Issue ID or training task ID.
- Fix summary.
- Affected state version.
- Patch or state-diff reference.
- Evidence and regression checks.

## What Changes In The RL Environment

The fix is linked to the issue, a new state version may be recorded, and evaluator inputs become available.

## What The Agent Gets Back

Fix ID, linked issue status, state version outcome, and evaluation readiness.

## Security Boundary

Fix records should contain enough evidence for evaluation without exposing raw secrets. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `get_blue_team_fix_queue`
- `evaluate_blue_team_agent`
- `evaluate_agent_experiment`
