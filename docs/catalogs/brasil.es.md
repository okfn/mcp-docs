# Implementación de Brasil

**Repo:** [okfn/mcp-dados-brasil](https://github.com/okfn/mcp-dados-brasil)
&middot; **Fuente:** [portaldatransparencia.gov.br](https://portaldatransparencia.gov.br)
&middot; **Idioma:** portugués

Herramientas MCP sobre las *emendas parlamentares* (enmiendas
parlamentarias) de Brasil, publicadas por la Contraloría General de la
Unión (CGU) en el Portal da Transparência.

## Lo más destacado

El plugin expone herramientas para consultar enmiendas por localidad,
autor, función y subfunción de gobierno, acción presupuestaria y tipo
de enmienda, además de rankings de principales beneficiarios
(*favorecidos*) y principales autores, y un
[glosario](../plugins/glossaries.md) con las definiciones oficiales
del diccionario de datos del portal (para que el modelo nunca confunda
los valores *empenhado*, *liquidado* y *pago*).

## Cómo funciona

El paquete incluye el dataset de enmiendas (archivos CSV del servicio
de descargas del Portal da Transparência) y un script
`load-emendas-db` que los carga en una base SQLite local. Cada
herramienta ejecuta una consulta SQL sobre esa base con pandas y
devuelve tablas y gráficos siguiendo el contrato estándar de
[resultados de las herramientas](../plugins/tool-results.md).

## Instalación

Es un paquete de Python instalable con pip, registrado a través del
entry point `mcp_server`. Instalalo en el entorno del servidor MCP,
ejecutá `load-emendas-db` una vez para construir la base local y
reiniciá el servidor. Las descripciones, los parámetros y las
preguntas de ejemplo se escriben en portugués, acorde a la audiencia.

## Desde el terreno

Este catálogo respaldó un piloto con la Contraloría General de la Unión
de Brasil, centrado en las **enmiendas parlamentarias**, uno de los
datasets más solicitados del portal. El objetivo era probar si la
ciudadanía podía preguntar en lenguaje natural y obtener respuestas
trazables hasta los datos oficiales. Los hallazgos están documentados
en la *Field Guide to Connecting AI to Public Information*.
