---
title: "Case Study: Red/Blue State Experiment"
---

[Home](/security-rl-mcp-docs/)

# Case Study: Red/Blue State Experiment

This case study runs a Red/Blue experiment against a submitted `state.json`. Red agents receive only the public attack-facing view. Blue agents receive the defender view and the issue queue produced by Red.

## Scenario

A user wants to know whether the application's current deployment and code state exposes practical attack paths. The RL environment creates parallel assignments for Red and Blue agents so multiple agents can test the same environment without sharing private state incorrectly.

## Actors

Red agents are Vercel Eve projects that attack from public information, endpoint behavior, and allowed reconnaissance. Blue agents are Vercel Eve projects that read defender state, inspect logged issues, and produce fixes. The control plane owns assignment routing, environment state versions, and reward events.

## MCP Tools Used

- `submit_full_application_state` or `finalize_application_state` to create the environment.
- `prepare_red_blue_eve_agents` to create Red/Blue worker briefs.
- `create_agent_experiment` to define the experiment episode count, teams, and target environment.
- `preflight_agent_experiment` to verify that state, auth, queues, and providers are ready.
- `start_agent_experiment` to enqueue assignments.
- `claim_next_agent_assignment` and `record_agent_assignment_result` for worker execution.
- `log_red_team_issue`, `get_blue_team_fix_queue`, and `record_blue_team_fix` for the Red/Blue loop.
- `evaluate_agent_experiment` to score outcomes.

## Walkthrough

The user submits a valid environment. The control plane prepares Red and Blue agent briefs from the same environment ID, but the state views are intentionally different. Red receives a public view: public routes, exposed assets, technology hints, and allowed test scope. Blue receives the defender view: code and configuration context, relevant sanitized state, prior detections, and Red issues after they are logged.

When the experiment starts, workers claim assignments from their queue. A Red worker tests an attack path and calls `log_red_team_issue` with evidence, affected assets, severity, reproducibility, and state version. A Blue worker calls `get_blue_team_fix_queue`, selects an unresolved issue, proposes or records a patch, and calls `record_blue_team_fix`.

The experiment evaluator compares issue quality, fix latency, fix correctness, regression risk, and whether the Blue fix landed within the required state-version window.

## Observable Outcome

The experiment produces a list of Red findings, Blue fixes, assignment results, and reward signals tied to one environment. Concurrent Red and Blue agents can run against the same environment ID because assignment ownership and state versioning prevent accidental overwrite.

## Reward Data Produced

The reward signal includes Red discovery value, Blue time-to-fix, whether the fix addresses the issue within one version of the Red flag, and whether the fix degrades other parts of the state. These events become trajectory data for later training.


---

## Documentation Sections

- [RL Environment MCP](/index)
- [Endpoint and Auth](/setup/endpoint-and-auth)
- [Connect Codex](/setup/connect-codex)
- [Connect Claude Code](/setup/connect-claude-code)
- [MCP Control Plane](/concepts/mcp-control-plane)
- [Environments](/concepts/environments)
- [state.json](/concepts/state-json)
- [Red/Blue Boundaries](/concepts/red-blue-boundaries)
- [Reward and Trajectory](/concepts/reward-and-trajectory)
- [Local vs Hosted Agents](/concepts/local-vs-hosted-agents)
- [Case Study: Submit Application State](/workflows/submit-state)
- [Case Study: Red/Blue State Experiment](/workflows/run-state-json-experiment)
- [Case Study: Blue LLM Training](/workflows/run-blue-llm-training-experiment)
- [Case Study: Red Team Agent Loop](/workflows/red-team-agent-loop)
- [Case Study: Blue Team Agent Loop](/workflows/blue-team-agent-loop)
- [Case Study: Export Training Data](/workflows/export-training-data)
- [MCP Tool Reference](/tools/tool-reference)
- [Digital Twins Roadmap](/roadmap/digital-twins)
- [Readiness Checks](/operations/readiness-checks)
- [Troubleshooting](/operations/troubleshooting)
