# Fortalezas y debilidades

## La conclusión principal

El sistema es bastante **determinista cuando se le pregunta algo muy
específico**, como "¿cuál fue el valor X en el año Y?". A medida que las
preguntas se vuelven más abiertas, las respuestas divergen más. Los
usuarios deben tener esto presente en todo momento: **repreguntar y
verificar.** Estas herramientas deben usarse con cuidado.

## Fortalezas

- **Precisión en consultas específicas.** Cuando una pregunta apunta a
  un valor que existe en un dataset, el comportamiento es casi
  determinista.
- **Honestidad sobre los límites de los datos.** En general dice
  claramente cuando algo no está en el dataset, en lugar de inventarlo.
- **Se recupera bien de las correcciones.** Cuando un usuario repregunta
  o señala un error, recalcula, lo admite y corrige la respuesta.
- **El glosario ayuda.** Las definiciones oficiales del dataset, tanto
  consultables como
  [inyectadas en el contexto de las herramientas](glossary.md), mejoran
  las respuestas y ayudan a los no expertos.
- **Las tablas y gráficos de autoría humana** junto a la respuesta de la
  IA son muy valorados y son la garantía de precisión.
- **Utilidad real y concreta.** Los usuarios lo pusieron a trabajar en
  serio, por ejemplo mejorando un artículo de Wikipedia.
- **Impulsa los datos abiertos.** El piloto revela qué datasets faltan y
  exige buena documentación.
- **Transfiere capacidades.** Los técnicos de los socios aprendieron el
  enfoque lo suficiente como para construir su propio servidor MCP, sin
  que nadie se lo pidiera. Ver
  [lo que quedó después del piloto](ripple-effects.md).
- **Simple de operar.** Sin cuentas, sin base de datos.

## Debilidades

- **Los cálculos derivados no están garantizados.** Los porcentajes y
  las variaciones interanuales fueron los únicos casos en que se
  presentaron números incorrectos como datos. Ver
  [confiabilidad de los cálculos](calculations.md).
- **Mezcla conocimiento del modelo con datos del dataset** sin
  señalarlo. Mitigado con un
  [cambio en el system prompt](transparency.md), pero sigue necesitando
  verificación del usuario.
- **Tono seguro independientemente de la evidencia.** Suena igual de
  seguro con o sin datos.
- **Tablas y gráficos repetidos o innecesarios.** Mitigado
  [minimizándolos por defecto](presentation.md).
- **Sin conversaciones guardadas ni compartidas** al no haber cuentas, y
  sin descarga en un clic de una respuesta completa.
- **La cobertura depende de los datasets conectados.** Las preguntas más
  profundas quedan sin respuesta hasta que se
  [abran y conecten más datos](data-quality.md).
- **Las preguntas abiertas divergen** y necesitan verificación del
  usuario.
