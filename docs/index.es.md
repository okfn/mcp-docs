# Plataforma MCP de OKFN

**Responder preguntas con datos abiertos, no con conjeturas de la IA.**

Esta es la documentación de la plataforma MCP de OKFN: una pequeña
familia de proyectos de software libre que permiten que las personas
hagan preguntas en lenguaje corriente (inglés, español, portugués...) y
obtengan respuestas calculadas a partir de fuentes oficiales de datos
abiertos, con cada respuesta enlazando a los datos originales.

Esa oración contiene los dos objetivos del proyecto: respuestas
calculadas a partir de los datos, lo que llamamos **precisión**, y
respuestas que enlazan a su fuente, lo que llamamos **trazabilidad**.
[El modelo abierto](overview/open-model.md) explica ambos.

Se construye como parte de los
[AI Learning Labs](https://okfn.org/en/projects/ai-learning-labs/mcp-open-government-data/)
de la Open Knowledge Foundation.

## Mira la charla

Presentamos este trabajo como *IA Trazable para datos publicos: un
modelo abierto para America Latina* en el UN Big Data Regional Hub en
Brasil, organizado por la CEPAL, en junio de 2026, a cargo de Patricio
Del Boca (líder técnico) y Andres Vazquez (desarrollador senior).

<div class="video">
  <iframe src="https://www.youtube-nocookie.com/embed/9QBr7kWAcdI"
          title="IA Trazable para datos publicos: un modelo abierto para America Latina"
          style="width: 100%; aspect-ratio: 16 / 9; border: 0;"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
          allowfullscreen></iframe>
</div>

La charla cubre el desafío central (por qué no se puede confiar en los
LLM por sí solos con datos públicos), el modelo abierto detrás de
nuestra respuesta, una demo en vivo del caso de Uruguay y lo que
aprendimos. Esta documentación es la versión escrita y extendida de esa
misma visión.

La [página del evento de la CEPAL](https://rtc-cea.cepal.org/es/evento/videoconferencia-sobre-ia-trazable-para-datos-publicos-un-modelo-abierto-para-america-latina)
tiene más sobre la sesión, incluyendo un PDF con las diapositivas de la
presentación.

## Por qué

!!! tagline "La idea central"
    Los grandes modelos de lenguaje son excelentes para conversar y
    pésimos con los hechos. Los portales de datos abiertos son
    excelentes con los hechos y pésimos para conversar.

Esta plataforma conecta ambos mundos. **No queremos que la IA sepa la
respuesta, queremos que recupere, explique y cite los datos para la
respuesta.**

No hemos alcanzado plenamente ese objetivo, pero en el camino
construimos algo genuinamente útil, una herramienta que vale la pena
usar con cuidado. Lo que aprendimos intentando llegar está escrito en
[lecciones de los pilotos](lessons/index.md).

## Qué hay en la caja

- Un **servidor MCP** que convierte datasets abiertos (archivos CSV,
  bases de datos) en herramientas que una IA puede llamar.
- Un **chat gateway**, un chat web simple que conecta cualquier LLM
  compatible con OpenAI al servidor MCP y muestra tablas, gráficos y
  enlaces a las fuentes directamente desde los datos, [sin pasarlos por
  la IA](overview/idea.md).
- **Plugins** acotados a un dominio de datos específico (el balance
  energético de Uruguay, Brasil, y el tuyo después) que describen
  datasets y las preguntas que pueden responder.

## Adónde ir ahora

- ¿Recién llegas? Empieza por [la idea](overview/idea.md).
- ¿Quieres ejecutarlo? Ve a [primeros pasos](getting-started/index.md).
- ¿Quieres agregar los datos de tu país? Lee [plugins](plugins/index.md).

!!! note "Etapa temprana"
    Toda la plataforma está en una fase temprana de investigación. Se
    esperan cambios incompatibles, y también que esta documentación
    cambie bajo tus pies.
