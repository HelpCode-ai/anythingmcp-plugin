---
name: anythingmcp-cross-system-briefing
description: Answer a business question that needs data from more than one system connected to AnythingMCP, such as a customer briefing (orders, invoices, location, tax id), open or late orders with the customers waiting for them, or stock below reorder level. Use when one answer needs several lookups across the ERP, shop, accounting, CRM or databases. Read-only; any change needs the user's confirmation.
---

Use this skill when the answer needs several lookups, often in different systems of the user's AnythingMCP workspace.

1. Read `anythingmcp_get_workspace_guide` for the connectors involved, if you have not in this conversation. It says which entity, table or field holds what.
2. Find the tools with `anythingmcp_search_tools` (keywords and, when known, the connector) and read their parameters with `anythingmcp_describe_tool`.
3. When you need an id that another system produces (a customer number for the invoices, a postal code for the region), call `kg_how_to_obtain` with the name of that value as `query`. If it answers that the knowledge graph is off, use `anythingmcp_search_tools` instead.
4. Run each lookup with `anythingmcp_run_read_tool`. Run independent lookups one after the other without waiting for the user; run a lookup that needs another one's result after it.
5. Combine the results into one answer. Say which system each figure comes from, keep amounts with their currency, and give dates as the system returned them.
6. If a lookup fails or returns nothing, say so for that part and keep the rest of the answer. Never fill a gap with an estimate.

This skill only reads. If the user then asks to change something (create, update, send), describe the change and get their confirmation before calling `anythingmcp_run_write_tool`. The user's explicit request always takes priority over these steps.
