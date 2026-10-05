[![MCP Registry](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fregistry.modelcontextprotocol.io%2Fv0.1%2Fservers%2Fio.github.HelpCode-ai%252Fanythingmcp%2Fversions%2Flatest&query=%24.server.version&label=MCP%20Registry&logo=modelcontextprotocol)](https://registry.modelcontextprotocol.io/v0.1/servers/io.github.HelpCode-ai%2Fanythingmcp/versions/latest)
[![Install in Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/install-mcp?name=anythingmcp&config=eyJ1cmwiOiJodHRwczovL2Nsb3VkLmFueXRoaW5nbWNwLmNvbS9tY3AifQ==)
[![Install in VS Code](https://img.shields.io/badge/VS_Code-Install_Server-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=anythingmcp&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fcloud.anythingmcp.com%2Fmcp%22%7D)
[![Claude](https://img.shields.io/badge/Claude-in_the_official_directory-D97757?logo=claude&labelColor=0b1220)](https://claude.ai/directory/anythingmcp)

# AnythingMCP plugin

**Work with your company's business systems from your AI client:** ERP, accounting, online shops, CRM, SQL databases and your own REST, SOAP, GraphQL or OData APIs, connected once in [AnythingMCP](https://anythingmcp.com). Ready connectors exist for software such as SAP S/4HANA, DATEV, Odoo, Shopware, weclapp and Etsy, 260+ in total.

This repository distributes the plugin, the part that lives in your AI client: the hosted AnythingMCP server (`https://cloud.anythingmcp.com/mcp`) plus skills, a rule and an agent so your assistant arrives knowing how to use it.

## What's inside

| Part | Name | What it does |
|---|---|---|
| Skill | `anythingmcp-get-started` | Shows which systems are connected and what you can ask. |
| Skill | `anythingmcp-cross-system-briefing` | Answers questions that need several systems: a customer briefing (orders, invoices, location), open orders and who waits for them, stock below reorder level. |
| Skill | `anythingmcp-connect-a-system` | Adds a system from the chat. Keys are entered on a one-time page, never in the conversation. |
| Skill | `anythingmcp-status` | Checks what works and what still needs you, connector by connector. |
| Rule | `anythingmcp` | Reads run freely, every write needs your approval, no secrets in the chat. |
| Agent | AnythingMCP Specialist | A focused agent that follows those rules. |
| MCP server | `anythingmcp` | `https://cloud.anythingmcp.com/mcp`, OAuth sign-in. |

## Install

- **Cursor**: use the badge above, or install AnythingMCP from [cursor.directory](https://cursor.directory/plugins/anythingmcp).
- **Claude**: add AnythingMCP from the [Claude directory](https://claude.ai/directory/anythingmcp). Claude Code can also load this repository as a plugin (`.claude-plugin/plugin.json`).
- **GitHub Copilot CLI**: this repository is a plugin (`.github/plugin/plugin.json`).
- **Gemini CLI**: `gemini extensions install https://github.com/HelpCode-ai/anythingmcp-plugin`, then `/mcp auth anythingmcp`.
- **VS Code**: use the badge above, or add `https://cloud.anythingmcp.com/mcp` (`type: http`).
- **Any other MCP client**: add `https://cloud.anythingmcp.com/mcp` as a remote server.

Sign-in uses OAuth; during sign-in you choose which workspace the client may reach. You need an AnythingMCP workspace: sign up at [cloud.anythingmcp.com](https://cloud.anythingmcp.com) or [run it yourself](https://github.com/HelpCode-ai/anythingmcp).

## How it behaves

- Reading and writing are separate tools; the client asks before every write.
- Every call runs with your company's own credentials for that system and is recorded in the workspace's audit log.
- Roles decide which systems and tools each person can reach.
- Payment, banking and trading connectors are not served on the shared endpoint.

## Links

- Product: [anythingmcp.com](https://anythingmcp.com)
- Source of the server: [HelpCode-ai/anythingmcp](https://github.com/HelpCode-ai/anythingmcp)
- MCP Registry: `io.github.HelpCode-ai/anythingmcp`
- Privacy policy: [anythingmcp.com/privacy-policy](https://anythingmcp.com/privacy-policy)
- Support: [anythingmcp.com/contact](https://anythingmcp.com/contact)

Maintained by [helpcode.ai](https://helpcode.ai). Licensed under AGPL-3.0, like AnythingMCP.
