# `evaluate_blue_team_agent`

Scores a Blue agent run or candidate fix.

## Use This When

Use this after a Blue agent has attempted a fix, patch, or independent state improvement.

## Inputs

- Environment ID.
- Run ID, assignment ID, fix ID, or episode ID.
- Optional evaluation policy.

## What Changes In The RL Environment

The evaluator records Blue-specific scores and reward components.

## What The Agent Gets Back

Blue score, issue-closure result, state-validity result, regression notes, and reward details.

## Security Boundary

Evaluation should operate on defender-authorized state and sanitized evidence. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `record_blue_team_fix`
- `export_blue_team_training_dataset`
- `evaluate_agent_experiment`
