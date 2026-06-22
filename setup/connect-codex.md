# Connect Codex

Codex can connect to the HTTP MCP endpoint. Until Codex is wired to your Google/Dex connect page, use an environment variable that contains a Dex-issued access token or temporary service token.

```bash
export AGENT_BEARER_TOKEN="<Dex access token or temporary service token>"
```

Add to `~/.codex/config.toml`:

```toml
[mcp_servers.rl_environment]
url = "https://security-rl.useimmaculate.com/mcp"
bearer_token_env_var = "AGENT_BEARER_TOKEN"
```

Smoke:

```bash
codex exec 'Use the rl_environment MCP server and call get_provider_diagnostics.'
```

Target product flow:

```text
codex mcp login rl_environment -> browser Google login -> Dex token stored for Codex MCP calls
```
