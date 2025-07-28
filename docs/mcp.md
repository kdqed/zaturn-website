---
title: "Using Zaturn as an MCP"
description: "AI-powered data analysis for everyone"
---

Once you've [installed Zaturn](/docs/install), you can set it up to use as an MCP as follows:

## Add Zaturn & Data sources to MCP Config

Modify your LLM client's MCP config JSON file to add Zaturn. You can link data sources as `args`. An example is shown below:

```json
"mcpServers": {
  "zaturn": {
    "command": "zaturn_mcp",
    "args": [
      "postgresql://username:password@host:port/dbname",
      "mysql://username:password@host:port/dbname",
      "sqlite:////full/path/to/sample_dbs/northwind.db",
      "clickhouse://username:password@host:port/dbname",
      "mssql://user:pwd@hostname:port/dbname",
      "/full/path/to/sample_dbs/titanic.parquet",
      "/full/path/to/sample_dbs/ny_aq.csv",
      "/full/path/to/sample_dbs/duckdb_sample.duckdb"
    ]
  },
}
```
