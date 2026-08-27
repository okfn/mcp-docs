# Brazil implementation

**Repo:** [okfn/mcp-dados-brasil](https://github.com/okfn/mcp-dados-brasil)
&middot; **Source:** [portaldatransparencia.gov.br](https://portaldatransparencia.gov.br)
&middot; **Language:** Portuguese

MCP tools over Brasil's *emendas parlamentares* (parliamentary
amendments), published by the Office of the Comptroller General (CGU)
on the Portal da Transparência. All tools are
[Python tools](../plugins/python-tools.md); the plugin declares no
YAML datasets.

## Highlights

The plugin exposes tools to query amendments by locality, author,
government function and subfunction, budget action, and amendment
type, plus rankings of top recipients (*favorecidos*) and top authors,
and a [glossary](../plugins/glossaries.md) with the official
definitions from the portal's data dictionary (so the model never
confuses *empenhado*, *liquidado* and *pago* values).

## How it works

The package ships the amendments dataset (CSV files from the Portal da
Transparência download service) and a `load-emendas-db` script that
loads them into a local SQLite database. Each tool runs a SQL query
over that database with pandas and returns tables and charts through
the standard [tool results](../plugins/tool-results.md) contract.

## Installing it

It is a pip-installable Python package, registered through the
`mcp_server` entry point. Install it into the MCP server's
environment, run `load-emendas-db` once to build the local database,
and restart the server. Descriptions, parameters and sample questions
are written in Portuguese, matching the audience.

## From the field

This catalog backed a pilot with Brasil's Office of the Comptroller
General, focused on **parliamentary amendments**, one of the most
requested datasets on the portal. The goal was to test whether citizens
could ask in natural language and get answers traceable back to
official data. The findings are written up in the *Field Guide to
Connecting AI to Public Information*.
