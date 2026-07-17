# Run the MCP server

Clone and run:

```bash
git clone https://github.com/okfn/mcp-server
cd mcp-server
uv sync          # install dependencies
uv run pytest    # optional: run the tests
uv run mcp-server
```

By default the server speaks **stdio**, which is what desktop MCP
clients (like Claude Desktop) expect. For a network server, use HTTP:

```bash
MCP_TRANSPORT=http uv run mcp-server
```

The HTTP server listens on `http://127.0.0.1:8063` by default.

## Settings

Settings live in `settings.py` and every one of them can be overridden
with an environment variable or a `local_settings.py` file:

| Setting | Default | Meaning |
|---------|---------|---------|
| `MCP_TRANSPORT` | `stdio` | `stdio` for local clients, `http` for the network |
| `MCP_HOST` | `127.0.0.1` | Bind address in HTTP mode |
| `MCP_PORT` | `8063` | Port in HTTP mode |

## What tools does it serve?

Out of the box, the server loads its own bundled example tools. The
interesting part is adding plugins with real datasets: see
[connecting a plugin](../plugins/connect.md) to install the Uruguay or
Brasil catalogs, or write your own.
