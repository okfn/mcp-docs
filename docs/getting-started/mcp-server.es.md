# Ejecutar el servidor MCP

Clona y ejecuta:

```bash
git clone https://github.com/okfn/mcp-server
cd mcp-server
uv sync          # install dependencies
uv run pytest    # optional: run the tests
uv run mcp-server
```

Por defecto el servidor habla **stdio**, que es lo que esperan los
clientes MCP de escritorio (como Claude Desktop). Para un servidor en
red, usa HTTP:

```bash
MCP_TRANSPORT=http uv run mcp-server
```

El servidor HTTP escucha en `http://127.0.0.1:8063` por defecto.

## Configuración

La configuración vive en `settings.py` y cada valor puede sobrescribirse
con una variable de entorno o un archivo `local_settings.py`:

| Configuración | Por defecto | Significado |
|---------|---------|---------|
| `MCP_TRANSPORT` | `stdio` | `stdio` para clientes locales, `http` para la red |
| `MCP_HOST` | `127.0.0.1` | Dirección de escucha en modo HTTP |
| `MCP_PORT` | `8063` | Puerto en modo HTTP |

## ¿Qué herramientas sirve? {#what-tools-does-it-serve}

De fábrica, el servidor carga sus propias herramientas de ejemplo
incluidas. La parte interesante es agregar plugins con datasets reales:
mira [conectar un plugin](../plugins/connect.md) para instalar los
catálogos de Uruguay o Brasil, o escribe el tuyo.
