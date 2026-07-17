# Plugins

A plugin is a git repo that teaches the MCP server about a set of
datasets. We scope each plugin to a **focused data domain** (for
example Uruguay's energy balance) rather than to a whole open data
portal, which tends to grow too general. The Uruguay energy and Brasil
catalogs are plugins; yours can be too. See [why we scope plugins
narrowly](../lessons/scope.md) for the reasoning.

A plugin can describe its tools in two ways, and mix both freely:

- [**Python tools**](python-tools.md): plain Python functions. This is
  the main path, and what we reach for in practice: it handles anything
  from a simple lookup to databases, APIs and computations, and stays
  clear as a dataset grows.
- [**YAML datasets**](yaml-datasets.md): declare a query in a small
  `.yaml` file, no programming required. Handy for building simple
  queries quickly, but only really suited to very simple datasets, and
  worth understanding its limits first. See [the YAML
  trade-off](../lessons/yaml-tradeoff.md).

Whatever the style, every tool must follow the same
[result contract](tool-results.md): a text answer for the AI plus
structured data (sources, tables, charts) for the UI.

## The path to your own plugin

1. Start from the existing catalogs as templates:
   [Uruguay's energy plugin](../catalogs/uruguay.md) (Python) or
   [Brasil](../catalogs/brasil.md) (YAML, simple datasets).
2. Write your first tool as a [Python function](python-tools.md), or a
   YAML dataset if it really is a simple one.
3. Test it locally with [MCP Inspector](../getting-started/inspector.md).
4. [Give your plugin a description and sample questions](plugin-info.md)
   so the chat shows a nice landing card.
5. [Connect it to a server](connect.md).

!!! tip "Learn from a real deployment"
    Before you go deep, skim the [lessons from the Uruguay
    pilot](../lessons/index.md). Two are especially practical when
    building a plugin: [precompute derived values instead of asking the
    AI](../lessons/calculations.md), and [give the AI a domain
    glossary](../lessons/glossary.md) by injecting official definitions
    into your tools' context.
