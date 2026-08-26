# ¿Por qué MCP? Un modelo abierto para datos públicos

El [Model Context Protocol](https://modelcontextprotocol.io/) (MCP) es
un estándar abierto, presentado por Anthropic a fines de 2024 y
adoptado desde entonces en toda la industria de la IA, que define cómo
las aplicaciones de IA se conectan a datos y herramientas externos. Un
**cliente** MCP (una interfaz de chat, un IDE, un asistente de
escritorio) habla con un **servidor** MCP, que expone **herramientas**
que el modelo puede invocar, **recursos** que el cliente puede leer, y
**prompts**, sobre dos transportes estándar: stdio (local) y HTTP
(red). La especificación y los SDK se mantienen de forma abierta en
[modelcontextprotocol.io](https://modelcontextprotocol.io/).

Esta plataforma es una aplicación directa del estándar: los datasets se
exponen como herramientas y recursos MCP, el servidor habla ambos
transportes, y cualquier cliente compatible con MCP (Claude Desktop,
VS Code, MCP Inspector, nuestro chat gateway) puede conectarse sin
cambios. Mira la página de [arquitectura](../dev/architecture.md) para
ver cómo las llamadas del protocolo encajan en el ciclo de ejecución, y
dónde somos más estrictos que el estándar (el contrato de fuentes).

## Por qué lo elegimos

- **Estandarización y diseño plug-and-play.** Las buenas prácticas
  están incorporadas en la arquitectura del servidor; las nuevas
  fuentes de datos se conectan a partir de plantillas sin reconstruir
  la interfaz de IA.
- **Marco abierto y replicable.** Completamente de código abierto,
  protocolo incluido: sin dependencia de un proveedor, sin "caja
  negra".
- **Autonomía local probada.** Durante los pilotos, técnicos de los
  socios construyeron un servidor MCP sobre una nueva fuente de datos
  sin que nadie se lo pidiera.
- **Un kit de herramientas reutilizable en crecimiento.** Un nuevo
  asistente de datos parte de una plantilla en lugar de partir de cero,
  más fácil de adoptar para equipos técnicos con menos experiencia.
