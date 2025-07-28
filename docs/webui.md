---
title: "Using Zaturn as a Web UI"
description: "AI-powered data analysis for everyone"
---

Once you've [installed Zaturn](/docs/install), you can setup and use the Web UI (known as Zaturn Studio) as follows:

## 1. Run Zaturn Studio

Run the following command, this will start the web interface.

```
$ zaturn_studio
```

Next, open the following URL on your browser:

> http://localhost:6066

## 2. Setup LLM API

Note that Zaturn is an open source bundle of tools that can be used by an LLM. While this part is free, providing LLM runtime for free is not possible on a solo indie-developer budget. 

Therefore, you'll have to bring your own OpenAI-compatible LLM API. Please add the following on the Zaturn Studio interface:
- API endpoint
- API key
- Model Name (thinking models work the best but cost more. Grok 3 Mini was the optimal one in my trials) 

## 3. Add Data Sources

Add data sources when prompted.
- For file-based sources (CSV/Parquet/SQLite/DuckDB), upload the files. Zaturn Studio will make its own copy of the file and work on that. 
- For database URLs, please ensure the credentials in the URLs grant just read-only access to the database. While Zaturn tries to ensure that the AI LLM cannot write/modify data on any of the linked sources, this is on a best-effort basis and not guaranteed to work with all kinds of databases.
- For more information on URL formats and the engines used for each database, see the [data sources page](/docs/data-sources)



