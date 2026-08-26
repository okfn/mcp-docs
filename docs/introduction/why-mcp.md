# Why MCP? An open model for public data

The [Model Context Protocol](https://modelcontextprotocol.io/) (MCP) is
an open standard, introduced by Anthropic in late 2024 and since
adopted across the AI industry, that defines how AI applications
connect to external data and tools. An MCP **client** (a chat
interface, an IDE, a desktop assistant) talks to an MCP **server**,
which exposes **tools** the model can invoke, **resources** the client
can read, and **prompts**, over two standard transports: stdio (local)
and HTTP (network). The specification and SDKs are maintained openly at
[modelcontextprotocol.io](https://modelcontextprotocol.io/).

This platform is a direct application of the standard: datasets are
exposed as MCP tools and resources, the server speaks both transports,
and any MCP-capable client (Claude Desktop, VS Code, MCP Inspector, our
chat gateway) can connect to it unchanged. See the
[architecture](../dev/architecture.md) page for how the protocol calls
fit the runtime cycle, and where we are stricter than the standard
(the source contract).

## Why we chose it

- **Standardization and plug-and-play design.** Good practices are
  embedded in the server architecture; new data sources connect from
  templates without rebuilding the AI interface.
- **Open, replicable framework.** Fully open source, protocol
  included: no vendor lock-in, no "black box".
- **Proven local autonomy.** During the pilots, partner technicians
  built an MCP server over a new data source unprompted.
- **A growing reusable toolkit.** A new data assistant starts from a
  template rather than from scratch, easier for less experienced
  technical teams to adopt.
