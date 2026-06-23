# RL Environment MCP

The RL Environment MCP is the agent-facing control plane for turning an application's submitted `state.json` into a running reinforcement-learning environment. A power user works through a local coding agent such as Codex or Claude Code. The coding agent connects to the MCP, submits application state, launches Red and Blue agent assignments, records trajectories, and exports reward data.

Public endpoint:

```text
https://security-rl.useimmaculate.com/mcp
```

Auth intent:

```text
User-facing auth: Google login through Dex/OIDC.
Wire-level auth: OAuth bearer access token issued by Dex.
Service fallback: scoped worker token for daemon pools and smoke tests only.
```

Use these docs by job:

- Start with **Concepts** to understand environments, state, experiments, Red/Blue boundaries, rewards, and the digital-twin direction.
- Use **Setup** to connect Codex or Claude Code through OAuth-backed MCP discovery.
- Use **Workflows** as case studies you can run with the MCP.
- Use **Tools** when you need the exact MCP call that advances one part of the RL loop.
- Use **Schemas** to understand the data contracts the agents create and consume.
- Use **Operations** for public smoke tests, readiness checks, hosted workers, and auth errors.
