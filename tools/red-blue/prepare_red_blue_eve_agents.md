# `prepare_red_blue_eve_agents`

Prepares role-specific Red and Blue agent briefs for Vercel Eve workers.

## Use This When

Use this before launching parallel Red/Blue workers for an environment.

## Inputs

- Environment ID.
- Experiment ID or run label.
- Counts for Red and Blue workers.
- Optional model and Vercel Eve project configuration.

## What Changes In The RL Environment

The control plane creates role briefs, queue metadata, and scoped state views for Red and Blue workers.

## What The Agent Gets Back

Prepared worker descriptors, brief IDs, role labels, and launch guidance.

## Security Boundary

Red and Blue views are separated here. Red gets public attack context; Blue gets defender context and issue queues. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `get_red_blue_agent_brief`
- `get_red_blue_agent_state`
- `start_agent_experiment`
