[![MCP Registry](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fregistry.modelcontextprotocol.io%2Fv0.1%2Fservers%2Fio.github.HelpCode-ai%252Fanythingmcp%2Fversions%2Flatest&query=%24.server.version&label=MCP%20Registry&logo=modelcontextprotocol)](https://registry.modelcontextprotocol.io/v0.1/servers/io.github.HelpCode-ai%2Fanythingmcp/versions/latest)
[![Install in Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/install-mcp?name=anythingmcp&config=eyJ1cmwiOiJodHRwczovL2Nsb3VkLmFueXRoaW5nbWNwLmNvbS9tY3AifQ==)
[![Install in VS Code](https://img.shields.io/badge/VS_Code-Install_Server-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=anythingmcp&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fcloud.anythingmcp.com%2Fmcp%22%7D)
[![Claude](https://img.shields.io/badge/Claude-in_the_official_directory-D97757?logo=claude&labelColor=0b1220)](https://claude.ai/directory/anythingmcp)

# AnythingMCP plugin

**Work with your company's business systems from your AI client:** ERP, accounting, online shops, CRM, SQL databases and your own REST, SOAP, GraphQL or OData APIs, connected once in [AnythingMCP](https://anythingmcp.com). Ready connectors exist for software such as SAP S/4HANA, DATEV, Odoo, Shopware, weclapp and Etsy: 700+ connectors with 13,000+ tools in total.

This repository distributes the plugin, the part that lives in your AI client: the hosted AnythingMCP server (`https://cloud.anythingmcp.com/mcp`) plus skills, a rule and an agent so your assistant arrives knowing how to use it.

## What's inside

| Part | Name | What it does |
|---|---|---|
| Skills | 7 skills, see [Skills](#skills) | Teach your assistant how to use AnythingMCP well. |
| Rule | `anythingmcp` | Reads run freely, every write needs your approval, no secrets in the chat. |
| Agent | AnythingMCP Specialist | A focused agent that follows those rules. |
| MCP server | `anythingmcp` | `https://cloud.anythingmcp.com/mcp`, OAuth sign-in. |

## Skills

Each skill is a folder under [`skills/`](skills) with a `SKILL.md`.

- [`anythingmcp-get-started`](skills/anythingmcp-get-started/SKILL.md): shows which systems are connected and what you can ask.
- [`anythingmcp-cross-system-briefing`](skills/anythingmcp-cross-system-briefing/SKILL.md): answers questions that need several systems, such as a customer briefing, open orders and who waits for them, or stock below reorder level.
- [`anythingmcp-connect-a-system`](skills/anythingmcp-connect-a-system/SKILL.md): adds a system from the catalog in the chat; keys are entered on a one-time page, never in the conversation.
- [`anythingmcp-query-a-database`](skills/anythingmcp-query-a-database/SKILL.md): answers from a connected SQL or MongoDB database with small read-only queries, schema first.
- [`anythingmcp-search-company-files`](skills/anythingmcp-search-company-files/SKILL.md): finds and reads documents in folders connected to File Search, and cites file, page and date.
- [`anythingmcp-add-your-own-api`](skills/anythingmcp-add-your-own-api/SKILL.md): turns your own REST, SOAP, GraphQL or OData API, or an MCP server, into tools through the dashboard.
- [`anythingmcp-status`](skills/anythingmcp-status/SKILL.md): checks what works and what still needs you, connector by connector.

The skills only use the tools the AnythingMCP server lists on `/mcp` (`anythingmcp_list_connectors`, `anythingmcp_search_tools`, `anythingmcp_describe_tool`, `anythingmcp_run_read_tool`, `anythingmcp_run_write_tool`, `anythingmcp_get_workspace_guide`, `kg_how_to_obtain`, `anythingmcp_get_configuration_url`) and the workspace tools reached through them.

File Search is on every AnythingMCP Cloud plan, with folder and file limits per plan. Self-hosted, it needs a paid licence after the 30-day evaluation.

## Install

- **Claude Code**: add this repository as a marketplace, then install the plugin:
  ```
  /plugin marketplace add HelpCode-ai/anythingmcp-plugin
  /plugin install anythingmcp@anythingmcp
  ```
  On Claude Code 2.1.275 or later, one step also works: `/plugin install anythingmcp --marketplace HelpCode-ai/anythingmcp-plugin`. Then run `/mcp` to sign in to AnythingMCP.
- **Skills only (any agent that reads `SKILL.md`)**: `npx skills add HelpCode-ai/anythingmcp-plugin`. Add the MCP server `https://cloud.anythingmcp.com/mcp` to your client as well; the skills need it.
- **Claude (claude.ai, desktop)**: add AnythingMCP from the [Claude directory](https://claude.ai/directory/anythingmcp).
- **Cursor**: install AnythingMCP from [cursor.directory](https://cursor.directory/plugins/anythingmcp), or use the badge above for the MCP server alone.
- **Gemini CLI**: `gemini extensions install https://github.com/HelpCode-ai/anythingmcp-plugin`, then `/mcp auth anythingmcp`. This installs the MCP server from `gemini-extension.json`.
- **GitHub Copilot CLI**: this repository is a plugin (`.github/plugin/plugin.json`).
- **VS Code**: use the badge above, or add `https://cloud.anythingmcp.com/mcp` (`type: http`).
- **Any other MCP client**: add `https://cloud.anythingmcp.com/mcp` as a remote server.

Sign-in uses OAuth; during sign-in you choose which workspace the client may reach. You need an AnythingMCP workspace: sign up at [cloud.anythingmcp.com](https://cloud.anythingmcp.com) or [run it yourself](https://github.com/HelpCode-ai/anythingmcp).

## How it behaves

- Reading and writing are separate tools; the client asks before every write.
- Every call runs with your company's own credentials for that system and is recorded in the workspace's audit log.
- Roles decide which systems and tools each person can reach.
- On the shared endpoint, payment and banking connectors serve only their read tools, and cryptocurrency and image, video or audio generation connectors are not served; they work on their server's own URL.

## Links

- Product: [anythingmcp.com](https://anythingmcp.com)
- Source of the server: [HelpCode-ai/anythingmcp](https://github.com/HelpCode-ai/anythingmcp)
- MCP Registry: `io.github.HelpCode-ai/anythingmcp`
- Privacy policy: [anythingmcp.com/privacy-policy](https://anythingmcp.com/privacy-policy)
- Support: [anythingmcp.com/contact](https://anythingmcp.com/contact)

Maintained by [helpcode.ai](https://helpcode.ai). Licensed under AGPL-3.0, like AnythingMCP.
