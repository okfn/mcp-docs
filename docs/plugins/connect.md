# Connect a plugin to a server

Connecting a plugin is just installing it into the server's
environment. At startup the server scans all installed packages and
registers their tools:

```bash
uv pip install "git+https://github.com/okfn/mcp-server"
uv pip install "git+https://github.com/okfn/mcp-exampleplugin"
uv run mcp-server
```

Python plugins are discovered through their `mcp_server` entry point.
Packages named `mcp_server_*` that carry [YAML
datasets](yaml-datasets.md) are discovered by name convention.

For a private plugin repo, install from a git URL your environment can
reach, for example over SSH with a read-only deploy key.

This is also how the [production
deployment](../operations/deployment.md) works: the server image
installs the plugin packages at build time.

## After changing a plugin

Push to the plugin repo, then reinstall the package and restart the
server. Tools are loaded once, at startup.
