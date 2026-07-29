# Executar o servidor MCP

Clone e execute:

```bash
git clone https://github.com/okfn/mcp-server
cd mcp-server
uv sync          # install dependencies
uv run pytest    # optional: run the tests
uv run mcp-server
```

Por padrão o servidor fala **stdio**, que é o que os clientes MCP de
desktop (como o Claude Desktop) esperam. Para um servidor em rede, use
HTTP:

```bash
MCP_TRANSPORT=http uv run mcp-server
```

O servidor HTTP escuta em `http://127.0.0.1:8063` por padrão.

## Configurações

As configurações vivem em `settings.py` e cada uma delas pode ser
sobrescrita com uma variável de ambiente ou um arquivo
`local_settings.py`:

| Configuração | Padrão | Significado |
|---------|---------|---------|
| `MCP_TRANSPORT` | `stdio` | `stdio` para clientes locais, `http` para a rede |
| `MCP_HOST` | `127.0.0.1` | Endereço de escuta no modo HTTP |
| `MCP_PORT` | `8063` | Porta no modo HTTP |

## Quais ferramentas ele serve?

De fábrica, o servidor carrega suas próprias ferramentas de exemplo
embutidas. A parte interessante é adicionar plugins com datasets reais:
veja [conectar um plugin](../plugins/connect.md) para instalar os
catálogos do Uruguai ou do Brasil, ou escreva o seu próprio.
