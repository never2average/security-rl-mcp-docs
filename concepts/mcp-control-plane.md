# MCP Control Plane

The MCP server is the control plane between a power user, local coding agents, the RL environment database, local VCS snapshots, Red/Blue assignments, and reward data. It does not need to host Codex or Claude for the default workflow; it exposes tools that local agents call.

```text
power user -> local coding agent -> RL Environment MCP -> Postgres + runtime workspaces + reward data
```
