# Product Marketing Alliance Plugin for Claude

Product marketing guidance from [Product Marketing Alliance](https://www.productmarketingalliance.com/)
(The Alliance), grounded in a curated library of practitioner content: positioning, messaging,
differentiation, pricing, launches, go-to-market, ICP and sales enablement. Answers cite the
expert practitioners they draw on by name, title and company.

This repo is the distribution channel only. It carries the plugin manifest, the remote server
address and a router skill. The server itself is hosted by The Alliance at
`https://mcp.thealliance.io/mcp`.


## What you get

| Component | What it does |
|-----------|--------------|
| `plugin/.mcp.json` | Connects Claude to The Alliance's hosted MCP server, so there's no server URL to type. You authenticate once (see below). |
| `plugin/skills/alliance-mcp-governor/` | A router skill that is active *before* tool discovery, so product marketing questions get routed to the connector instead of answered from general knowledge. Non-product-marketing questions are answered normally. |

### Tool

The server exposes one tool, **`pmm_mentor`**. It is read-only: it never changes anything in
your environment or accounts.

1. You ask a product marketing question.
2. The tool returns a few clarifying questions (with suggested answers) so the answer fits your
   situation.
3. Using your answers, it searches The Alliance's library of articles and expert videos and
   returns the most relevant insights, with the speakers named.
4. Claude writes the answer from that material.


## Install

Available for Claude Desktop and claude.ai.

1. Open **Settings → Capabilities → Plugins**.
2. Click **Add marketplace → Add from a repository** and paste
   `https://github.com/pmalliance/product-marketing-mcp.git`.
3. Turn on **Sync automatically**, then click **Sync**.
4. Select **Product Marketing Alliance Plugin** and click **Install**.
5. Click **Manage → Connectors → Connect** and sign in (see below).


## Authentication

The connector uses OAuth 2.0 with PKCE. Sign in with either:

- your Alliance **Client ID** and **Client Secret**, from your Alliance account dashboard
  (see <https://mcp.thealliance.io/docs#credentials>), or
- **Log in with Google**, if you're a paid member.

The server checks your membership before granting access, and your plan sets your usage
allowance. Access tokens expire after one hour and are refreshed automatically while your
membership is active.


## Example prompts

- "How do I explain what we do to a technical buyer?"
- "What makes us different from our main competitor, and how should we say it?"
- "Who is our product actually for? Help me define our ICP."
- "How should we price and package a new add-on?"
- "What should a launch plan for a major feature include?"


## Data handling and privacy

What happens to the information you give the connector:

- **What is sent:** your question and your answers to the clarifying questions. Your email
  address is used only at sign-in to check your membership, and is not sent to an AI model
  unless you include it in your question.
- **How it's processed:** The Alliance uses OpenAI to check your question's topic and to write
  and encode search queries, and Pinecone to search and rank results from The Alliance's
  content library. No model is trained or fine-tuned on your data, and The Alliance has not
  opted in to OpenAI's data sharing. OpenAI may keep requests for up to 30 days for abuse
  monitoring, unless longer retention is required by law. Pinecone may use query data to
  operate and improve its own services, under its own terms.
- **What is stored:** each question and its context are recorded in The Alliance's usage log,
  linked to your account, for plan limits and usage records. The log is kept for 24 months and
  then deleted. Deleted data may remain in secure backups for up to 98 days before it is
  permanently removed. The server keeps no conversation history; your history stays in Claude.
- **Where:** the server runs in London, UK. Account and usage data is stored in the EU. OpenAI
  and Pinecone process requests in the United States, under the EU Standard Contractual
  Clauses with the UK Addendum.
- **Never:** your questions are not added to the content library, shown to other members, or
  used to train AI models.

Full details: [Privacy policy](https://www.productmarketingalliance.com/privacypolicy/).
For a customer data-handling statement for procurement or IT review, or to request access
to or deletion of your data, contact hello@productmarketingalliance.com.


## Support

- Docs and connection help: <https://mcp.thealliance.io/docs>
- Help centre: <https://www.productmarketingalliance.com/help-centre/>
- Email: hello@productmarketingalliance.com
- Issues with the plugin itself: open an issue on this repo.


## License

[MIT](LICENSE). This covers the files in this repository only. The Alliance's hosted server
and content library are not covered by this license.
