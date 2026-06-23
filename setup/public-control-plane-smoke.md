# Public Control Plane Smoke

Use this page to confirm the public MCP control plane is reachable and advertising OAuth discovery.

## Endpoint

```text
https://security-rl.useimmaculate.com/mcp
```

## Unauthenticated Check

A request without OAuth should return `401` and a `WWW-Authenticate` header pointing at protected-resource metadata. That is expected.

```bash
curl -i https://security-rl.useimmaculate.com/mcp
```

Expected behavior:

- HTTP `401` when no OAuth token is present.
- `WWW-Authenticate` includes the protected resource metadata URL.
- The metadata URL advertises Dex/OIDC as the authorization server.

## Authenticated Check

For normal users, complete Google login through the coding-agent MCP OAuth flow. After OAuth completes, the client should be able to call `tools/list` without asking the user to paste a shared token.

For automated workers, use a scoped service credential managed by the worker runtime. Do not publish that credential in user documentation.
