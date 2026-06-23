# `submit_application_state_section`

Submits one named section of application state for an environment that is being assembled incrementally.

## Use This When

Use this when the agent discovers the application in stages or when state is too large to submit comfortably in one call.

## Inputs

- The target environment draft or name.
- The section name, such as `repository`, `network_endpoints`, `identity_provider`, or `data_assets`.
- The section payload matching that part of the schema.

## What Changes In The RL Environment

The draft environment stores the section, validates it against the expected schema fragment, and tracks which required sections are still missing.

## What The Agent Gets Back

The draft environment ID, section validation result, accepted fields, missing sections, and any errors that need correction.

## Security Boundary

The same secret-handling rule applies as full submission: include references and descriptors, not raw secret values. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `finalize_application_state`
- `submit_full_application_state`
- `get_rl_environment`
