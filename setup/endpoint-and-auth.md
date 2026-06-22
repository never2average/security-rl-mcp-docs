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

The reason the protocol still mentions `Authorization: Bearer ...` is that OAuth and OIDC send access tokens as bearer credentials on API calls. A Google login flow should look like this:

```text
1. User clicks Connect with Google.
2. Browser redirects to Dex at https://security-rl.useimmaculate.com/dex.
3. Dex sends the user through Google OAuth.
4. Dex returns an OIDC access token for audience rl-environment-api.
5. The MCP client sends: Authorization: Bearer <Dex access token>.
6. The MCP server validates the JWT against Dex JWKS.
```

Current server behavior:

```text
AUTH_MODE=oidc
DEX_ISSUER_URL=https://security-rl.useimmaculate.com/dex
OIDC_AUDIENCE=rl-environment-api
```

The auth middleware accepts two credential types:

| Credential | Use |
| --- | --- |
| Dex/OIDC JWT from Google login | Primary user auth path. |
| `AGENT_BEARER_TOKEN` | Fallback for worker pools and smoke tests only. |

Product requirement:

```text
Normal user: Google login.
Worker/service account: scoped service token.
Raw shared bearer token: not a user-facing install path.
```

For clients that do not support remote MCP OAuth yet, ship a local stdio proxy that performs Google/Dex login and injects the short-lived token into requests. The user should still never copy a long-lived shared token.
