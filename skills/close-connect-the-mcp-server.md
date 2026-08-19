---
name: Connect an agent to the Close MCP server at the right privilege level
description: >-
  Reach Close's hosted MCP server over OAuth or an API key, choose the scope
  tier deliberately, and know which capabilities are MCP-only versus REST-only.
api: mcp/close-mcp.yml
endpoint: https://mcp.close.com/mcp
operations: []
mcp_tools:
  - lead_search
  - search
  - fetch_lead
  - create_lead
  - update_opportunity
  - delete_lead
  - schedule_voice_agent_call
generated: '2026-08-13'
method: generated
source: >-
  Grounded in mcp/close-mcp.yml (tool inventory transcribed from
  https://developer.close.com/mcp/tools) and mcp/close-tool-crosswalk.yml.
---

# Connect an agent to the Close MCP server

Close ships a **hosted remote** MCP server. There is no npx package and nothing to install —
the endpoint is callable now:

```
https://mcp.close.com/mcp
```

Transport is **HTTP Streamable**. SSE is explicitly not supported.

## Authenticate

**Preferred — OAuth 2.0 with Dynamic Client Registration.** Any DCR-capable MCP client
(Claude, Claude Code, Cursor, VS Code, n8n) can register itself:

```
claude mcp add --scope user --transport http close https://mcp.close.com/mcp
```

The unauthenticated endpoint answers `401` with a correct RFC 9728 challenge pointing at
`https://mcp.close.com/.well-known/oauth-protected-resource`, which names
`https://api.close.com/` as the authorization server. PKCE (`S256`) is required.

**Alternative — API key headers**, for custom setups:

```
Close-API-Key: <your Close API key>
Close-Scope:   mcp.read | mcp.write_safe | mcp.write_destructive
```

Be aware of what this second path means: under API-key auth the **client asserts its own
scope in a header**. Nothing server-side binds the key to a tier. If you want the privilege
boundary enforced rather than declared, use OAuth.

## Choose the scope deliberately — the tiers are cumulative

| Scope | Adds | Total tools |
|---|---|---|
| `mcp.read` | search, fetch, list, reporting | 57 |
| `mcp.write_safe` | create/update tools that add data | 73 |
| `mcp.write_destructive` | update, delete, enrich, dispatch AI calls | 107 |

`mcp.write_destructive` is where the irreversible tools live: `delete_lead` (removes the
company and all of its addresses, contacts, opportunities, tasks and activities),
`delete_contact`, `enrich_field` (writes an AI-inferred value onto a record), and
`schedule_voice_agent_call` (queues an outbound AI phone call to a real person).
**Default to `mcp.read` and escalate only for a specific task.**

Note the contrast with REST: the REST API's only scope is `all.full_access`. MCP is the
*only* Close surface where least privilege is expressible at all.

## Know what is MCP-only

14 of the 107 tools have no REST equivalent — mapping in `mcp/close-tool-crosswalk.yml`:

- The entire **voice agent (Chloe)** product: `find_voice_agents`, `get_voice_agents`,
  `get_voice_agent_overview_report`, `get_voice_agent_performance_report`,
  `propose_voice_agent_update`, `apply_voice_agent_update`, `schedule_voice_agent_call`.
- **Natural-language search**: `search` and `paginate_search`, backed by the Advanced
  Filtering API which is not in the OpenAPI.
- **Aggregation**: `aggregation` plus its `get_fields` companion. Call `get_fields` first —
  the tool description requires it.
- **Docs retrieval**: `close_product_knowledge_search`.

## Know what is REST-only

212 of Close's 300 REST operations have no MCP tool: telephony and phone-number management,
exports, bulk actions, reporting, webhook subscriptions, memberships, roles, connected
accounts, send-as, unsubscribes, dialers and integration links. If your agent needs any of
those, it needs an HTTP client as well as an MCP connection.

## A second, different server

`https://developer.close.com/_mcp/server` is a **separate** anonymous server exposing one
read-only tool, `searchDocs`, over the developer documentation. It holds no CRM data. Do not
conflate the two.

## Recovering a real input schema

`tools/list` on `mcp.close.com` is auth-gated, so an unauthenticated agent cannot introspect
input schemas. Once connected, introspect for real. Until then, `mcp/close-tool-crosswalk.yml`
binds 93 of the 107 tools to the backing OpenAPI `operationId`, whose `parameters` and
`requestBody` are the honest approximation of each tool's input contract.
