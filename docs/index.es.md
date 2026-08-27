# Documentación técnica de MCP

Bienvenido a la documentación técnica de MCP: una guía práctica para
conectar datos públicos abiertos a modelos de IA usando el Model
Context Protocol (MCP).

Este manual proporciona las especificaciones de arquitectura, los
patrones de código y las plantillas de configuración necesarias para
construir plugins, ejecutar el servidor y desplegar herramientas de
datos.

Todo lo que hay aquí se mide contra dos objetivos: **precisión**
(respuestas calculadas a partir de datos oficiales, no recordadas del
entrenamiento) y **trazabilidad** (cada respuesta enlaza de vuelta a su
fuente). El [contexto del proyecto](introduction/context.md) explica
ambos y por qué importan para los datos públicos.

**¿Buscas contexto no técnico o la estrategia del proyecto?** Consulta
la *Field Guide to Connecting AI to Public Information* (guía de campo
para conectar la IA a la información pública). Cubre lecciones de
nuestros pilotos de Brasil y Uruguay, orientación para trabajar con
expertos de dominio y feedback de usuarios reales. El enlace a la
Field Guide se compartirá pronto.

Para más información, visita la página oficial del proyecto
"Traceable AI Answers for Public Data" en el
[sitio web de la Open Knowledge Foundation (OKFN)](https://okfn.org/en/projects/ai-learning-labs/mcp-open-government-data/).

## Qué hay en la caja

- Un **servidor MCP** que convierte datasets abiertos (archivos CSV,
  bases de datos) en herramientas que una IA puede llamar.
- Un **chat gateway**, un chat web simple que conecta cualquier LLM
  compatible con OpenAI al servidor MCP y muestra tablas, gráficos y
  enlaces a las fuentes directamente desde los datos, [sin pasarlos por
  la IA](dev/architecture.md).
- **Plugins** acotados a un dominio de datos específico (el balance
  energético de Uruguay, Brasil, y el tuyo después) que describen
  datasets y las preguntas que pueden responder.

## Adónde ir ahora

- ¿Recién llegas? Empieza por el [contexto del proyecto](introduction/context.md).
- ¿Quieres ejecutarlo? Ve a [primeros pasos](getting-started/index.md).
- ¿Quieres agregar los datos de tu país? Lee [plugins](plugins/index.md).

!!! note "Etapa temprana"
    Toda la plataforma está en una fase temprana de investigación. Se
    esperan cambios incompatibles, y también que esta documentación
    cambie bajo tus pies.
