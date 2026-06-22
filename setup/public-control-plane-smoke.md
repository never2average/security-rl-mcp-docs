# Public Control Plane Smoke

Run from the server checkout:

```bash
corepack pnpm run smoke:public-control-plane
```

Raw MCP smoke:

```bash
curl -fsS   -H "Authorization: Bearer $AGENT_BEARER_TOKEN"   -H "accept: application/json, text/event-stream"   -H "content-type: application/json"   -d '{"jsonrpc":"2.0","id":1,"method":"tools/list","params":{}}'   https://security-rl.useimmaculate.com/mcp
```

Expected: HTTP 200 with a JSON-RPC `tools/list` response.
