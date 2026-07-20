# Tool results

Every tool in the platform returns **two answers at once**, for two
different readers:

- `content`: human-readable text. This is what the **LLM** reads to
  compose its reply. Always required.
- `structuredContent`: a JSON payload. This is what the **UI** (the
  chat gateway) reads to render source links, tables and charts.

This split is the heart of the traceability promise: the AI gets
words, the interface gets verifiable data.

!!! important "Only `content` reaches the AI"
    The gateway feeds `content` back to the model as the tool's reply,
    but it renders `table` and `charts` from `structuredContent`
    **directly to the screen, without passing them through the model**.
    That means the tables and charts a user sees are exactly what your
    tool function computed, human-written code over real data, not
    something the AI reformatted or could distort. Put the numbers you
    want trusted in `structuredContent`.

## What goes in `structuredContent`

| Field | Type | Required | What it does |
|-------|------|----------|--------------|
| `sources` | list | yes | Links to the original data. Rendered as source links under the answer. |
| `table` | list of rows | no | Tabular data (first row is the header). Rendered as an HTML table. |
| `charts` | list | no | Chart.js data and configuration. Rendered as charts. (In development.) |
| `force` | string | no | Text shown to the user exactly as-is, bypassing the LLM entirely. |

## Example with a table

```python
from mcp.types import CallToolResult, TextContent
from mcp_server import DataToolOutput

@registry.tool()
def list_cities() -> DataToolOutput:
    """Return the top 3 cities by population."""
    return CallToolResult(
        content=[TextContent(type="text", text="Found 3 cities sorted by population.")],
        structuredContent={
            "sources": ["https://example.org/cities-data"],
            "table": [
                ["City", "Population"],
                ["Tokyo", "37400068"],
                ["Delhi", "30290936"],
                ["Shanghai", "27058479"],
            ],
        },
    )
```

## How it is enforced

The annotation `-> DataToolOutput` ties the return value to a schema
(a Pydantic `ValidationModel`) published as
[structured output](https://github.com/modelcontextprotocol/python-sdk?tab=readme-ov-file#structured-output).
At startup, `@registry.tool()` inspects each function's return
annotation. If it is not `DataToolOutput`, the server logs a warning and
**returns the function without registering it**. The tool does not
appear in `tools/list`, so no client can call it and the LLM never
learns it exists.

!!! info "This is stricter than MCP requires"
    The Model Context Protocol has no concept of a mandatory source. A
    perfectly conformant MCP tool can return an answer from nowhere.
    We deliberately narrow the standard: in this server, declaring where
    the data came from is a condition of being registered at all.

    This is the one place where traceability stops being a principle and
    becomes a mechanism. It also means our tools are stricter than
    generic MCP tools, not incompatible with them: any MCP client can
    still call them, it just gets a richer, source-carrying payload
    than the protocol guarantees.
