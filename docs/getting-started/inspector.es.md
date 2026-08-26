# Probar con MCP Inspector

**Este paso es opcional.** Puedes saltar directo a [ejecutar el chat
gateway](chat-gateway.md); el Inspector es solo la forma más rápida de
comprobar que el servidor y sus herramientas funcionan, sin IA
involucrada.

[MCP Inspector](https://github.com/modelcontextprotocol/inspector) es la
interfaz oficial de depuración para servidores MCP. Te permite explorar
las herramientas y llamarlas a mano, sin ningún modelo de IA en el
medio, y comprobar que una herramienta hace lo que crees que hace.

Con el servidor corriendo en modo HTTP (mira
[ejecutar el servidor MCP](mcp-server.md)):

```bash
npx @modelcontextprotocol/inspector
```

Luego, en la página web del Inspector que se abre:

1. Elige el tipo de transporte **Streamable HTTP**.
2. Conéctate a `http://127.0.0.1:8063` (nota: sin sufijo `/mcp`).
3. Lista las herramientas, elige una, completa sus parámetros y
   ejecútala.

También puedes dejar que el Inspector lance el servidor por sí mismo
sobre stdio:

```bash
npx @modelcontextprotocol/inspector uv run mcp-server
```

!!! tip
    Cuando una herramienta que esperabas no aparece en la lista, revisa
    los logs del servidor al arranque: las herramientas que no siguen el
    [contrato de resultados](../plugins/tool-results.md) se omiten con
    una advertencia, no con un error.
