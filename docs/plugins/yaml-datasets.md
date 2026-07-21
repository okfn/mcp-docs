# YAML datasets

Some datasets are just a CSV file and a handful of obvious questions:
"what is the total per year?", "which are the top 10?", "list the rows
for my city". For those, you can skip writing code: describe the dataset
in a YAML file and pick an **engine**.

!!! warning "Only for really simple datasets"
    The moment a dataset needs anything custom, YAML stops being enough
    and you are better off with a [Python tool](python-tools.md). Read
    [the YAML trade-off](../lessons/yaml-tradeoff.md) before you lean
    on it.

## The engines

| Engine | Answers questions like |
|--------|------------------------|
| `aggregate` | "What is the total / average / count of X?" (optionally grouped) |
| `row_list` | "List the rows matching my filters, sorted by X" |
| `top_row` | "Which row has the highest / lowest X?" |
| `unique_values` | "Which distinct values exist in this column?" |

## Anatomy of a dataset file

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

Each `filter` becomes a parameter the AI can fill in when calling the
tool. Filter types include `str` (case-insensitive), `int`, `float`
and `int_range` (which generates `_from` / `_to` parameters).

An optional `visualization` block (with `group_by` and a chart `type`
of `bar`, `line` or `pie`) makes the tool return a chart along with
the answer.

## Where files live

Put each dataset in its own `.yaml` file inside the plugin's
`datasets/` folder. One file, one dataset: small files are easier to
review and never conflict with each other.

The engines themselves live in the
[mcp-server repo](https://github.com/okfn/mcp-server/tree/main/src/mcp_server/engines),
which is the reference if you need the full list of options.
