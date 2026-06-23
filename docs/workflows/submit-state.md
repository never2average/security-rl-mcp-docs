---
title: "Case Study: Submit Application State"
---

[Home](/security-rl-mcp-docs/)

# Case Study: Submit Application State

A power user is working locally in Codex or Claude Code and wants to turn an existing application into an RL environment. The coding agent inspects the repo, infrastructure notes, public endpoints, identity configuration, and deployment model, then submits the application state through the MCP.

## Scenario

The user has a Vercel Eve application and wants the security control plane to create an environment from the app's current state. The first goal is not to run Red or Blue agents yet. The goal is to produce a validated environment record that later agents can use without re-discovering the application from scratch.

## Actors

The power user owns the application and authenticates with Google through Dex. The local coding agent gathers facts and calls the MCP. The RL control plane validates and versions the submitted state.

## MCP Tools Used

- `submit_full_application_state` when the agent can construct the whole `state.json` in one call.
- `submit_application_state_section` when the agent has to submit discovery results in sections.
- `finalize_application_state` when all required sections have been submitted.
- `get_rl_environment` to confirm the environment ID, state version, and validation result.

## Walkthrough

The agent first maps the app into the `state.json` schema: repository, runtime, public endpoints, users, credentials metadata, identity provider, data assets, detection rules, work items, and recent changes. Secrets are represented as references or descriptors, not raw values.

If the state is small, the agent calls `submit_full_application_state` once. If discovery is incremental, it submits sections such as `repository`, `network_endpoints`, `application_cloud`, and `identity_provider` with `submit_application_state_section`, then calls `finalize_application_state`.

The environment is created only after schema validation passes. The response includes the environment ID and the state version that future Red, Blue, experiment, assignment, and trajectory tools must reference.

## Observable Outcome

The user gets a durable RL environment that represents the application's current security-relevant state. The state can be read back with `get_rl_environment`, and future agents do not need broad repo or cloud access to start from the same baseline.

## Data Produced

This case produces an environment record, a normalized `state.json`, validation diagnostics, and an initial state version. That version becomes the seed for Red/Blue tests and for the application's future digital twin.


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
