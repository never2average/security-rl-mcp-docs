# `finalize_application_state`

Finalizes a multipart state submission and promotes it into a usable RL environment.

## Use This When

Use this after all required sections have been submitted through `submit_application_state_section`.

## Inputs

- The draft environment ID.
- Optional finalize metadata, such as source commit, deployment label, or submitter note.

## What Changes In The RL Environment

The control plane performs whole-document validation, creates a state version, builds role-scoped views, and marks the environment ready or blocked.

## What The Agent Gets Back

The environment ID, ready status, state version, validation report, and any remaining blockers.

## Security Boundary

Finalize does not grant Red or Blue agents extra access. It only turns submitted state into the canonical environment record. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `submit_application_state_section`
- `get_rl_environment`
- `create_agent_experiment`
