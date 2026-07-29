# Confiabilidad de los cálculos

Esta es la única área donde los testers reportaron respuestas
**numéricamente incorrectas pero presentadas como datos**. Las consultas
directas ("¿cuál fue el valor X en el año Y?") fueron confiables. Los
cálculos derivados no.

La pregunta riesgosa parece simple: "dame una tabla con los porcentajes
de X". El problema es que X puede ir desde una cifra simple hasta algo que
agrega varios otros números, y el modelo no tiene ninguna garantía de
hacer bien la aritmética.

## Cómo mitigarlo

La solución confiable es no pedirle al modelo que haga las cuentas. Precalcula
el valor derivado con [Python y pandas](../plugins/python-tools.md) para que
se convierta en una columna real del dataset, y documenta esa columna.
Entonces la herramienta solo la lee.

- **Casos simples** (un porcentaje directo de un dataset): agrega el
  porcentaje como una columna nueva con pandas. Documenta qué significa.
- **Casos complejos** (un porcentaje que cruza varias columnas o
  datasets): precalcula, otra vez con pandas, el porcentaje que la gente
  realmente tiende a preguntar, por ejemplo "¿qué proporción fue renovable en
  el año X?".
- **Casos difíciles y muy específicos** ("¿cuánto creció X entre el año Y1
  y el año Y2?"): demasiado específicos para precalcularlos para cada par. Una
  herramienta que actúe como una pequeña calculadora podría ayudar aquí.
  Todavía no lo hemos probado.

## La conclusión

Trata cualquier porcentaje o variación interanual calculada al vuelo como
sospechosa hasta que una herramienta la compute desde una columna
documentada. Si un número importa, debe venir de los datos, no de la cabeza
del modelo.
