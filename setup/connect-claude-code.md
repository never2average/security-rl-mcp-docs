# Connect Claude Code

Claude Code should connect to the HTTP MCP endpoint and authenticate through the MCP OAuth discovery flow.

```bash
claude mcp add --transport http rl_environment https://security-rl.useimmaculate.com/mcp
```

Smoke inside Claude Code:

```text
Use the rl_environment MCP server and call get_provider_diagnostics.
```

A manual `Authorization` header is only a service-account compatibility path for workers or smoke tests.
