# Red/Blue Boundaries

Red and Blue agents do not get the same state projection. Red receives public attacker-visible state. Blue receives operator/fix context and the active fix queue.

```text
power user -> local coding agent -> RL Environment MCP -> Postgres + runtime workspaces + reward data
```
