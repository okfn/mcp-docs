# Calidad y apertura de los datos

Lo más importante que nos mostró el piloto no tiene que ver con la IA en
absoluto: **es un fuerte incentivo para abrir datos buenos y bien
documentados.**

A medida que los usuarios profundizaban, los expertos de dominio notaban
una y otra vez que al portal le faltaban datasets necesarios para
responder sus preguntas. Durante el piloto se agregaron cinco datasets de
consumo de energía por sector, y las respuestas mejoraron mucho. Tres de
los cinco se conectaron a herramientas MCP; los dos restantes quedaron
pendientes para el equipo del portal.

Estas herramientas solo funcionan cuando los datos subyacentes son de
buena calidad y están bien documentados. Los datos de este piloto eran
excelentes, y esa es una gran parte de por qué funcionó.

Vale la pena convertir eso en una precondición: **analizar la calidad y
la documentación de los datasets candidatos antes de que empiece el
piloto**, y elegir datos que ya sean buenos. El piloto va a sacar a la
luz carencias de todos modos (el nuestro reveló datasets cuyas
descripciones necesitaban mejoras, y la ausencia de metadatos se nota en
el momento en que una pregunta depende de ellos), pero un piloto debería
profundizar datos buenos, no rescatar datos malos.

La calidad tiene dos mitades, y ambas importan:

- **La calidad de los datos** determina directamente la calidad de las
  respuestas.
- **La calidad de los metadatos** es lo que hace que la experiencia sea
  didáctica: buenas descripciones, unidades y definiciones son lo que le
  permite al asistente explicar un número en lugar de solo recitarlo.
  Por eso también rinde un
  [glosario de dominio](glossary.md).

La mitad de los metadatos es además un desafío más amplio para los
proveedores de datos abiertos. Las descripciones de los datasets muchas
veces no son tan claras ni tan completas como deberían, especialmente en
organizaciones que administran grandes cantidades de datasets, donde
nadie puede pulir a mano cada entrada. Mejorarlas es lo que hace que los
datasets sean más fáciles de descubrir e interpretar, tanto para los
sistemas de IA como para las personas.

Aquí se esconde un **círculo virtuoso**. Cuando los expertos de dominio
conversan con la herramienta, ven rápidamente que las respuestas que les
faltan faltan porque los datos no están. Eso los empuja a abrir más
datos, lo que desbloquea más respuestas, lo que invita a más preguntas.
La herramienta se convierte en un motor para abrir datos de calidad.

## La cobertura es la hoja de ruta

Las respuestas se calculan solo a partir de los datasets conectados, así
que las preguntas que van más allá de lo conectado simplemente no
obtienen respuesta. Ese es el comportamiento honesto que queremos (mejor
un claro "no está en los datos" que un número inventado), pero significa
que la hoja de ruta de la herramienta es en realidad la hoja de ruta de
los datos: la cobertura crece exactamente tan rápido como crecen los
datos abiertos y documentados que hay detrás. Hay que seguir integrando
y conectando nuevos datasets; es un trabajo de largo plazo que ningún
piloto resuelve por sí solo.
