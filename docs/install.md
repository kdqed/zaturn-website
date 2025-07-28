---
title: "Installing Zaturn"
description: "AI-powered data analysis for everyone"
---

Follow the steps below to install Zaturn.

## 1. Install Python and uv

Zaturn is built with Python, so you need Python to run it. You don't need to know Python programming though.

[uv](https://github.com/astral-sh/uv) is a package manager for Python, and if you're starting from scratch, it's pretty easy to get uv first and then install Python using uv.

uv can be installed on MacOS/Windows/Linux using the [instructions on their page](https://docs.astral.sh/uv/getting-started/installation/). Then, run the following command to install Python:

```bash
$ uv python install
```

## 2. Install Zaturn from PyPI

Install the [Zaturn package from PyPI](https://pypi.org/project/zaturn/) using the following command:
```bash
$ uv tool add zaturn
```

OR use `pip` if you already have it:

```bash
$ pip install zaturn
```

## 3. Use Zaturn

Zaturn can be used as an [MCP](/docs/mcp) or as a [web interface](/docs/webui).
