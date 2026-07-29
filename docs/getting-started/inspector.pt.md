# Testar com o MCP Inspector

O [MCP Inspector](https://github.com/modelcontextprotocol/inspector) é a
interface oficial de depuração para servidores MCP. Ele permite navegar
pelas ferramentas e chamá-las na mão, sem nenhum modelo de IA no meio. É
a forma mais rápida de conferir que uma ferramenta faz o que você acha
que ela faz.

Com o servidor rodando em modo HTTP (veja
[executar o servidor MCP](mcp-server.md)):

```bash
npx @modelcontextprotocol/inspector
```

Depois, na página web do Inspector que se abre:

1. Escolha o tipo de transporte **Streamable HTTP**.
2. Conecte-se a `http://127.0.0.1:8063` (nota: sem o sufixo `/mcp`).
3. Liste as ferramentas, escolha uma, preencha seus parâmetros e
   execute.

Você também pode deixar o Inspector iniciar o servidor por conta própria
sobre stdio:

```bash
npx @modelcontextprotocol/inspector uv run mcp-server
```

!!! tip
    Quando uma ferramenta que você esperava não aparece na lista,
    verifique os logs do servidor na inicialização: ferramentas que não
    seguem o [contrato de resultados](../plugins/tool-results.md) são
    puladas com um aviso, não com um erro.
