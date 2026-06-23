# Case Study: External Worker Assignment

This case study shows how an external coding agent connects to the MCP, claims work, performs it locally or in a hosted worker, and records the result.

## Scenario

An experiment has started and the control plane has queued assignments for Red agents, Blue agents, evaluators, or diagnostics workers. Multiple agents may be running in parallel, so every worker needs a safe way to claim exactly one assignment and keep it alive while it runs.

## Actors

The worker is a local Codex, Claude Code, or Vercel Eve project. The MCP control plane owns the queue, lease, heartbeat, assignment status, and final output.

## MCP Tools Used

- `get_agent_worker_queue` to inspect available work for a role.
- `claim_next_agent_assignment` to lease one assignment.
- `get_agent_assignment_readiness` to confirm prerequisites.
- `heartbeat_agent_assignment` to keep the lease alive.
- `record_agent_assignment_result` to submit output.
- `get_agent_assignment_output` to read stored result data.

## Walkthrough

The worker authenticates through the MCP and asks for its queue. It claims the next assignment for its role, receives an assignment ID, environment ID, role, state version, and scoped instructions. The worker verifies readiness before spending tokens or running tests.

During execution, the worker sends heartbeats. If it crashes or loses network, the daemon can requeue stale assignments. When the worker finishes, it records a structured result with status, evidence, artifacts, and references to any Red issue or Blue fix it created.

## Observable Outcome

The control plane can run many agents per environment without duplicate work corrupting the experiment. Every result is attached to an assignment, and every assignment can be traced back to an experiment episode.

## Data Produced

This case produces assignment lease events, heartbeat events, result records, and optional artifact references. These records become part of the experiment trajectory.
