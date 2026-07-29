# Lecciones de los pilotos

Probamos la misma arquitectura en **dos pilotos gubernamentales**, en Brasil
y en Uruguay: mira [dos pilotos](two-pilots.md) para saber quiénes, cómo y qué
nos propusimos aprender. El piloto de Uruguay, que funcionó públicamente en
[mcp-uruguay.okfn.org](https://mcp-uruguay.okfn.org/), produjo el feedback
más detallado, así que la mayoría de los ejemplos concretos vienen de ahí.

Esta sección está escrita para cualquiera que esté construyendo u operando un
despliegue similar: qué funcionó, qué no, y qué cambiamos en el
camino.

!!! note "Lee esto como notas de campo, no como un veredicto"
    El feedback llegó mientras todavía estábamos desplegando versiones nuevas,
    así que no es estrictamente feedback sobre un producto terminado. Varios de
    los problemas descritos aquí ya estaban corregidos por cambios publicados
    durante el piloto. Cuando ese es el caso, la página lo dice.

## La versión corta

La experiencia general fue positiva. Cuando les preguntamos a los socios
qué le dirían a otro gobierno que estuviera considerando un enfoque similar,
su respuesta empezó, literalmente, con "¡Háganlo!". El patrón que los usuarios
más valoraron fue
la combinación de **tablas y gráficos de autoría humana inyectados junto a
la respuesta final de la IA**: la prosa viene del modelo, pero los números
y sus fuentes vienen directamente de los datos. Cuanto más experto era el
usuario y mejor conocía los datasets, más cosas pequeñas encontraba
para mejorar, que es exactamente el tipo de feedback que queríamos.

Un ejemplo concreto de impacto: wikimedistas usaron la herramienta para mejorar
el artículo de Wikipedia sobre energía solar en Uruguay. Es un gran caso de uso,
y un recordatorio de que una herramienta tan fluida también podría usarse mal
con la mejor de las intenciones, así que la verificación importa.

## Lo que aprendimos, por tema

- [Dos pilotos](two-pilots.md): con quiénes probamos, cómo, y
  qué nos propusimos aprender.
- [Conectar los datos es la parte fácil](meaning.md): el acceso no es
  comprensión, y el significado es donde está el trabajo.
- [Plugins de alcance acotado](scope.md): por qué dividimos el amplio
  repo de Uruguay en uno enfocado y específico de un dominio.
- [Expertos de dominio desde el primer día](partners.md): cuándo tienen que
  llegar los dueños de los datos, y cómo elegir el equipo socio.
- [Empezar con un dataset simple](start-simple.md): establecer el
  enfoque sobre datos fáciles antes de escalar a datos complejos.
- [El compromiso del YAML](yaml-tradeoff.md): por qué declarar datasets en YAML
  es una buena idea solo para casos realmente simples.
- [Confiabilidad de los cálculos](calculations.md): por dónde pueden
  colarse números incorrectos, y cómo prevenirlo.
- [Transparencia y confianza](transparency.md): el modelo mezclando su propio
  conocimiento con los datos, y por qué siempre deberías repreguntar.
- [Calidad y apertura de los datos](data-quality.md): el piloto como
  incentivo para abrir datos bien documentados.
- [Herramientas nuevas, problemas viejos](data-access.md): las preguntas de
  gobernanza de datos que conectar IA no te permite saltarte.
- [Probar no es simple](testing.md): por qué verificar respuestas lleva tiempo
  y conocimiento de dominio.
- [Un glosario de dominio](glossary.md): definiciones oficiales, inyectadas en
  el contexto de las herramientas.
- [Recursos de datos abiertos](resources.md): dirigir a los usuarios a los
  datos crudos más allá de nuestra herramienta.
- [Tablas y gráficos](presentation.md): demasiados, y qué hicimos al
  respecto.
- [Sin cuentas, sin base de datos](no-database.md): el costo y el beneficio de
  mantenerse simple.
- [Lo que quedó después del piloto](ripple-effects.md): las capacidades
  que el piloto dejó en el gobierno socio.
- [Fortalezas y debilidades](summary.md): el balance
  consolidado.
