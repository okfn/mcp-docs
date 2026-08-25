# Why MCP? An open model for public data

The [Model Context Protocol](https://modelcontextprotocol.io/) (MCP)
provides an open, standardized architecture for connecting AI models
directly to public open data. Instead of building custom, proprietary
integrations for every dataset, MCP establishes an open and reusable
method for responsible data retrieval.

Key reasons for choosing MCP:

- **Standardization and plug-and-play design.** MCP embeds good
  practices directly into the server architecture. If datasets follow
  standard structures, developers can connect new data sources using
  templates without rebuilding the AI interface from scratch.
- **Open, replicable framework.** Developed as part of the OKFN AI
  Learning Labs, the stack is fully open source, avoiding vendor
  lock-in or proprietary "black box" solutions.
- **Proven local autonomy.** The architecture allows technical teams to
  extend the system independently. During the pilots, partner
  technicians successfully built an MCP server over a new data source
  unprompted.
- **A growing reusable toolkit.** Deploying a new data assistant starts
  from a template rather than from scratch, making it easier for less
  experienced technical teams to adopt and scale.

Because MCP is an open standard, the server also works with any
MCP-capable client, not only our chat gateway: Claude Desktop, VS Code,
MCP Inspector and others.
