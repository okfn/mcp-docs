# Brasil

**Repo:** [okfn/mcp-dados-brasil](https://github.com/okfn/mcp-dados-brasil)
&middot; **Portal:** [dados.gov.br](https://dados.gov.br)
&middot; **Idioma:** portugués

Definiciones de datasets para el portal nacional de datos abiertos de
Brasil. Cada archivo `.yaml` bajo `datasets/` declara un dataset y sus
herramientas; el repo también contiene herramientas en Python para los
casos más elaborados.

## Desde el terreno

Este catálogo respaldó un piloto con la Contraloría General de la Unión
de Brasil, enfocado en las **enmiendas parlamentarias**, uno de los
datasets más solicitados del portal. El objetivo era probar si la
ciudadanía podía preguntar en lenguaje natural y obtener respuestas
trazables hasta los datos oficiales. Ver [lecciones de los
pilotos](../lessons/index.md).

## Agregar un dataset

Sigue la guía general de [datasets en YAML](../plugins/yaml-datasets.md):
un nuevo archivo `.yaml` en `datasets/`, push, y volver a hacer fetch en
el servidor. Las descripciones, los parámetros y las preguntas de
ejemplo están escritas en portugués, acorde a la audiencia.
