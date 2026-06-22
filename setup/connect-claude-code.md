# Connect Claude Code

Claude Code needs the MCP URL and an authorization header. The token should come from Google/Dex login once the connect page exists.

```bash
export AGENT_BEARER_TOKEN="<Dex access token or temporary service token>"

claude mcp add --transport http rl_environment   https://security-rl.useimmaculate.com/mcp   --header "Authorization: Bearer $AGENT_BEARER_TOKEN"
```

Smoke inside Claude Code:

```text
Use the rl_environment MCP server and call get_provider_diagnostics.
```
