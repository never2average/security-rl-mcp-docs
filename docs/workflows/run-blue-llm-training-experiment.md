---
title: "Case Study: Blue LLM Training"
---

[Home](/security-rl-mcp-docs/)

# Case Study: Blue LLM Training Experiment

This case study trains or evaluates a Blue-team model in a harness where it must keep improving the application's state without waiting for live Red issues.

## Scenario

In production Red/Blue mode, Blue waits for Red issues. In Blue LLM training mode, Blue cannot wait. The harness generates tasks from the environment state, historical Red findings, static weaknesses, known misconfigurations, and synthetic perturbations of `state.json`. The Blue agent patches state and produces reward data.

## Actors

The Blue LLM is the candidate defender. The harness controls prompts, tasks, expected boundaries, scoring, and dataset export. The MCP records every meaningful action as trajectory data.

## MCP Tools Used

- `create_blue_llm_config` to define the model, provider, harness settings, and scoring policy.
- `set_active_blue_llm_config` to choose the active defender configuration.
- `create_agent_experiment` to create a Blue-only or Blue-heavy training experiment.
- `get_red_blue_agent_state` to provide a defender-safe state view.
- `record_agent_experiment_event` to capture observations, actions, patches, and judge events.
- `evaluate_blue_team_agent` to score the Blue run.
- `export_blue_team_training_dataset` to create training data.
- `start_blue_llm_training_job` to launch a downstream training job when enough data exists.

## Walkthrough

The user creates a Blue LLM config that points at the candidate model. The experiment references an environment ID and a state version. The harness then creates defender tasks: close an exposed endpoint, tighten an identity rule, improve detection coverage, remove an unsafe credential reference, or repair a risky deployment setting.

For each task, the Blue agent receives a sanitized defender state and a goal. It proposes a patch to the environment state or records a fix artifact. The harness evaluates the patch against schema validity, security improvement, blast radius, and consistency with user intent.

Every observation and action is stored as a trajectory event. Successful and failed attempts both matter because the training dataset needs contrastive examples, not only winning outputs.

## Observable Outcome

The user gets comparable Blue-agent episodes across the same application twin. The output is a scored dataset of state observations, candidate fixes, evaluator notes, and rewards.

## Reward Data Produced

Rewards are based on valid schema edits, real security improvement, low regression risk, issue closure, minimal overreach, and whether the candidate improved state without requiring live Red input.


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
