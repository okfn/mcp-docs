# Un modelo abierto para datos públicos

La plataforma es más que código: es un modelo abierto para conectar la
IA con datos abiertos gubernamentales, diseñado para que otros
gobiernos y comunidades puedan reutilizarlo. Es parte de los
[AI Learning Labs](https://okfn.org/en/projects/ai-learning-labs/mcp-open-government-data/)
de la Open Knowledge Foundation, que convierten pilotos reales en
métodos abiertos y replicables para una IA responsable.

## Los dos objetivos

Todo se mide contra dos objetivos, elegidos porque son exactamente lo
que un LLM solo no puede ofrecer:

- **Precisión**: la respuesta se calcula a partir de los datos, no se
  recuerda del entrenamiento. Un modelo que memorizó una cifra la
  seguirá recitando después de que la cifra cambie; una herramienta que
  lee el dataset, no.
- **Trazabilidad**: la respuesta lleva un enlace a la fuente, para que
  quien lee pueda verificarla en lugar de confiar en ella. Esto es lo
  que hace que el sistema sea auditable por gente que no confía en él,
  que es la única clase de confianza que vale la pena tener para los
  datos públicos.

Una advertencia de los pilotos: un enlace a la fuente prueba de dónde
salieron los datos, no de dónde salió el razonamiento. Ver [la
trazabilidad es necesaria pero no
suficiente](../lessons/transparency.md).

## Tres ejes

**Colaboración.** El trabajo es una colaboración entre miembros de la
red, compartiendo problemas y soluciones en lugar de que cada uno
construya solo.

**Conocimiento abierto.** El desarrollo es de código abierto. El
conocimiento se comparte públicamente. El aprendizaje se documenta, se
traduce y se pone a disposición, de modo que el resultado es un modelo
abierto de buenas prácticas para conectar la IA y los datos abiertos,
no una caja negra.

**Estandarización.** Las buenas prácticas están incorporadas en el
diseño del servidor MCP. Los gobiernos enfrentan problemas similares
con datos similares, así que hay mucho espacio para la reutilización.
El ideal al que apuntamos es una arquitectura plug-and-play: trae tus
datos estandarizados y obtén un asistente funcionando.

La afirmación de reutilización ya tiene una primera prueba de campo:
después de uno de los pilotos, los propios técnicos del socio
construyeron un servidor MCP sobre otra fuente de datos, sin que nadie
se lo pidiera. Ver [lo que quedó después del
piloto](../lessons/ripple-effects.md).

## Hacia dónde va esto

Los pilotos alimentan una hoja de ruta más larga:

- Terminar la fase de pruebas de los pilotos e incorporar los
  comentarios recibidos.
- Documentar el aprendizaje (este sitio es ese paso) y traducirlo.
- Hacer que la documentación funcione para equipos técnicos con menos
  experiencia, y seguir publicando ejemplos avanzados funcionales. Los
  socios de los pilotos señalaron ambas cosas: los ejemplos como lo que
  ayudó, la claridad extra como lo que faltaba.
- Publicar el material de forma abierta.
- Hacer crecer un kit de herramientas reutilizable para datos
  estandarizados, para que un despliegue nuevo empiece desde una
  plantilla y no desde cero.
