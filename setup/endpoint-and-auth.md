# Endpoint and Auth

Public MCP endpoint:

```text
https://security-rl.useimmaculate.com/mcp
```

You do not need bearer tokens as the product experience. You need Google login as the product experience.

The reason the docs mention `Authorization: Bearer ...` is that OAuth and OIDC still send access tokens as bearer credentials on API calls. A Google login flow should look like this:

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
| `AGENT_BEARER_TOKEN` | Fallback for worker pools, smoke tests, and MCP clients that cannot complete OAuth yet. |

Product requirement:

```text
Normal user: Google login.
Worker/service account: scoped service token.
Raw shared bearer token: temporary fallback only.
```

For a true one-click MCP install, add a `/connect` page that performs the Google/Dex login and then writes or hands the resulting token to the local MCP client config. The wire protocol still uses bearer auth; the user no longer manually manages a bearer secret.
