# Case Study: Blue Team Agent Loop

This case study shows a Blue agent fixing Red issues and improving the state of the environment.

## Scenario

A Red agent has logged an issue against environment version `N`. The Blue agent must inspect defender-safe state, identify the fix, and record a patch or fix decision by version `N + 1` when the production Red/Blue policy requires it.

## Actors

The Blue worker is an LLM-based coding agent with defender permissions. The control plane provides sanitized application state, issue queues, and state-version constraints. The evaluator checks whether the fix closes the Red issue without creating new risk.

## MCP Tools Used

- `get_red_blue_agent_brief` to retrieve Blue instructions.
- `get_red_blue_agent_state` to retrieve defender-safe application state.
- `get_blue_team_fix_queue` to retrieve unresolved Red issues.
- `record_blue_team_fix` to submit the fix and evidence.
- `record_agent_experiment_event` to capture the reasoning and patch action.
- `evaluate_blue_team_agent` or `evaluate_agent_experiment` to score the result.

## Walkthrough

The Blue agent asks for the fix queue and chooses an issue. It retrieves the defender view of state for the affected environment and state version. That state can include sanitized code topology, cloud configuration, identity posture, data assets, recent changes, and detection context.

The Blue agent creates a minimal fix plan, applies or describes the state patch, and records the fix. The fix record references the Red issue, affected assets, state version, validation evidence, and any regression checks.

In training mode, the Blue agent may work without waiting for a Red issue. In that mode, tasks come from the harness and the reward is based on independently improving the state.

## Observable Outcome

The Red issue moves into a fixed or attempted-fix state. The environment gains a new state version, and the evaluator can compare issue quality, fix quality, and fix timeliness.

## Reward Data Produced

Blue rewards come from closing valid Red issues quickly, preserving application behavior, reducing future attack surface, and producing valid state changes. Overbroad fixes and unverified claims reduce the score.
