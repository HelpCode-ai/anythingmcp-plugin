---
name: anythingmcp-status
description: Check the health of the user's AnythingMCP connection. Use when tools fail, results look stale, the user asks "is AnythingMCP working", "why can't you reach my ERP", or after the user finished setting up a connector.
---

Use this skill to find out what works and what needs the user, without guessing.

1. Call `anythingmcp_list_connectors`.
   - If the call itself fails with an authentication error, the client is not signed in: tell the user to reconnect AnythingMCP in their client's MCP settings (Cursor: Settings → Tools & MCP → Connect) and sign in on the AnythingMCP page.
   - If `connectors` is empty and there is no `needsSetup`, nothing is connected yet: continue with the `anythingmcp-connect-a-system` skill.
2. For every entry under `needsSetup`, give the user its name, what is missing and its `finishSetupUrl`.
3. If the user reported a failing tool, call `anythingmcp_describe_tool` for it and run it once more with `anythingmcp_run_read_tool` (reads only). Report the error in plain words: an expired sign-in at the vendor, a missing permission, a wrong setting or a vendor outage. Do not retry writes.
4. Close with one line per connector: ready, needs the user (with the link), or failing (with the reason).

Do not change anything while checking. The user's explicit request always takes priority over these steps.
