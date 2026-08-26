# Ferramentas em Python

Quando o YAML não é suficiente (um banco de dados SQLite, uma API
externa, um cálculo), escreva uma função Python comum.

## Um pacote de plugin mínimo

```bash
uv init --package mcp-exampleplugin
cd mcp-exampleplugin
uv add https://github.com/okfn/mcp-server.git
```

Defina uma função `register_tools(registry)`:

```python
from mcp.types import CallToolResult, TextContent
from mcp_server import DataToolOutput

def register_tools(registry):

    @registry.tool()
    def greetings_from_example() -> DataToolOutput:
        """Return a greetings message to the user."""
        source = "https://example.org/link/to/data"
        return CallToolResult(
            content=[TextContent(type="text", text="Hello from an example plugin!")],
            structuredContent={"sources": [source]},
        )
```

Depois declare o entry point no `pyproject.toml`, que é como o servidor
descobre seu plugin na inicialização:

```toml
[project.entry-points.mcp_server]
mcp-exampleplugin = "mcp_exampleplugin:register_tools"
```

Execute o servidor de dentro da pasta do seu pacote e teste com o
[Inspector](../getting-started/inspector.md):

```bash
MCP_TRANSPORT=http uv run mcp-server
```

## Duas regras para lembrar

1. A função **deve** ser anotada com `-> DataToolOutput`. Ferramentas
   sem essa anotação são ignoradas na inicialização, com um aviso. É
   assim que o servidor faz valer o
   [contrato de resultados](tool-results.md).
2. O docstring importa: é a descrição que a IA lê para decidir quando
   chamar sua ferramenta. Escreva-o para a IA, no idioma em que seus
   usuários vão fazer as perguntas.

## Pré-calcule os valores derivados, não peça à IA {#precompute-derived-values-do-not-ask-the-ai-to}

Consultas diretas ("qual foi o valor X no ano Y?") são confiáveis.
Cálculos derivados não: porcentagens, parcelas e variações ano a ano
foram a única área onde os testadores dos pilotos relataram respostas
numericamente erradas mas apresentadas como dados. O modelo não tem
nenhuma garantia de acertar a aritmética, e um percentual errado em uma
tabela arrumada parece totalmente convincente.

A correção confiável é não pedir para o modelo fazer as contas.
Pré-calcule o valor derivado com pandas para que ele vire uma coluna
real e documentada, e deixe a ferramenta apenas lê-la:

- **Casos simples** (um percentual direto de um dataset): adicione o
  percentual como uma coluna nova com pandas, e documente o que
  significa.
- **Casos complexos** (um percentual que cruza várias colunas ou
  datasets): pré-calcule o percentual que as pessoas realmente
  costumam perguntar, por exemplo "qual parcela foi renovável no
  ano X?".
- **Casos difíceis e muito específicos** ("quanto X cresceu entre o ano
  Y1 e o ano Y2?"): específicos demais para pré-calcular para cada par.
  Uma ferramenta que atue como uma pequena calculadora pode ajudar
  aqui; ainda não testamos isso.

Trate qualquer percentual ou variação calculada na hora como suspeita
até que uma ferramenta a compute a partir de uma coluna documentada. Se
um número importa, ele deve vir dos dados, não da cabeça do modelo.

## Menos código repetitivo

`CallToolResult` fica verboso. Para casos simples o servidor oferece
helpers:

```python
from mcp_server.results import text_result

@registry.tool()
def hello_world() -> DataToolOutput:
    """Return a hello world value."""
    return text_result("Hello world!", source="https://example.org/data")
```
