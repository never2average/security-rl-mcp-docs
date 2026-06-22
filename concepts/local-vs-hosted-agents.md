# Local vs Hosted Agents

Default mode is local: the user runs Codex or Claude Code and those clients call the MCP server. Hosted-worker mode is optional for unattended VM-side worker pools.

```text
power user -> local coding agent -> RL Environment MCP -> Postgres + runtime workspaces + reward data
```
