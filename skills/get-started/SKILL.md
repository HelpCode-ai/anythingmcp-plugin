---
name: get-started
description: Orient a new AnythingMCP user. Use when the user first connects AnythingMCP, asks what it can do, or asks which business systems are connected to their workspace.
---

Use this skill to show the user what their AnythingMCP workspace can do right now.

1. Call `anythingmcp_list_connectors` to see the systems this connection reaches (ERP, accounting, online shop, CRM, databases, the user's own APIs) and any connector that still needs the user to finish its setup.
2. Call `anythingmcp_get_workspace_guide` and read it. It holds the workspace's notes on its data and the workflows the workspace approved.
3. Answer in a few lines:
   - which systems are connected, by name;
   - two or three concrete questions the user can ask that combine those systems;
   - for each connector listed under `needsSetup`, its `finishSetupUrl` and what is missing.
4. If nothing is connected yet, ask which app the user works with and continue with the `connect-a-system` skill.

Do not run write tools during orientation. Do not describe systems that `anythingmcp_list_connectors` did not return. The user's explicit request always takes priority over these steps.
