# Plugins de alcance acotado

Empezamos con un repo de plugin por portal: `mcp-datos-uruguay` estaba
pensado para cubrir todo el portal de datos abiertos de Uruguay. Se volvió
demasiado general. Un solo repo que intenta hablar por cada dataset de un
portal termina siendo superficial en todo y autoridad en nada.

Así que dividimos. Creamos un repo enfocado,
[mcp-datos-uruguay-ben](https://github.com/okfn/mcp-datos-uruguay-ben),
acotado a un solo dominio: el *Balance Energetico Nacional*, el balance
energético nacional de Uruguay. El amplio `mcp-datos-uruguay` se retiró y
ya no está en uso.

## La lección

**Prefiere un experto de dominio antes que un generalista del portal de
datos abiertos.** Un plugin es mucho mejor cuando la persona detrás entiende
profundamente un área temática, los datos de energía, sus términos, sus
particularidades, que cuando alguien sabe un poco de cada dataset que un
portal publica.

El alcance acotado rinde de formas concretas:

- Las descripciones de las herramientas y las preguntas de ejemplo son más
  precisas, porque las escribe alguien que sabe qué pregunta la gente
  realmente.
- Un [glosario de dominio](glossary.md) es viable de construir y mantener
  correcto cuando cubre un campo, no un portal entero.
- El repo se mantiene pequeño y fácil de mantener, y los distintos dominios
  evolucionan a su propio ritmo en sus propios repos.

Ante la duda, divide por dominio, no por portal ni por país.

Esta página trata de *quién* debería estar detrás de un plugin. Igual de
importante es *cuándo* se suma: mira [expertos de dominio desde el primer
día](partners.md).
