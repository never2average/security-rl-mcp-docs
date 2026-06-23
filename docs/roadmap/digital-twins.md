---
title: "Digital Twins Roadmap"
---

[Home](/security-rl-mcp-docs/)

# Digital Twins Roadmap

The roadmap is to turn `state.json` from a submission format into a living digital twin of the application. The MCP already stores validated state, versions, issues, fixes, assignments, and trajectories. The next product step is to derive increasingly faithful twin layers from that value.

## Phase 1: Descriptive Twin

The descriptive twin is the application map. It links repositories, services, endpoints, cloud resources, identities, roles, data assets, telemetry, and SDLC changes. The output is a queryable model that a coding agent can navigate without scraping the company from scratch.

What this enables:

- Red agents can reason from public-facing services to likely abuse cases.
- Blue agents can identify owners, affected services, controls, and tests.
- Setup agents can detect missing or stale sections in the submitted state.

## Phase 2: Security Twin

The security twin adds attacker and defender projections. It keeps Red-visible state separate from Blue-visible operator state. It models exposed paths, identity edges, data sensitivity, detection coverage, and enforcement actions.

What this enables:

- Red teams operate from public knowledge only.
- Blue teams receive safe operator context without raw secrets.
- The harness can reward fixes that reduce reachable risk instead of only closing tickets.

## Phase 3: Executable Twin

The executable twin turns state into repeatable experiments. Agent assignments, Eve projects, local VCS snapshots, worker queues, and telemetry events become a controlled simulation surface. Blue fixes can be replayed against a versioned environment, and Red findings can be compared across models.

What this enables:

- Multiple concurrent environments for the same application.
- Multiple Red and Blue agents per environment.
- Comparable reward trajectories for model training.
- Regression checks when a new state version changes risk.

## Phase 4: Training Twin

The training twin packages episodes into supervised and reinforcement-learning data. It exports observations, allowed state, agent actions, findings, fixes, reward deltas, and final evaluation scores.

What this enables:

- Blue LLM candidates train against harness-in-the-loop feedback.
- The system can compare prompt changes, model changes, and policy changes.
- Fix quality is tied to state versions and Red findings, not vague human preference.

## Phase 5: Continuously Updating Twin

The final direction is a continuously refreshed twin. Repository events, cloud inventory, identity changes, telemetry, incidents, and agent actions update the state. The MCP becomes the agent-safe control plane over that evolving twin.

The critical rule stays the same: the twin must preserve boundaries. Red gets public attack perspective. Blue gets sanitized operator context. Workers get scoped service credentials. Humans authenticate through Google/Dex. Raw shared secrets never become the user interface.


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
