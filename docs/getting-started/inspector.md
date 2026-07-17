# Test with MCP Inspector

[MCP Inspector](https://github.com/modelcontextprotocol/inspector) is
the official debugging UI for MCP servers. It lets you browse tools and
call them by hand, with no AI model in the loop. It is the fastest way
to check that a tool does what you think it does.

With the server running in HTTP mode (see
[run the MCP server](mcp-server.md)):

```bash
npx @modelcontextprotocol/inspector
```

Then, in the Inspector web page that opens:

1. Choose transport type **Streamable HTTP**.
2. Connect to `http://127.0.0.1:8063` (note: no `/mcp` suffix).
3. List the tools, pick one, fill its parameters and run it.

You can also let the Inspector launch the server itself over stdio:

```bash
npx @modelcontextprotocol/inspector uv run mcp-server
```

!!! tip
    When a tool you expected does not appear in the list, check the
    server logs at startup: tools that do not follow the
    [result contract](../plugins/tool-results.md) are skipped with a
    warning, not an error.
