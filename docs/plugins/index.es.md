# Construir plugins y datasets

Un plugin es un repo git que le enseña al servidor MCP sobre un
conjunto de datasets. Acotamos cada plugin a un **dominio de datos
enfocado** (por ejemplo el balance energético de Uruguay) en lugar de a
todo un portal de datos abiertos, que tiende a volverse demasiado
general. Los catálogos de energía de Uruguay y de Brasil son plugins;
el tuyo también puede serlo.

Un plugin puede describir sus herramientas de dos maneras, y mezclar
ambas libremente:

- [**Herramientas en Python**](python-tools.md): funciones de Python
  comunes. Este es el camino principal, y al que recurrimos en la
  práctica: cubre desde una consulta simple hasta bases de datos, APIs
  y cálculos, y se mantiene claro a medida que un dataset crece.
- [**Datasets en YAML**](yaml-datasets.md): declara una consulta en un
  pequeño archivo `.yaml`, sin necesidad de programar. Solo para
  datasets realmente simples: mira [cuándo usar YAML vs.
  Python](yaml-datasets.md#when-to-use-yaml-vs-python).

Preferimos funciones de Python como herramientas para empezar.
Sea cual sea el estilo, toda herramienta debe seguir el mismo
[contrato de resultados](tool-results.md): una respuesta en texto para
la IA más datos estructurados (fuentes, tablas, gráficos) para la UI.

## El camino hacia tu propio plugin

1. Parte de los catálogos existentes como plantillas:
   [el plugin de energía de Uruguay](../catalogs/uruguay.md) (Python).
2. Escribe tu primera herramienta como una [función de
   Python](python-tools.md).
3. Pruébala localmente con [MCP Inspector](../getting-started/inspector.md).
4. [Dale a tu plugin una descripción y preguntas de
   ejemplo](plugin-info.md) para que el chat muestre una linda tarjeta
   de presentación.
5. [Conéctalo a un servidor](connect.md).

!!! tip "Dos lecciones de los pilotos"
    Dos prácticas resultaron especialmente valiosas al construir un
    plugin: [precalcular los valores derivados en lugar de pedírselos a
    la IA](python-tools.md#precompute-derived-values-do-not-ask-the-ai-to),
    y [darle a la IA un glosario de dominio](glossaries.md) inyectando
    definiciones oficiales en el contexto de tus herramientas.
