# YAML datasets

Some datasets are just a CSV file and a handful of obvious questions:
"what is the total per year?", "which are the top 10?", "list the rows
for my city". For those, you can skip writing code: describe the dataset
in a YAML file and pick an **engine**.

!!! warning "Only for really simple datasets"
    The moment a dataset needs anything custom, YAML stops being enough
    and you are better off with a [Python tool](python-tools.md). Read
    [when to use YAML vs. Python](#when-to-use-yaml-vs-python) before
    you lean on it. We always prefer python over YAML.

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

## When to use YAML vs. Python

Declaring datasets in YAML works well for basic cases, but declarative
YAML can easily turn into a bespoke query language if stretched too
far. Every new filter type, join or calculated column requires
expanding the YAML parser engine, and then has to be learned by whoever
writes the YAML. The apparent simplicity moves rather than disappears.

Rule of thumb:

- **Use YAML** for genuinely simple CSV files with standard aggregation
  or top-N questions.
- **Use Python** as soon as a dataset requires custom calculations,
  date transformations, multi-table joins or complex filtering logic.
  Writing a few lines of standard [Python code](python-tools.md) is
  clearer and easier to maintain than extending custom YAML rules.

None of this makes YAML wrong. It makes it a sharp tool for a narrow
job: use it for the simple cases, and do not try to grow it into a
general query language, because that is a language you would then have
to maintain.
