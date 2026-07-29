# Dos pilotos

La misma arquitectura se probó dos veces, en dos países, con dos
instituciones y dos datasets muy diferentes. Eso fue deliberado.

| | Brasil | Uruguay |
|---|---|---|
| **Socio** | Contraloría General de la Unión (CGU) | AGESIC |
| **Dataset central** | Enmiendas parlamentarias, uno de los datasets más solicitados del portal nacional | Balance Energético Nacional (BEN): importaciones de energía, generación, capacidad instalada |
| **Pregunta** | ¿Pueden los ciudadanos preguntar en lenguaje natural y obtener respuestas trazables a datos oficiales? | ¿La misma arquitectura se sostiene en otro país, contexto y entorno de datos? |
| **Otros datos que exploramos** | Transferencias de Bolsa Família por municipio, compras públicas federales, operadores de seguros de salud | Compras públicas en formato [Open Contracting](https://standard.open-contracting.org/) (OCDS), estadísticas de delitos sexuales |

La fila de "otros datos" es trabajo que probamos pero no terminamos: las
herramientas existen en los repos de plugins, algunas deshabilitadas o en
borrador, y no fueron parte de las pruebas estructuradas del piloto que se
describen abajo. Importan como evidencia de que la misma arquitectura se
estira a más datasets, en particular los datos de compras públicas en ambos
lados.

## Por qué dos

Un piloto demuestra que se puede construir un prototipo. Dos pilotos empiezan
a mostrar si el enfoque es portable: si la misma arquitectura basada en
MCP sobrevive a distintos datasets, distintas instituciones y
distintas necesidades de usuarios.

Esa portabilidad es todo el sentido de llamar a esto un
[modelo abierto](../overview/open-model.md) en lugar de un producto. Si
solo funcionara con el balance energético, sería una herramienta de energía.

## Cómo probamos

- **13 personas** probaron en total.
- Testers de **dentro de los gobiernos piloto**, que conocen los datos y
  el contexto institucional.
- Testers de **organizaciones de la sociedad civil**, actuando como
  validadores externos, sin el conocimiento interno que hace que una
  respuesta parezca correcta.
- Los testers hicieron sus propias preguntas y registraron el feedback en
  bitácoras.
- Las bitácoras se analizaron luego buscando precisión, patrones de
  problemas recurrentes y señales de usabilidad.
- El piloto corrió en **etapas cortas**, mostrando avances e incorporando
  feedback en cada paso. Un socio del piloto luego señaló este ritmo como
  una de las cosas que funcionaron.

## Qué nos propusimos aprender

**Respuestas precisas y verificables.** ¿El sistema devuelve respuestas
correctas? ¿Los usuarios pueden verificarlas contra la fuente? ¿Queda claro
de dónde salió la información?

**Comportamiento en conversaciones más largas.** ¿La calidad se mantiene a lo
largo de cinco a diez preguntas de seguimiento, o se cuelan pérdida de
contexto, contradicciones e interpretaciones sin respaldo? Esta es una
pregunta genuinamente abierta: la mayoría de las pruebas ocurren naturalmente
de a una pregunta por vez, y la degradación multi-turno es más difícil de
detectar y más difícil de medir. Todavía no tenemos una respuesta confiable.

**Usabilidad y adopción.** ¿La interfaz es intuitiva para personas que
no son técnicas ni expertas de dominio?

!!! note "La mayor parte del detalle aquí viene de Uruguay"
    Las páginas que siguen se basan principalmente en el piloto de Uruguay,
    que produjo el feedback estructurado más detallado. El informe
    consolidado entre pilotos todavía se está escribiendo, y esta sección
    crecerá a medida que se incorporen los hallazgos de Brasil y las
    sesiones de reflexión con los socios.
