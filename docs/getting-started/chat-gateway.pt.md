# Executar o chat gateway

O gateway é a cara humana da plataforma: um chat web onde a IA é
conduzida a responder a partir dos dados das ferramentas MCP em vez da
sua própria memória.

Você precisa primeiro do [servidor MCP rodando](mcp-server.md) em modo
HTTP.

```bash
git clone https://github.com/okfn/mcp-chat-gateway
cd mcp-chat-gateway
uv sync
```

Configure o provedor de IA, editando `local_settings.py` ou com
variáveis de ambiente:

| Variável | Exemplo | Significado |
|----------|---------|---------|
| `AI_API_KEY` | `sk-...` | Key do seu provedor de LLM |
| `AI_BASE_URL` | `https://api.deepseek.com` | Qualquer endpoint compatível com OpenAI |
| `AI_MODEL` | `deepseek-chat` | Nome do modelo |
| `MCP_URL` | `http://127.0.0.1:8063` | Onde o servidor MCP vive |

Depois execute:

```bash
uv run python app.py     # serves on http://127.0.0.1:8064
```

Abra `http://127.0.0.1:8064`, escolha uma pergunta sugerida ou digite a
sua, e veja a resposta chegar com suas tabelas, gráficos e links das
fontes.

!!! tip "Ainda sem datasets? Pergunte sobre as ferramentas de exemplo"
    Um servidor recém clonado já serve suas [ferramentas de exemplo
    embutidas](mcp-server.md#what-tools-does-it-serve), então você pode
    testar o ciclo completo antes de instalar qualquer catálogo real:
    pergunte ao chat o que ele consegue responder, chame uma ferramenta
    de exemplo através dele, e confira que a resposta volta com suas
    fontes.

!!! note "Descartável por design"
    O gateway é intencionalmente simples: HTML/JS/CSS puros, um backend
    Flask mínimo, sem framework de frontend. Ele existe para testar e
    demonstrar a plataforma; espere que mude rápido.
