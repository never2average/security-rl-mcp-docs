---
title: "Endpoint and Auth"
---

[Home](/security-rl-mcp-docs/)

# Endpoint and Auth

Public MCP endpoint:

```text
https://security-rl.useimmaculate.com/mcp
```

User-facing auth is Google login through Dex/OIDC. Static bearer tokens are not the user install path.

OAuth-capable MCP clients discover auth from:

```text
https://security-rl.useimmaculate.com/.well-known/oauth-protected-resource/mcp
```

The server also returns this discovery URL in `WWW-Authenticate` when `/mcp` is called without a token.

## Why Bearer Still Appears

OAuth and OIDC still send access tokens as bearer credentials on API calls. That does not mean users should copy a shared static token. A normal user flow is:

1. User clicks Connect with Google.
2. Browser redirects to Dex at `https://security-rl.useimmaculate.com/dex`.
3. Dex sends the user through Google OAuth.
4. Dex returns an OIDC access token for audience `rl-environment-api`.
5. The MCP client sends `Authorization: Bearer <Dex access token>` on API calls.
6. The MCP server validates the JWT against Dex JWKS.

## Server Expectations

The production server should run in OIDC mode:

```text
AUTH_MODE=oidc
DEX_ISSUER_URL=https://security-rl.useimmaculate.com/dex
OIDC_AUDIENCE=rl-environment-api
```

The primary credential is a Dex/OIDC JWT created after Google login. A scoped service token can exist for controlled worker pools, daemon jobs, and smoke tests. A raw shared bearer token is not a user-facing install path.

## Client Compatibility

For MCP clients that support remote OAuth, the user should only need the MCP URL and a browser login.

For clients that do not support remote MCP OAuth yet, ship a local stdio proxy that performs Google/Dex login and injects the short-lived token into requests. The user should still never copy a long-lived shared token.


---

## Documentation Sections

- [RL Environment MCP](/index)
- [Endpoint and Auth](/setup/endpoint-and-auth)
- [Connect Codex](/setup/connect-codex)
- [Connect Claude Code](/setup/connect-claude-code)
- [MCP Control Plane](/concepts/mcp-control-plane)
- [Environments](/concepts/environments)
- [state.json](/concepts/state-json)
- [Red/Blue Boundaries](/concepts/red-blue-boundaries)
- [Reward and Trajectory](/concepts/reward-and-trajectory)
- [Local vs Hosted Agents](/concepts/local-vs-hosted-agents)
- [Case Study: Submit Application State](/workflows/submit-state)
- [Case Study: Red/Blue State Experiment](/workflows/run-state-json-experiment)
- [Case Study: Blue LLM Training](/workflows/run-blue-llm-training-experiment)
- [Case Study: Red Team Agent Loop](/workflows/red-team-agent-loop)
- [Case Study: Blue Team Agent Loop](/workflows/blue-team-agent-loop)
- [Case Study: Export Training Data](/workflows/export-training-data)
- [MCP Tool Reference](/tools/tool-reference)
- [Digital Twins Roadmap](/roadmap/digital-twins)
- [Readiness Checks](/operations/readiness-checks)
- [Troubleshooting](/operations/troubleshooting)
