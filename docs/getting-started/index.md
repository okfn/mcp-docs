# Getting started

Everything runs on a laptop with free software. You will need:

- **Python 3.14** and [uv](https://docs.astral.sh/uv/) (the package
  manager used across all repos).
- **Node.js** only if you want the MCP Inspector testing tool.
- An **API key** for an OpenAI-compatible LLM (DeepSeek, OpenAI,
  or a local Ollama, which needs no key) only for the chat gateway.

The order that makes sense:

1. [Run the MCP server](mcp-server.md): the heart of the platform.
2. [Test it with MCP Inspector](inspector.md): call tools by hand,
   no AI involved.
3. [Run the chat gateway](chat-gateway.md): the full experience,
   AI included.
