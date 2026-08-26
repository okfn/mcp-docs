# Primeiros passos

Tudo roda em um laptop com software livre. Você vai precisar de:

- **Python 3.14** e [uv](https://docs.astral.sh/uv/) (o gerenciador de
  pacotes usado em todos os repos).
- **Node.js** só se você quiser a ferramenta de testes MCP Inspector.
- Uma **API key** para um LLM compatível com OpenAI (DeepSeek, OpenAI,
  ou um Ollama local, que não precisa de key) só para o chat gateway.

A ordem que faz sentido:

1. [Execute o servidor MCP](mcp-server.md): o coração da plataforma.
2. [Teste com o MCP Inspector](inspector.md) (opcional): chame
   ferramentas na mão, sem IA envolvida.
3. [Execute o chat gateway](chat-gateway.md): a experiência completa,
   com IA incluída.
