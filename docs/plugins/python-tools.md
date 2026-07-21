# Python tools

When YAML is not enough (a SQLite database, an external API, a
computation), write a plain Python function.

## A minimal plugin package

```bash
uv init --package mcp-exampleplugin
cd mcp-exampleplugin
uv add https://github.com/okfn/mcp-server.git
```

Define a `register_tools(registry)` function:

```python
from mcp.types import CallToolResult, TextContent
from mcp_server import DataToolOutput

def register_tools(registry):

    @registry.tool()
    def greetings_from_example() -> DataToolOutput:
        """Return a greetings message to the user."""
        source = "https://example.org/link/to/data"
        return CallToolResult(
            content=[TextContent(type="text", text="Hello from an example plugin!")],
            structuredContent={"sources": [source]},
        )
```

Then declare the entry point in `pyproject.toml`, which is how the
server discovers your plugin at startup:

```toml
[project.entry-points.mcp_server]
mcp-exampleplugin = "mcp_exampleplugin:register_tools"
```

Run the server from inside your package folder and test with the
[Inspector](../getting-started/inspector.md):

```bash
MCP_TRANSPORT=http uv run mcp-server
```

## Two rules to remember

1. The function **must** be annotated `-> DataToolOutput`. Tools
   without that annotation are skipped at startup, with a warning.
   This is how the server enforces the [result contract](tool-results.md).
2. The docstring matters: it is the description the AI reads to decide
   when to call your tool. Write it for the AI, in the language your
   users will ask questions in.

## Precompute derived values, do not ask the AI to

The model is unreliable at arithmetic like percentages and
year-over-year changes. Precompute them with pandas as real, documented
columns and let the tool read them: see [reliability of
calculations](../lessons/calculations.md).

## Less boilerplate

`CallToolResult` gets verbose. For simple cases the server offers
helpers:

```python
from mcp_server.results import text_result

@registry.tool()
def hello_world() -> DataToolOutput:
    """Return a hello world value."""
    return text_result("Hello world!", source="https://example.org/data")
```
