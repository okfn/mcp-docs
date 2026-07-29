# Conectar los datos es la parte fácil

La lección principal de ambos pilotos: **darle al modelo acceso a
datos oficiales no fue la parte difícil.**

La capa MCP hace ese trabajo, y lo hace de forma confiable. Apunta el servidor
a un dataset, describe las herramientas, y el modelo puede leer números reales
en lugar de recordarlos.

Pero el acceso no es comprensión. Un modelo que puede leer una columna de
números todavía no sabe:

- Qué significan realmente los términos, en el sentido oficial.
- En qué unidades están los valores.
- Qué período de tiempo cubre una cifra, y si los períodos son comparables.
- Qué deja afuera el dataset deliberadamente.
- Qué supuestos se hicieron cuando se compilaron los datos.

Estos no son detalles de apoyo que puedas agregar después para pulir. **Deciden
si una respuesta es correcta.** Un número correcto bajo una etiqueta
equivocada es una respuesta equivocada.

## Qué significa esto en la práctica

La mayor parte del trabajo real de construir un plugin no es plomería, es
explicarle los datos a la máquina:

- Escribir un [glosario de dominio](glossary.md) e inyectar las definiciones
  oficiales en el contexto de las herramientas, para que el modelo las tenga al
  componer cada respuesta.
- Escribir descripciones de herramientas y parámetros que declaren unidades y
  períodos explícitamente, en lugar de asumir que son obvios.
- Ser explícito sobre los límites de un dataset, para que el modelo pueda decir
  "no está en los datos" en lugar de estirarse.
- Mantener los plugins [acotados a un dominio que alguien realmente
  entiende](scope.md), porque nadie puede escribir buenas descripciones para
  un portal con el que no ha trabajado.

Por eso también [la calidad de los metadatos importa tanto como la calidad de
los datos](data-quality.md). Presupuesta para el significado, no solo para la
conexión.
