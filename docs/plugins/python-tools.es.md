# Herramientas en Python

Cuando el YAML no alcanza (una base de datos SQLite, una API externa,
un cálculo), escribe una función de Python común.

## Un paquete de plugin mínimo

```bash
uv init --package mcp-exampleplugin
cd mcp-exampleplugin
uv add https://github.com/okfn/mcp-server.git
```

Define una función `register_tools(registry)`:

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

Luego declara el entry point en `pyproject.toml`, que es la forma en
que el servidor descubre tu plugin al arrancar:

```toml
[project.entry-points.mcp_server]
mcp-exampleplugin = "mcp_exampleplugin:register_tools"
```

Ejecuta el servidor desde dentro de la carpeta de tu paquete y prueba
con el [Inspector](../getting-started/inspector.md):

```bash
MCP_TRANSPORT=http uv run mcp-server
```

## Dos reglas para recordar

1. La función **debe** estar anotada con `-> DataToolOutput`. Las
   herramientas sin esa anotación se omiten al arrancar, con una
   advertencia. Así es como el servidor hace cumplir el
   [contrato de resultados](tool-results.md).
2. El docstring importa: es la descripción que la IA lee para decidir
   cuándo llamar a tu herramienta. Escríbelo para la IA, en el idioma
   en que tus usuarios harán las preguntas.

## Precalcula los valores derivados, no se los pidas a la IA

El modelo es poco confiable en aritmética como porcentajes y
variaciones interanuales. Precalcúlalos con pandas como columnas
reales y documentadas y deja que la herramienta las lea: mira
[confiabilidad de los cálculos](../lessons/calculations.md).

## Menos código repetitivo

`CallToolResult` se vuelve verboso. Para los casos simples el servidor
ofrece helpers:

```python
from mcp_server.results import text_result

@registry.tool()
def hello_world() -> DataToolOutput:
    """Return a hello world value."""
    return text_result("Hello world!", source="https://example.org/data")
```
