# The Alliance Marketing: Claude plugin

Product marketing guidance from [The Alliance](https://www.productmarketingalliance.com/),
grounded in a curated library of practitioner content: positioning, messaging,
differentiation, pricing, launches, go-to-market, ICP and sales enablement.

This repo is the distribution channel only. It carries the plugin manifest, the
remote server address and the router skill — the server itself is hosted at
`https://mcp.allianceteam.io/mcp`.


## Install

This plugin is distributed as a repository link, for **Claude Desktop and
claude.ai** (not the Claude Code CLI). Add it as a plugin marketplace source:

```
https://github.com/pmalliance/product-marketing-mcp.git
```

Claude reads `.claude-plugin/marketplace.json` from this repo and offers
**The Alliance Marketing** for install. Approve the OAuth prompt to connect
to the hosted MCP server — no API keys required.


## What you get

| Component | What it does |
|-----------|--------------|
| `plugin/.mcp.json` | Connects Claude to the hosted MCP server. OAuth is negotiated by the client — no keys or secrets to paste. |
| `plugin/skills/alliance-mcp-governor/` | A router skill that is active *before* tool discovery, so product marketing questions get routed into the connector instead of answered from general knowledge. |

Ask a product marketing question the way you normally would — "how do I explain
what we do to a technical buyer", "what makes us different from X", "who is this
actually for" — and Claude will pull from the library and cite the practitioners
it drew on.


## Support

- Docs and connection help: <https://mcp.allianceteam.io/docs>
- Membership and account questions: The Alliance member support

Issues with the plugin itself can be filed on this repo.
