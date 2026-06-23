# `evaluate_agent_experiment`

Evaluates experiment outcomes and writes reward or score records.

## Use This When

Use this after assignments have produced enough output to score the experiment.

## Inputs

- Experiment ID.
- Optional evaluator configuration or scoring policy.

## What Changes In The RL Environment

The evaluator records scores, reward signals, pass/fail summaries, and issue/fix quality judgments.

## What The Agent Gets Back

Evaluation summary, per-role scores, reward metrics, failed checks, and dataset readiness.

## Security Boundary

Evaluation should use sanitized evidence and should not turn private Blue state into Red-visible training context. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `get_agent_experiment_episode`
- `evaluate_blue_team_agent`
- `export_blue_team_training_dataset`
