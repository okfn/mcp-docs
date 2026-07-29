# Resultados das ferramentas

Cada ferramenta da plataforma retorna **duas respostas ao mesmo tempo**,
para dois leitores diferentes:

- `content`: texto legível para humanos. É o que o **LLM** lê para
  compor sua resposta. Sempre obrigatório.
- `structuredContent`: um payload JSON. É o que a **UI** (o chat
  gateway) lê para renderizar links de fontes, tabelas e gráficos.

!!! important "Só `content` chega à IA"
    O gateway devolve `content` ao modelo, mas renderiza `table` e
    `charts` a partir de `structuredContent` **diretamente na tela,
    sem passá-los pelo modelo**. O que os usuários veem é exatamente o
    que sua ferramenta calculou. Coloque os números que você quer que
    sejam confiáveis em `structuredContent`.

## O que vai em `structuredContent`

| Campo | Tipo | Obrigatório | O que faz |
|-------|------|----------|--------------|
| `sources` | lista | sim | Links para os dados originais. Renderizados como links de fontes abaixo da resposta. |
| `table` | lista de linhas | não | Dados tabulares (a primeira linha é o cabeçalho). Renderizada como uma tabela HTML. |
| `charts` | lista | não | Dados e configuração do Chart.js. Renderizados como gráficos. (Em desenvolvimento.) |
| `force` | string | não | Texto mostrado ao usuário exatamente como está, sem passar pelo LLM. |

## Exemplo com uma tabela

```python
from mcp.types import CallToolResult, TextContent
from mcp_server import DataToolOutput

@registry.tool()
def list_cities() -> DataToolOutput:
    """Return the top 3 cities by population."""
    return CallToolResult(
        content=[TextContent(type="text", text="Found 3 cities sorted by population.")],
        structuredContent={
            "sources": ["https://example.org/cities-data"],
            "table": [
                ["City", "Population"],
                ["Tokyo", "37400068"],
                ["Delhi", "30290936"],
                ["Shanghai", "27058479"],
            ],
        },
    )
```

## Como isso é garantido

A anotação `-> DataToolOutput` amarra o valor de retorno a um esquema
(um `ValidationModel` do Pydantic) publicado como
[structured output](https://github.com/modelcontextprotocol/python-sdk?tab=readme-ov-file#structured-output).
Na inicialização, `@registry.tool()` inspeciona a anotação de retorno
de cada função. Se não for `DataToolOutput`, o servidor registra um
aviso e **devolve a função sem registrá-la**. A ferramenta não aparece
em `tools/list`, então nenhum cliente pode chamá-la e o LLM nunca fica
sabendo que ela existe.

!!! info "Isso é mais rígido do que o MCP exige"
    O Model Context Protocol não tem o conceito de fonte obrigatória.
    Uma ferramenta MCP perfeitamente conforme pode retornar uma
    resposta vinda do nada. Nós estreitamos o padrão de propósito:
    neste servidor, declarar de onde os dados vieram é condição para
    sequer ser registrada.

    Nossas ferramentas continuam compatíveis: qualquer cliente MCP
    pode chamá-las, ele só recebe um payload mais rico, com fontes
    incluídas, do que o protocolo garante.
