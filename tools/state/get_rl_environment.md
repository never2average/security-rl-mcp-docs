# `get_rl_environment`

Reads an RL environment record, including current state version and validation status.

## Use This When

Use this before starting experiments, when debugging a state submission, or when an agent needs the canonical environment metadata.

## Inputs

- The environment ID.
- Optional state version or view selector if the caller needs a specific snapshot.

## What Changes In The RL Environment

This is a read operation. It does not mutate state or assignments.

## What The Agent Gets Back

Environment metadata, state version, validation summary, readiness status, and the state view allowed for the caller.

## Security Boundary

The response is scoped by the authenticated principal and role. A Red agent must not receive the same state view as a Blue agent. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `submit_full_application_state`
- `finalize_application_state`
- `get_red_blue_agent_state`
