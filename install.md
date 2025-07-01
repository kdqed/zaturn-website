---
title: "Installing Zaturn"
description: "AI-powered data analysis for everyone"
---

Zaturn can be installed as a web interface or as an MCP. If this is too technical for you, please feel free to [schedule a demo](https://cal.com/kdqed/zaturn-demo) for assistance.

## 1. Setting up the Web Interface

### 1.1. Install Python and uv

Zaturn is built with Python, so you need Python to run it. You don't need to know Python programming though.

[uv](https://github.com/astral-sh/uv) is a package manager for Python, and if you're starting from scratch, it's pretty easy to get uv first and then install Python using uv.

uv can be installed on MacOS/Windows/Linux using the [instructions on their page](https://docs.astral.sh/uv/getting-started/installation/). Then, run the following command to install Python:

```bash
$ uv python install
```

### 1.2. Install Zaturn from PyPI

Install the [Zaturn package from PyPI](https://pypi.org/project/zaturn/) using the following command:
```bash
$ uv tool add zaturn
```

OR use `pip` if you already have it:

```bash
$ pip install zaturn
```

### 1.3. Run Zaturn Studio

Run the following command, this will start the web interface.

```
$ zaturn_studio
```

Next, open the following URL on your browser:

> http://localhost:6066

### 1.4. Setup LLM API

Note that Zaturn is an open source bundle of tools that can be used by an LLM. While this part is free, providing an LLM for free is not possible on a solo indie-developer budget. 

Therefore, you'll have to bring your own OpenAI-compatible LLM API. Please add the API endpoint, API key, and model name on the Zaturn studio interface.

### 1.5. Add Data Sources

Add data sources when prompted. For file-based sources, upload the files. Zaturn Studio will make its own copy of the file and work on that. For database URLs, please ensure the URLs grant just read-only access to the database. While Zaturn tries to ensure that the AI LLM cannot write/modify data on any of the linked sources, this is on a best-effort basis and not guaranteed to work 100% of the time.


## 2. Setting up the MCP Server

### 2.1. Install Python and uv

Zaturn is built with Python, so you need Python to run it. You don't need to know Python programming though.

[uv](https://github.com/astral-sh/uv) is a package manager for Python, and if you're starting from scratch, it's pretty easy to get uv first and then install Python using uv.

uv can be installed on MacOS/Windows/Linux using the [instructions on their page](https://docs.astral.sh/uv/getting-started/installation/). Then, run the following command to install Python:

```bash
$ uv python install
```

### 2.2. Install Zaturn from PyPI

Install the [Zaturn package from PyPI](https://pypi.org/project/zaturn/) using the following command:
```bash
$ uv tool add zaturn
```

OR use `pip` if you already have it:

```bash
$ pip install zaturn
```

### 2.3. Add Zaturn & Data sources to MCP Config

Modify your client's MCP config JSON file to add Zaturn. You can link data sources as `args`. An example is shown below:

```json
"mcpServers": {
  "zaturn": {
    "command": "zaturn_mcp",
    "args": [
      "postgresql://username:password@host:port/dbname",
      "mysql://username:password@host:3306/dbname",
      "sqlite:////full/path/to/sample_dbs/northwind.db",
      "clickhouse://username:password@host:port/dbname",
      "/full/path/to/sample_dbs/titanic.parquet",
      "/full/path/to/sample_dbs/ny_aq.csv",
      "/full/path/to/sample_dbs/duckdb_sample.duckdb"
    ]
  },
}
```

### 2.4. Data Intergrity Tips

For file-based sources, please have a backup copy.

For database URLs, please ensure the URLs grant just read-only access to the database. While Zaturn tries to ensure that the AI LLM cannot write/modify data on any of the linked sources, this is on a best-effort basis and not guaranteed to work 100% of the time.

