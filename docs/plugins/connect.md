# Connect a plugin to a server

There are two ways to get a plugin's tools into a running server.

## Option 1: pip install (Python plugins)

The server scans all installed Python packages for `mcp_server` entry
points at startup. So connecting a plugin is just installing it into
the same environment:

```bash
uv pip install "git+https://github.com/okfn/mcp-server"
uv pip install "git+https://github.com/okfn/mcp-exampleplugin"
uv run mcp-server
```

## Option 2: tool sources (YAML repos)

For repos of declarative YAML datasets, list them in the server's
`deploy/tool_sources.yaml`. The server clones them and loads the YAML
files from the given path:

```yaml
- name: mcp-dados-brasil
  repo: git@github.com:okfn/mcp-dados-brasil.git
  path: datasets     # folder inside the repo where the tools live
  ref: main
```

### Private repos

If the repo is private, add a read-only deploy key:

```yaml
  key: deploy/keys/mcp-dados-brasil-key
```

Generate the key pair, upload the public half to the repo's deploy
keys on GitHub (read access is enough), and place the private file on
the server with permissions `600`:

```bash
ssh-keygen -t ed25519 -f keys/mcp-dados-brasil-key -N "" -C "deploy@mcp-server"
```

## After changing a plugin

Push to the plugin repo, then re-fetch / restart on the server. Tools
are loaded once, at startup.
