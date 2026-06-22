# RL Environment MCP

The RL Environment MCP is the agent-facing control plane for submitting application `state.json`, running Red/Blue experiments, coordinating external coding-agent assignments, and collecting reward/trajectory data.

Public endpoint:

```text
https://security-rl.useimmaculate.com/mcp
```

Auth intent:

```text
User-facing auth: Google login through Dex/OIDC.
Wire-level auth: Authorization: Bearer <Dex-issued access token or fallback service token>.
```

A bearer token is still the HTTP mechanism because MCP calls are API requests. The product should not ask normal users to manage a static shared bearer token. Normal users should click Google login, receive a Dex-issued OIDC token, and let their coding agent send that token as the bearer credential.

Use these docs by workflow:

```text
concepts/     Understand the control plane and RL objects.
setup/        Connect Codex or Claude Code with Google-backed auth.
workflows/    Run common agent and RL loops.
tools/        Per-tool reference pages.
schemas/      Data shapes used by tools and API records.
examples/     Copyable examples.
operations/   Readiness, smoke tests, and troubleshooting.
```
