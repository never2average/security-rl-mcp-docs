# `record_agent_assignment_result`

Records the final result for a claimed assignment.

## Use This When

Use this when the worker has completed, failed, or intentionally skipped its assigned work.

## Inputs

- Assignment ID.
- Status.
- Structured result payload.
- Evidence, artifact references, and linked issue/fix IDs when applicable.

## What Changes In The RL Environment

The assignment is marked complete or failed and the result becomes part of the experiment trajectory.

## What The Agent Gets Back

Stored result ID, assignment status, linked events, and downstream evaluation readiness.

## Security Boundary

Submit evidence and references, not raw secrets or unapproved private data. Authentication is expected to come from Google/Dex OAuth discovery for human-connected agents. Service bearer tokens are only a fallback for controlled workers.

## Related Tools

- `get_agent_assignment_output`
- `record_agent_experiment_event`
- `evaluate_agent_experiment`
