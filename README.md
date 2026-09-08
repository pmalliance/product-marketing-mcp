# Product Marketing Alliance Plugin: Claude plugin

Product marketing guidance from [The Alliance](https://www.productmarketingalliance.com/),
grounded in a curated library of practitioner content: positioning, messaging,
differentiation, pricing, launches, go-to-market, ICP and sales enablement.

This repo is the distribution channel only. It carries the plugin manifest, the
remote server address and the router skill — the server itself is hosted at
`https://mcp.allianceteam.io/mcp`.


## Install

This plugin is distributed as a repository link, for **Claude Desktop and
claude.ai** (not the Claude Code CLI).

1. Open **Settings → Capabilities → Plugins**
   (`https://claude.ai/new?#settings/customize-plugins`).
2. Click **Add marketplace**.
3. Click **Add from a repository**.
4. Paste this repo's URL:
   ```
   https://github.com/pmalliance/product-marketing-mcp.git
   ```
5. Turn on **Sync automatically** so updates land without a manual reinstall, then
   click **Sync**.
6. Select **Product Marketing Alliance Plugin** and click **Install**.
7. Click **Manage → Connectors → Connect**.
8. Sign in with your Alliance **Client ID** and **Client Secret**, or click
   **Log in with Google** if you're a paid member.

Claude reads `.claude-plugin/marketplace.json` from this repo to offer the plugin for
install; the connector itself (`plugin/.mcp.json`) points at the hosted MCP server, so
you never need to type a server URL. Client ID/Secret pairs come from your Alliance
account dashboard — see <https://mcp.allianceteam.io/docs#credentials>.


## What you get

| Component | What it does |
|-----------|--------------|
| `plugin/.mcp.json` | Connects Claude to the hosted MCP server (no server URL to type). You still authenticate once — Client ID/Secret from your Alliance dashboard, or Google login for paid members. |
| `plugin/skills/alliance-mcp-governor/` | A router skill that is active *before* tool discovery, so product marketing questions get routed into the connector instead of answered from general knowledge. |

Ask a product marketing question the way you normally would — "how do I explain
what we do to a technical buyer", "what makes us different from X", "who is this
actually for" — and Claude will pull from the library and cite the practitioners
it drew on.


## Support

- Docs and connection help: <https://mcp.allianceteam.io/docs>
- Membership and account questions: The Alliance member support

Issues with the plugin itself can be filed on this repo.
