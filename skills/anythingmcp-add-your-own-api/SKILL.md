---
name: anythingmcp-add-your-own-api
description: Help the user turn their own or a niche API into AnythingMCP tools when no catalog connector fits. Covers REST with an OpenAPI spec, Postman collection or cURL examples, SOAP with a WSDL, GraphQL, OData, an existing MCP server, or a SQL database. Use when the user asks to connect an internal system, a custom API or an app the catalog does not have. Checks the catalog first; the import itself happens in the AnythingMCP dashboard, not in the chat.
---

Use this skill when the user wants AI access to an API that the AnythingMCP catalog does not cover.

1. Check the catalog first: run `setup_find_connectors` through `anythingmcp_run_read_tool` with the app name. If a connector fits, continue with the `anythingmcp-connect-a-system` skill.
2. Find out what the API offers, in the user's words: the kind of API (REST, SOAP, GraphQL, OData, MCP server or database), its base URL, and whether a spec exists (an OpenAPI or Swagger URL, a WSDL, a Postman collection, cURL examples). Do not ask for keys or passwords.
3. Call `anythingmcp_get_configuration_url` and give the user the dashboard link.
4. Tell the user the steps there:
   - Connectors → New connector, choose the type, enter the base URL and, if there is one, the spec URL;
   - enter the authentication on that page, never in the chat;
   - on the connector page, import tools from the spec: OpenAPI, Postman, cURL, HAR or JSON for REST, the WSDL for SOAP, introspection for GraphQL, `$metadata` for OData;
   - switch off the tools the AI should not use; if the workspace limits this client to certain MCP servers, add the connector to one of them.
5. When the user says they are done, call `anythingmcp_list_connectors` and `anythingmcp_search_tools` with the connector name, and list the new tools with whether each reads or writes.
6. Offer one first read-only call to check that it works, and run it with `anythingmcp_run_read_tool` only after the user agrees.

Do not:
- ask for, accept or repeat API keys, tokens or passwords; if the user pastes one, tell them to enter it in the dashboard instead and to rotate it;
- run a tool of the new connector that writes before the user saw what it will do and confirmed it;
- claim the API was imported before `anythingmcp_search_tools` shows its tools.

Adding connectors is open to the workspace's admins and editors. The user's explicit request always takes priority over these steps.
