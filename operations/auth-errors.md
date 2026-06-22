# Auth Errors

`missing bearer token` means no Authorization header was sent. OAuth-capable MCP clients should read the `WWW-Authenticate` header, fetch the protected-resource metadata, and start Google/Dex login.

`invalid bearer token` means the token is stale, malformed, wrong audience, or not signed by Dex.
