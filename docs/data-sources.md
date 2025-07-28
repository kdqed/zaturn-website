---
title: "Supported Data Sources"
description: "AI-powered data analysis for everyone"
---

Zaturn supports the data sources listed below. For each data source, please take security precautions by ensuring read-only access through URL credentials, or making backup copies of data files. This is critical because AI LLMs will be running SQL on your data directly and they can be quite unpredictable. 

## Clickhouse

Clickhouse is supported using the [ClickHouse Connect Python Driver](https://clickhouse.com/docs/integrations/python) under the hood.

You can specify database URLs in the following format:

```
clickhouse://username:password@host:port/dbname
```

Zaturn tries to not let any data to be modified by executing `SET readonly=1;` before every query. However, please use an `username` with read-only access to ensure no data is modified.

## CSV

Zaturn handles running SQL on CSV files using the [DuckDB Python client](https://duckdb.org/docs/stable/clients/python/overview.html). 

- For Zaturn Studio, upload the CSV files.
- For MCP, specify the full path to the CSV file in the MCP config (e.g.: /full/path/to/sample_dbs/ny_aq.csv). Make a backup copy of the CSV just in case the file is modified or cleared.

## DuckDB

Zaturn handles running SQL on `.duckdb` database files using the [DuckDB Python client](https://duckdb.org/docs/stable/clients/python/overview.html). Please ensure that the extension of the file is `.duckdb` to ensure that the appropriate client is used to read this file.

- For Zaturn Studio, upload the DuckDB file.
- For MCP, specify the full path to the DuckDB file in the MCP config (e.g.: /full/path/to/sample_dbs/duckdb_sample.duckdb). Make a backup copy of the DuckDB file just in case the file is modified or cleared.

## MySQL

For working with MySQL databases, Zaturn uses [SQLAlchemy](https://docs.sqlalchemy.org/en/20/dialects/mysql.html)

You can specify database URLs in the following format:

```
mysql://username:password@host:port/dbname
```

Zaturn tries to not let any data to be modified by executing `SET SESSION TRANSACTION READ ONLY;` before every query in a separate session. However, please use an `username` with read-only access to ensure no data is modified.

## Parquet

Zaturn handles running SQL on Parquet files using the [DuckDB Python client](https://duckdb.org/docs/stable/clients/python/overview.html). 

- For Zaturn Studio, upload the Parquet files.
- For MCP, specify the full path to the Parquet file in the MCP config (e.g.: /full/path/to/sample_dbs/titanic.parquet). Make a backup copy of the Parquet file just in case the file is modified or cleared.

## PostgreSQL

Zaturn uses [SQLAlchemy](https://docs.sqlalchemy.org/en/20/dialects/postgresql.html) to work with PostgreSQL databases.

You can specify database URLs in the following format:

```
postgresql://username:password@host:port/dbname
```

Zaturn tries to not let any data to be modified by setting `postgresql_readonly=True` in the connection options. However, please use an `username` with read-only access to ensure no data is modified.

## SQLite

Zaturn works with SQLite databases files using [SQLAlchemy](https://docs.sqlalchemy.org/en/20/dialects/sqlite.html). 

- For Zaturn Studio, upload the SQLite files.
- For MCP, specify the full path to the SQLite file, prefixed with `sqlite:///` in the MCP config (e.g.: sqlite:////full/path/to/sample_dbs/northwind.db). Make a backup copy of the database file just in case the file is modified or cleared.

Zaturn tries to not let any data to be modified by executing `PRAGMA query_only = ON;` before every query. However, take adequate precautions on your end to avoid data losses.

## SQL Server

For working with MS SQL Server databases, Zaturn uses [SQLAlchemy](https://docs.sqlalchemy.org/en/20/dialects/mssql.html)

You can specify database URLs in the following format:

```
mssql://username:password@host:port/dbname
```

> IMPORTANT: With MSSQL, it has not been possible to ensure that the database connection is read-only using the available client libraries. Therefore, please ensure that the `username` specified in the database URL has only read-only access and cannot modify any data.



