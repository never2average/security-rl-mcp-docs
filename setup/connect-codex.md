# Connect Codex

Codex should connect to the HTTP MCP endpoint and let the MCP OAuth discovery flow send the user through Google/Dex login.

Add to `~/.codex/config.toml`:

```toml
[mcp_servers.rl_environment]
url = "https://security-rl.useimmaculate.com/mcp"
```

Smoke:

```bash
codex exec 'Use the rl_environment MCP server and call get_provider_diagnostics.'
```

Target product flow:

```text
codex mcp login rl_environment -> browser Google login -> Dex token stored for Codex MCP calls
```

If the local Codex build cannot complete remote MCP OAuth yet, use a local auth proxy that owns the Google/Dex token. Do not give normal users a shared service token.
