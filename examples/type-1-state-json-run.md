# Type 1 state.json Run

This example is the standard Red/Blue environment run.

1. Submit application state with `submit_full_application_state`, or submit sections and call `finalize_application_state`.
2. Read the environment with `get_rl_environment` and confirm that it is ready.
3. Prepare Red and Blue Eve workers with `prepare_red_blue_eve_agents`.
4. Create and start an experiment with `create_agent_experiment`, `preflight_agent_experiment`, and `start_agent_experiment`.
5. Red workers claim assignments, read Red-safe state, and call `log_red_team_issue` for valid findings.
6. Blue workers claim assignments, read defender-safe state, call `get_blue_team_fix_queue`, and record fixes with `record_blue_team_fix`.
7. Evaluate the run with `evaluate_agent_experiment` and export trajectory data when needed.

The important boundary is that Red and Blue use the same environment ID but not the same state view. Red gets public attack-facing state. Blue gets defender context and the issue queue.
