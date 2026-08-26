# Ejecutar el chat gateway

El gateway es la cara humana de la plataforma: un chat web donde la IA
es guiada a responder desde los datos de las herramientas MCP en lugar
de su propia memoria.

Primero necesitas el [servidor MCP corriendo](mcp-server.md) en modo
HTTP.

```bash
git clone https://github.com/okfn/mcp-chat-gateway
cd mcp-chat-gateway
uv sync
```

Configura el proveedor de IA, ya sea editando `local_settings.py` o con
variables de entorno:

| Variable | Ejemplo | Significado |
|----------|---------|---------|
| `AI_API_KEY` | `sk-...` | Key de tu proveedor de LLM |
| `AI_BASE_URL` | `https://api.deepseek.com` | Cualquier endpoint compatible con OpenAI |
| `AI_MODEL` | `deepseek-chat` | Nombre del modelo |
| `MCP_URL` | `http://127.0.0.1:8063` | Dónde vive el servidor MCP |

Luego ejecútalo:

```bash
uv run python app.py     # serves on http://127.0.0.1:8064
```

Abre `http://127.0.0.1:8064`, elige una pregunta sugerida o escribe la
tuya, y mira llegar la respuesta con sus tablas, gráficos y enlaces a
las fuentes.

!!! tip "¿Todavía sin datasets? Pregunta por las herramientas de ejemplo"
    Un servidor recién clonado ya sirve sus [herramientas de ejemplo
    incluidas](mcp-server.md#what-tools-does-it-serve), así que puedes
    probar el ciclo completo antes de instalar ningún catálogo real:
    pregúntale al chat qué puede responder, llama una herramienta de
    ejemplo a través de él, y comprueba que la respuesta llega con sus
    fuentes.

!!! note "Descartable por diseño"
    El gateway es intencionalmente simple: HTML/JS/CSS planos, un
    backend Flask mínimo, sin framework de frontend. Existe para probar
    y demostrar la plataforma; espera que cambie rápido.
