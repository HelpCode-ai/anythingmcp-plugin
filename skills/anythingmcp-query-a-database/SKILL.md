---
name: anythingmcp-query-a-database
description: Answer questions from a SQL or MongoDB database connected to AnythingMCP (PostgreSQL, MySQL, MariaDB, SQL Server, Oracle, SAP HANA, SQLite, MongoDB) with small, read-only queries. Use when the user asks for figures, lists or reports that live in a company database, or says "query the database", "run SQL" or "look it up in the tables". Reads the schema first and never changes data without the user's approval.
---

Use this skill when the answer is in a database the user's AnythingMCP workspace connected.

1. Call `anythingmcp_list_connectors` and pick the database connector. If there is none, continue with the `anythingmcp-connect-a-system` skill (search for "postgres", "mysql", "mssql", "oracle" or "mongodb").
2. Read `anythingmcp_get_workspace_guide` for that connector. Workspace notes often say which tables matter and what the columns mean.
3. Find its tools with `anythingmcp_search_tools` (connector set, query "database"). A database connector has `get_database_schema`, `get_example_queries` and `execute_query`, sometimes with a prefix such as `erp_sql_execute_query`.
4. Run the schema tool once with `anythingmcp_run_read_tool`. Use only the table and column names it returns. Run the examples tool to get the dialect right (`TOP 10` or `LIMIT 10`, quoting, date literals).
5. Call `anythingmcp_describe_tool` on the query tool and check `access`:
   - `read`: the connector is read-only and accepts only SELECT. Run it with `anythingmcp_run_read_tool`.
   - `write`: the connector accepts writes. Show the user every query and get their approval before each `anythingmcp_run_write_tool` call, even for a SELECT.
6. Keep queries small: name the columns you need, filter, aggregate in SQL and limit the rows. Results stop at 1,000 rows. When you are unsure about size, count first or read 10 rows.
7. On MongoDB the query is a JSON string: `{"collection": "orders", "filter": {"status": "open"}, "projection": {"_id": 0, "number": 1}, "sort": {"date": -1}, "limit": 10}`.
8. Answer with the figures, the query you ran in a code block, and the tables it read. Say so when a result reached the row limit.

Do not:
- run INSERT, UPDATE, DELETE, MERGE or DDL unless the user asked for that change, saw the exact statement and confirmed it;
- run DROP, TRUNCATE, GRANT or similar statements at all;
- guess table or column names, or run `SELECT *` on a large table without a limit;
- try to reach a table the database refused through another table or view: the workspace blocked it on purpose.

The user's explicit request always takes priority over these steps, but never over the confirmation rule for writes.
