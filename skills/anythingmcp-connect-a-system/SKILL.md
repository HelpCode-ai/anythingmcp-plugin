---
name: anythingmcp-connect-a-system
description: Add a business system (ERP, online shop, accounting, CRM, marketplace, messaging or data API) to the user's AnythingMCP workspace from the chat, without the user ever typing credentials into the conversation.
---

Use this skill when the user wants to work with an app that is not connected yet. Adding connectors is open to the workspace's admins and editors.

1. Read `anythingmcp_get_workspace_guide` with connector `AnythingMCP Setup` once; it describes the setup tools.
2. Run `setup_find_connectors` through `anythingmcp_run_read_tool` with the app name or topic. Show what was found and what setting it up involves. If nothing fits, call `anythingmcp_get_configuration_url`: the user can connect their own API from the dashboard.
3. Confirm with the user which connector to add and collect only the non-secret settings the result lists as allowed (for example a shop URL or a tenant name).
4. After the user confirms, run `setup_install_connector` through `anythingmcp_run_write_tool` with the connector id and those settings.
5. If the answer contains a one-time link, give it to the user: they enter keys or sign in to the provider there, outside the chat.
6. When the user says they are done, run `setup_get_status` through `anythingmcp_run_read_tool` and report whether the connector is ready.

Never ask for, accept or repeat passwords, API keys, tokens or secrets in the chat. If the user pastes one, do not use it: tell them to enter it on the secure link instead and suggest they rotate it.
