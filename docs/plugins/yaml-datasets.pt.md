# Datasets em YAML

Alguns datasets são só um arquivo CSV e um punhado de perguntas óbvias:
"qual é o total por ano?", "quais são os 10 primeiros?", "liste as
linhas da minha cidade". Para esses, você pode pular a programação:
descreva o dataset em um arquivo YAML e escolha um **engine**.

!!! warning "Só para datasets realmente simples"
    No momento em que um dataset precisa de qualquer coisa
    personalizada, o YAML deixa de ser suficiente e é melhor usar uma
    [ferramenta em Python](python-tools.md). Leia [o trade-off do
    YAML](../lessons/yaml-tradeoff.md) antes de se apoiar nele.

## Os engines

| Engine | Responde perguntas como |
|--------|------------------------|
| `aggregate` | "Qual é o total / média / contagem de X?" (opcionalmente agrupado) |
| `row_list` | "Liste as linhas que atendem aos meus filtros, ordenadas por X" |
| `top_row` | "Qual linha tem o maior / menor X?" |
| `unique_values` | "Quais valores distintos existem nesta coluna?" |

## Anatomia de um arquivo de dataset

```yaml
engine: aggregate
dataset:
  name: fuel-prices
  source:
    csv: https://example.org/data/fuel-prices.csv
tool:
  name: average_fuel_price
  description: "Average fuel price, optionally filtered by year and fuel type"
  column: PRICE
filters:
  - column: YEAR
    param: year
    type: int
    description: "Year to filter by"
  - column: FUEL_TYPE
    param: fuel_type
    type: str
    description: "Type of fuel (e.g. gasoline, diesel)"
response: "The average price {filter_label} is {result}. Source: {source}"
```

Cada `filter` vira um parâmetro que a IA pode preencher ao chamar a
ferramenta. Os tipos de filtro incluem `str` (sem diferenciar
maiúsculas), `int`, `float` e `int_range` (que gera os parâmetros
`_from` / `_to`).

Um bloco opcional `visualization` (com `group_by` e um `type` de
gráfico `bar`, `line` ou `pie`) faz a ferramenta retornar um gráfico
junto com a resposta.

## Onde os arquivos ficam

Coloque cada dataset em seu próprio arquivo `.yaml` dentro da pasta
`datasets/` do plugin. Um arquivo, um dataset: arquivos pequenos são
mais fáceis de revisar e nunca entram em conflito entre si.

Os engines em si vivem no
[repo mcp-server](https://github.com/okfn/mcp-server/tree/main/src/mcp_server/engines),
que é a referência se você precisar da lista completa de opções.
