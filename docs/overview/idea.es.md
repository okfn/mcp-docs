# La idea

Los gobiernos y las organizaciones publican enormes cantidades de datos
abiertos: presupuestos, compras públicas, precios, estadísticas de
salud. Muy poca gente los usa, porque usarlos requiere descargar
archivos, entender esquemas y escribir código.

Al mismo tiempo, la gente ya les hace estas preguntas a los chatbots de
IA, y los chatbots responden de memoria: desactualizados, no
verificables, a veces inventados.

## Nuestra respuesta

Ponemos una capa entre la IA y el usuario:

1. El usuario hace una pregunta en su propio idioma.
2. En lugar de responder de memoria, la IA es guiada a llamar a una
   **herramienta**: una operación pequeña y con nombre, como "precio
   promedio de un producto por año", respaldada por un dataset real.
3. La herramienta calcula la respuesta a partir de los datos y la
   devuelve junto con la **fuente**: un enlace al dataset original.
4. El chat muestra la respuesta escrita por la IA, más tablas, gráficos
   y las fuentes, para que cualquiera pueda verificarla.

!!! important "Las tablas y los gráficos vienen del código, no de la IA"
    Una herramienta devuelve dos cosas: un texto corto para que la IA
    lo lea, y una carga estructurada (tablas, gráficos, fuentes) para
    la interfaz. Solo el texto llega al modelo. **Las tablas y los
    gráficos los construyen funciones de herramienta escritas por
    humanos y los muestra directamente la interfaz, sin pasar en ningún
    momento por la IA.** La IA escribe la prosa; los datos hablan por
    sí mismos a su lado.

Las tablas verificables y los enlaces a las fuentes junto a sus
palabras no son un extra agradable; son la salvaguarda. Ver [lecciones
de los pilotos](../lessons/index.md).

El razonamiento más profundo de por qué un LLM solo no alcanza está en
la página de [el desafío](challenges.md).

## Principios

- **Precisión y trazabilidad.** Las respuestas deben ser correctas,
  calculadas a partir de los datos, y cada respuesta debe apuntar a su
  fuente. El servidor [lo exige en el
  código](../plugins/tool-results.md#como-se-hace-cumplir).
- **Código simple antes que un lenguaje a medida.** Las herramientas
  son en su mayoría pequeñas funciones de Python. Los datasets
  realmente simples pueden en cambio declararse en YAML sin código,
  pero reservamos eso para los casos simples: ver [el compromiso del
  YAML](../lessons/yaml-tradeoff.md).
- **Software libre, tecnología aburrida.** Python, CSV, SQLite, HTML y
  JS planos. Todo puede correr en una laptop.
- **Propiedad local.** Cada comunidad o equipo de dominio mantiene su
  propio repo de plugin, en su propio idioma, a su propio ritmo.

## El estándar por debajo

La conexión entre la IA y las herramientas usa el
[Model Context Protocol](https://modelcontextprotocol.io/) (MCP), un
estándar abierto. Eso significa que nuestro servidor funciona no solo
con nuestro chat gateway sino con cualquier cliente compatible con MCP
(Claude Desktop, VS Code, MCP Inspector y otros).
