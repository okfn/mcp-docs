# Datasets em YAML

Alguns datasets são só um arquivo CSV e um punhado de perguntas óbvias:
"qual é o total por ano?", "quais são os 10 primeiros?", "liste as
linhas da minha cidade". Para esses, você pode pular a programação:
descreva o dataset em um arquivo YAML e escolha um **engine**.

!!! warning "Só para datasets realmente simples"
    No momento em que um dataset precisa de qualquer coisa
    personalizada, o YAML deixa de ser suficiente e é melhor usar uma
    [ferramenta em Python](python-tools.md). Leia [quando usar YAML vs.
    Python](#when-to-use-yaml-vs-python) antes de se apoiar nele.
    Sempre preferimos Python a YAML.

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

## Quando usar YAML vs. Python {#when-to-use-yaml-vs-python}

Declarar datasets em YAML funciona bem para casos básicos, mas o YAML
declarativo pode facilmente virar uma linguagem de consulta sob medida
se for esticado demais. Cada novo tipo de filtro, join ou coluna
calculada exige expandir o engine que interpreta o YAML, e depois tem
que ser aprendido por quem escreve o YAML. A aparente simplicidade se
move em vez de desaparecer.

Regra prática:

- **Use YAML** para arquivos CSV genuinamente simples com perguntas
  padrão de agregação ou top-N.
- **Use Python** assim que um dataset exigir cálculos personalizados,
  transformações de datas, joins entre várias tabelas ou lógica de
  filtragem complexa. Escrever umas poucas linhas de [código
  Python](python-tools.md) padrão é mais claro e mais fácil de manter
  do que estender regras de YAML sob medida.

Nada disso torna o YAML errado. Torna-o uma ferramenta afiada para um
trabalho estreito: use-o para os casos simples, e não tente fazê-lo
crescer até virar uma linguagem de consulta geral, porque essa é uma
linguagem que você teria então que manter.
