# Datasets en YAML

Algunos datasets son solo un archivo CSV y un puñado de preguntas
obvias: "¿cuál es el total por año?", "¿cuáles son los 10 primeros?",
"lista las filas de mi ciudad". Para esos, puedes saltarte el código:
describe el dataset en un archivo YAML y elige un **engine**.

!!! warning "Solo para datasets realmente simples"
    En el momento en que un dataset necesita algo a medida, el YAML
    deja de alcanzar y te conviene una [herramienta en
    Python](python-tools.md). Lee [cuándo usar YAML vs.
    Python](#when-to-use-yaml-vs-python) antes de apoyarte en él.
    Siempre preferimos Python sobre YAML.

## Los engines

| Engine | Responde preguntas como |
|--------|------------------------|
| `aggregate` | "¿Cuál es el total / promedio / conteo de X?" (opcionalmente agrupado) |
| `row_list` | "Lista las filas que cumplen mis filtros, ordenadas por X" |
| `top_row` | "¿Qué fila tiene el X más alto / más bajo?" |
| `unique_values` | "¿Qué valores distintos existen en esta columna?" |

## Anatomía de un archivo de dataset

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

Cada `filter` se convierte en un parámetro que la IA puede completar al
llamar a la herramienta. Los tipos de filtro incluyen `str` (sin
distinguir mayúsculas), `int`, `float` e `int_range` (que genera los
parámetros `_from` / `_to`).

Un bloque opcional `visualization` (con `group_by` y un `type` de
gráfico `bar`, `line` o `pie`) hace que la herramienta devuelva un
gráfico junto con la respuesta.

## Dónde viven los archivos

Pon cada dataset en su propio archivo `.yaml` dentro de la carpeta
`datasets/` del plugin. Un archivo, un dataset: los archivos pequeños
son más fáciles de revisar y nunca entran en conflicto entre sí.

Los engines en sí viven en el
[repo mcp-server](https://github.com/okfn/mcp-server/tree/main/src/mcp_server/engines),
que es la referencia si necesitas la lista completa de opciones.

## Cuándo usar YAML vs. Python {#when-to-use-yaml-vs-python}

Declarar datasets en YAML funciona bien para casos básicos, pero el
YAML declarativo puede convertirse fácilmente en un lenguaje de
consulta a medida si se lo estira demasiado. Cada nuevo tipo de filtro,
join o columna calculada requiere expandir el engine que interpreta el
YAML, y después tiene que ser aprendido por quien escriba el YAML. La
aparente simplicidad se mueve en lugar de desaparecer.

Regla práctica:

- **Usa YAML** para archivos CSV genuinamente simples con preguntas
  estándar de agregación o top-N.
- **Usa Python** en cuanto un dataset requiera cálculos a medida,
  transformaciones de fechas, joins entre varias tablas o lógica de
  filtrado compleja. Escribir unas pocas líneas de [código
  Python](python-tools.md) estándar es más claro y más fácil de
  mantener que extender reglas YAML a medida.

Nada de esto hace que el YAML esté mal. Lo hace una herramienta afilada
para un trabajo acotado: úsalo para los casos simples, y no intentes
hacerlo crecer hasta un lenguaje de consulta general, porque ese es un
lenguaje que después tendrías que mantener.
