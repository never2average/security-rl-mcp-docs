# `create_agent_experiment`

Creates an experiment definition for an environment, such as Red/Blue testing, Blue-only training, or evaluator runs.

## Use This When

Use this after an environment is ready and the user wants reproducible agent work tied to that environment.

## Inputs

- Environment ID.
- Experiment type.
- Agent roles and counts.
- Episode count or scheduling policy.
- Optional model/provider configuration and reward policy.

## What Changes In The RL Environment

The control plane records the experiment plan but does not necessarily enqueue work until it is preflighted and started.

## What The Agent Gets Back

Experiment ID, configured roles, target environment, initial status, and preflight hints.

## Security Boundary

Experiment creation defines roles, but role-specific state access is still enforced by assignment and Red/Blue state tools. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `preflight_agent_experiment`
- `start_agent_experiment`
- `evaluate_agent_experiment`
