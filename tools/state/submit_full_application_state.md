# `submit_full_application_state`

Submits a complete `state.json` document and creates or replaces an RL environment in one call.

## Use This When

Use this when the coding agent has enough application context to assemble the full schema before calling the MCP.

## Inputs

- A complete `state` object matching the current `state.json` schema.
- An optional environment name or source label.
- Optional metadata describing who submitted it and which repo or deployment it came from.

## What Changes In The RL Environment

The control plane validates the full document, stores a versioned environment record, initializes state-derived views, and makes the environment available to experiments and Red/Blue tools.

## What The Agent Gets Back

An environment ID, current state version, validation status, normalized sections, and any schema diagnostics that the agent must fix before experiments can start.

## Security Boundary

The submitted state should describe secrets by reference or metadata. Raw credentials, tokens, private keys, and user secrets should not be embedded in the JSON. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `submit_application_state_section`
- `finalize_application_state`
- `get_rl_environment`
