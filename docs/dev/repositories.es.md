# Repositorios

La plataforma es un espacio de trabajo de repos git pequeños e
independientes, en lugar de un gran monorepo. Cada repo tiene sus
propios tests, su propio README y su propio ritmo de releases.

## Núcleo

| Repo | Qué es |
|------|------------|
| [mcp-server](https://github.com/okfn/mcp-server) | El servidor MCP. Carga herramientas desde módulos Python, plugins instalados y archivos YAML, y las sirve por stdio o HTTP. |
| [mcp-chat-gateway](https://github.com/okfn/mcp-chat-gateway) | El chat web. Flask simple + HTML/JS, sin framework de frontend. Conecta un LLM al servidor MCP y muestra tablas, gráficos y fuentes. |

## Plugins de datos

| Repo | Qué es |
|------|------------|
| [mcp-datos-uruguay-ben](https://github.com/okfn/mcp-datos-uruguay-ben) | Herramientas sobre el balance energético nacional de Uruguay (BEN), de catalogodatos.gub.uy. En español. |
| [mcp-dados-brasil](https://github.com/okfn/mcp-dados-brasil) | Datasets del portal de datos abiertos de Brasil (dados.gov.br). En portugués. |

!!! note "mcp-datos-uruguay está retirado"
    El repo original `mcp-datos-uruguay` intentó cubrir todo el portal
    de Uruguay y se volvió demasiado general. Ya no está en uso; el más
    enfocado `mcp-datos-uruguay-ben` lo reemplazó. Mira [por qué
    acotamos los plugins](../lessons/scope.md).

## Piezas opcionales

| Repo | Qué es |
|------|------------|
| mcp-deployment | Configuración de Docker Compose + Caddy usada para correr la instancia pública en mcp.okfn.org. Repo privado: es nuestra propia infraestructura, así que no está disponible públicamente. Si necesitas ayuda para desplegar tu propia instancia, contáctanos. |
| [mcp-docs](https://github.com/okfn/mcp-docs) | Esta documentación. |

!!! tip "¿Qué repo toco?"
    Agregar un dataset para un país existente: el repo del plugin del país.
    Agregar un país nuevo: un repo de plugin nuevo (mira [plugins](../plugins/index.md)).
    Cambiar cómo funcionan las herramientas para todos: `mcp-server`.
