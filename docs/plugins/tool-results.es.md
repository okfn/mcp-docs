# Resultados de las herramientas

Cada herramienta de la plataforma devuelve **dos respuestas a la vez**,
para dos lectores distintos:

- `content`: texto legible para humanos. Es lo que lee el **LLM** para
  componer su respuesta. Siempre obligatorio.
- `structuredContent`: un payload JSON. Es lo que lee la **UI** (el
  chat gateway) para renderizar enlaces a fuentes, tablas y gráficos.

!!! important "Solo `content` llega a la IA"
    El gateway le devuelve `content` al modelo, pero renderiza `table`
    y `charts` desde `structuredContent` **directamente en pantalla,
    sin pasarlos por el modelo**. Lo que los usuarios ven es
    exactamente lo que tu herramienta calculó. Pon los números que
    quieres que sean confiables en `structuredContent`.

## Qué va en `structuredContent`

| Campo | Tipo | Obligatorio | Qué hace |
|-------|------|----------|--------------|
| `sources` | lista | sí | Enlaces a los datos originales. Se renderizan como enlaces a fuentes debajo de la respuesta. |
| `table` | lista de filas | no | Datos tabulares (la primera fila es el encabezado). Se renderiza como una tabla HTML. |
| `charts` | lista | no | Datos y configuración de Chart.js. Se renderizan como gráficos. (En desarrollo.) |
| `force` | string | no | Texto que se muestra al usuario tal cual, sin pasar por el LLM en absoluto. |

## Ejemplo con una tabla

```python
from mcp.types import CallToolResult, TextContent
from mcp_server import DataToolOutput

@registry.tool()
def list_cities() -> DataToolOutput:
    """Return the top 3 cities by population."""
    return CallToolResult(
        content=[TextContent(type="text", text=(
            "The 3 most populated cities are Tokyo (37,400,068), "
            "Delhi (30,290,936) and Shanghai (27,058,479)."
        ))],
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

Nota que `content` repite los datos. Es deliberado: el modelo escribe
su prosa solo a partir de `content`.

## Cómo se hace cumplir

La anotación `-> DataToolOutput` ata el valor de retorno a un esquema
(un `ValidationModel` de Pydantic) publicado como
[structured output](https://github.com/modelcontextprotocol/python-sdk?tab=readme-ov-file#structured-output).
Al arrancar, `@registry.tool()` inspecciona la anotación de retorno de
cada función. Si no es `DataToolOutput`, el servidor registra una
advertencia y **devuelve la función sin registrarla**. La herramienta
no aparece en `tools/list`, así que ningún cliente puede llamarla y el
LLM nunca se entera de que existe.

!!! info "Esto es más estricto de lo que exige MCP"
    El Model Context Protocol no tiene el concepto de una fuente
    obligatoria. Una herramienta MCP perfectamente conforme puede
    devolver una respuesta salida de la nada. Nosotros estrechamos el
    estándar a propósito: en este servidor, declarar de dónde salieron
    los datos es una condición para siquiera quedar registrada.

    Nuestras herramientas siguen siendo compatibles: cualquier cliente
    MCP puede llamarlas, solo que recibe un payload más rico, con
    fuentes incluidas, de lo que el protocolo garantiza.
