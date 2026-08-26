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

## Precalcula los valores derivados, no se los pidas a la IA {#precompute-derived-values-do-not-ask-the-ai-to}

Las consultas directas ("¿cuál fue el valor X en el año Y?") son
confiables. Los cálculos derivados no: los porcentajes, proporciones y
variaciones interanuales fueron la única área donde los testers de los
pilotos reportaron respuestas numéricamente incorrectas pero
presentadas como datos. El modelo no tiene ninguna garantía de hacer
bien la aritmética, y un porcentaje equivocado en una tabla prolija se
ve completamente convincente.

La solución confiable es no pedirle al modelo que haga las cuentas.
Precalcula el valor derivado con pandas para que se convierta en una
columna real y documentada, y deja que la herramienta simplemente la
lea:

- **Casos simples** (un porcentaje directo de un dataset): agrega el
  porcentaje como una columna nueva con pandas, y documenta qué
  significa.
- **Casos complejos** (un porcentaje que cruza varias columnas o
  datasets): precalcula el porcentaje que la gente realmente tiende a
  preguntar, por ejemplo "¿qué proporción fue renovable en el año X?".
- **Casos difíciles y muy específicos** ("¿cuánto creció X entre el
  año Y1 y el año Y2?"): demasiado específicos para precalcularlos para
  cada par. Una herramienta que actúe como una pequeña calculadora
  podría ayudar aquí; todavía no lo hemos probado.

Trata cualquier porcentaje o variación calculada al vuelo como
sospechosa hasta que una herramienta la compute desde una columna
documentada. Si un número importa, debe venir de los datos, no de la
cabeza del modelo.

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
