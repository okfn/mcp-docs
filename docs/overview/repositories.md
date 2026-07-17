# Repositories

The platform is a workspace of small, independent git repos rather than
one big monorepo. Each repo has its own tests, its own README and its
own release pace.

## Core

| Repo | What it is |
|------|------------|
| [mcp-server](https://github.com/okfn/mcp-server) | The MCP server. Loads tools from Python modules, installed plugins and YAML files, and serves them over stdio or HTTP. |
| [mcp-chat-gateway](https://github.com/okfn/mcp-chat-gateway) | The web chat. Plain Flask + HTML/JS, no frontend framework. Connects an LLM to the MCP server and renders tables, charts and sources. |

## Data plugins

| Repo | What it is |
|------|------------|
| [mcp-datos-uruguay-ben](https://github.com/okfn/mcp-datos-uruguay-ben) | Tools over Uruguay's national energy balance (BEN), from catalogodatos.gub.uy. In Spanish. |
| [mcp-dados-brasil](https://github.com/okfn/mcp-dados-brasil) | Datasets from Brasil's open data portal (dados.gov.br). In Portuguese. |

!!! note "mcp-datos-uruguay is retired"
    The original `mcp-datos-uruguay` repo tried to cover the whole
    Uruguay portal and grew too general. It is no longer in use; the
    focused `mcp-datos-uruguay-ben` replaced it. See [why we scope
    plugins narrowly](../lessons/scope.md).

## Optional pieces

| Repo | What it is |
|------|------------|
| mcp-deployment | Docker Compose + Caddy setup used to run the public instance at mcp.okfn.org. |
| [mcp-docs](https://github.com/okfn/mcp-docs) | This documentation. |

!!! tip "Which repo do I touch?"
    Adding a dataset for an existing country: the country plugin repo.
    Adding a new country: a new plugin repo (see [plugins](../plugins/index.md)).
    Changing how tools work for everyone: `mcp-server`.
