# AnythingMCP plugin

**Work with your company's business systems from your AI client:** ERP, accounting, online shops, CRM, SQL databases and your own REST, SOAP, GraphQL or OData APIs, connected once in [AnythingMCP](https://anythingmcp.com).

This plugin bundles the hosted AnythingMCP server (`https://cloud.anythingmcp.com/mcp`) with three skills:

| Skill | What it does |
|---|---|
| `get-started` | Shows which systems are connected and what you can ask. |
| `cross-system-briefing` | Answers questions that need several systems: a customer briefing (orders, invoices, location), open orders and who waits for them, stock below reorder level. |
| `connect-a-system` | Adds a system from the chat. Keys are entered on a one-time page, never in the conversation. |

## Install

- **Cursor**: install it from the marketplace, or add this repository as a plugin.
- **Any MCP client**: add `https://cloud.anythingmcp.com/mcp` as a remote MCP server. Sign-in uses OAuth; during sign-in you choose which workspace the client may reach.

You need an AnythingMCP workspace: sign up at [cloud.anythingmcp.com](https://cloud.anythingmcp.com) or [run it yourself](https://github.com/HelpCode-ai/anythingmcp). There are ready connectors for software such as SAP S/4HANA, DATEV, Odoo, Shopware, weclapp and Etsy.

## How it behaves

- Reading and writing are separate tools; the client asks before every write.
- Every call runs with your company's own credentials for that system and is recorded in the workspace's audit log.
- Roles decide which systems and tools each person can reach.
- Payment, banking and trading connectors are not served on the shared endpoint.

## Links

- Product: [anythingmcp.com](https://anythingmcp.com)
- Source: [HelpCode-ai/anythingmcp](https://github.com/HelpCode-ai/anythingmcp)
- Privacy policy: [anythingmcp.com/privacy-policy](https://anythingmcp.com/privacy-policy)
- Support: [anythingmcp.com/contact](https://anythingmcp.com/contact)

Maintained by [helpcode.ai](https://helpcode.ai). Licensed under AGPL-3.0, like AnythingMCP.
