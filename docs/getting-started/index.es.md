# Primeros pasos

Todo corre en una laptop con software libre. Vas a necesitar:

- **Python 3.14** y [uv](https://docs.astral.sh/uv/) (el gestor de
  paquetes usado en todos los repos).
- **Node.js** solo si quieres la herramienta de pruebas MCP Inspector.
- Una **API key** para un LLM compatible con OpenAI (DeepSeek, OpenAI,
  o un Ollama local, que no necesita key) solo para el chat gateway.

El orden que tiene sentido:

1. [Ejecuta el servidor MCP](mcp-server.md): el corazón de la
   plataforma.
2. [Pruébalo con MCP Inspector](inspector.md) (opcional): llama
   herramientas a mano, sin IA involucrada.
3. [Ejecuta el chat gateway](chat-gateway.md): la experiencia completa,
   IA incluida.
