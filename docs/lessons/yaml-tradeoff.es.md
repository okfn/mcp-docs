# El compromiso del YAML

Declarar datasets en YAML en lugar de escribir Python parece una gran
idea: nada de código, solo un archivo prolijo por dataset. Funciona, y para un
dataset genuinamente simple es rápido y agradable. Pero es una buena idea para
usar con cuidado, y terminamos usando mucho menos YAML del que esperábamos.

## Por qué

Un formato YAML declarativo es, al final, un **nuevo lenguaje de consulta**.
Para expresar una pregunta real necesitas engines, filtros, formateadores,
plantillas de respuesta, y reglas sobre cómo se combinan. Cada capacidad que
un dataset real pide (un nuevo tipo de filtro, un join, una columna calculada,
un formato especial) tiene que agregarse a ese lenguaje y después ser
aprendida por quien escriba el YAML.

Así que la aparente simplicidad se mueve en lugar de desaparecer. En vez de
escribir unas pocas líneas de Python que cualquier desarrollador Python puede
leer, escribes YAML en un dialecto a medida que solo este proyecto entiende, y
cuando no da más de sí te quedas atascado.

## Nuestra regla práctica

- ¿Un **dataset realmente simple**, un CSV plano con preguntas obvias de
  agregación o top-N? YAML está bien y es rápido.
- ¿**Cualquier cosa más allá de eso**? Recurre a una [herramienta
  Python](../plugins/python-tools.md). Es más clara, más potente, y
  usa un lenguaje que la gente ya conoce en lugar de uno que inventamos.

Nada de esto hace que el YAML esté mal. Lo hace una herramienta afilada para
un trabajo acotado. Úsalo para los casos simples, y no intentes hacerlo crecer
hasta un lenguaje de consulta general, porque ese es un lenguaje que después
tendrías que mantener.
