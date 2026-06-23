---
title: "Case Study: Export Training Data"
---

[Home](/security-rl-mcp-docs/)

# Case Study: Export Training Data

This case study turns experiment trajectories into datasets for model improvement, evaluator analysis, or offline review.

## Scenario

After several Red/Blue or Blue-only experiments, the user wants a dataset that captures observations, actions, outcomes, rewards, and state versions. The export must preserve enough context for training while excluding secrets and role-forbidden state.

## Actors

The experiment control plane stores events and outcomes. The exporter creates a dataset. The training harness or downstream pipeline consumes the exported records.

## MCP Tools Used

- `list_agent_experiment_events` to inspect trajectory events.
- `get_agent_experiment_episode` to retrieve episode-level context.
- `evaluate_agent_experiment` to ensure final scores exist.
- `evaluate_blue_team_agent` for Blue-specific scoring.
- `export_blue_team_training_dataset` to create a Blue training dataset.

## Walkthrough

The user selects an experiment or environment. The agent lists trajectory events and verifies that episodes have evaluation records. If scores are missing, it triggers evaluation before export.

The exporter collects state observations, role-specific briefs, actions, tool calls, Red issues, Blue fixes, evaluator decisions, and reward values. It normalizes them into records that can be used for supervised fine-tuning, preference data, or reinforcement learning with a harness in the loop.

## Observable Outcome

The user receives a dataset artifact with traceable environment IDs, state versions, episode IDs, rewards, and sanitized observations. The dataset can be filtered by role, model, environment, severity, or outcome.

## Data Produced

The export produces JSONL-style training records, evaluator summaries, and metadata that says which state schema version and reward policy generated the data.


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
