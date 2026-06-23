---
title: "Case Study: Red Team Agent Loop"
---

[Home](/security-rl-mcp-docs/)

# Case Study: Red Team Agent Loop

This case study shows a Red agent attacking an environment without receiving private defender state.

## Scenario

A Red-team Vercel Eve project is launched against an environment. It must behave like an external attacker inside the allowed test scope. It should not see private credentials, internal defender notes, hidden Blue fixes, or raw application state that a real attacker would not have.

## Actors

The Red worker is an LLM-based agent. The control plane creates a Red-safe brief and a Red-safe state view. Blue workers and evaluator workers consume the issues Red logs.

## MCP Tools Used

- `prepare_red_blue_eve_agents` to generate the Red brief.
- `get_red_blue_agent_brief` to retrieve role-specific instructions.
- `get_red_blue_agent_state` to retrieve the Red-safe view.
- `log_red_team_issue` to submit a finding.
- `record_red_blue_agent_run` to record the run summary.
- `record_agent_experiment_event` to capture important steps.

## Walkthrough

The Red agent retrieves its brief and role-scoped state. The state includes public endpoints, public repository hints if allowed, externally observable behavior, scope limits, and the current environment ID. It does not include defender-only application state.

The Red agent tests hypotheses, records observations, and logs a finding only when it can explain the issue, reproduction path, impact, and evidence. The issue is attached to the environment ID and state version so Blue can fix it against the correct baseline.

## Observable Outcome

The environment receives Red issues that Blue can act on. The Red agent's actions remain isolated from private Blue state, which preserves the validity of the attack simulation and the training signal.

## Reward Data Produced

Red rewards come from finding valid, reproducible, high-impact issues within scope. Invalid claims, duplicate reports, and private-state leakage reduce the score.


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
