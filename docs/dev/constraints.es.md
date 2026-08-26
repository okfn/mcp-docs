# Restricciones arquitectónicas

Dos decisiones de diseño deliberadas dan forma a la plataforma. Ambas
son compromisos, asumidos conscientemente, y ambas recibieron feedback
real de usuarios durante los pilotos.

## Gateway sin estado: sin cuentas, sin base de datos

**Decisión de diseño.** El sistema opera sin cuentas de usuario, sin
registro de sesiones y sin una base de datos central. Los usuarios
pueden descargar salidas individuales (tablas, gráficos o bloques de
texto), pero las conversaciones completas no se guardan ni se comparten
del lado del servidor.

**El compromiso.** Esto elimina la administración de bases de datos, el
cumplimiento de normas de retención de datos y la carga de gestión de
usuarios, manteniendo el servidor liviano y fácil de desplegar: no hay
base de datos que operar, respaldar o asegurar, ni datos personales que
custodiar.

El costo también es real. La falta de historial de chat fue la queja de
producto más repetida en el feedback del piloto: los testers comparan
el chat con las herramientas que usan todos los días, y contra esa
referencia la falta de historial y de compartir se siente de inmediato.

Dos cosas para tener en cuenta al ponderar esa queja. Ser un producto
de chat completo nunca estuvo en el alcance. Y el chat gateway es solo
un cliente: el servidor MCP sigue el protocolo estándar, así que puede
enchufarse a clientes de chat de terceros existentes que ya manejan
cuentas, historial y compartir. Si un despliegue futuro necesita esas
funcionalidades en este gateway, ese es el punto en el que agregar
almacenamiento valdría su peso extra.

## Presentación estructurada: tablas y gráficos

**Decisión de diseño.** Las herramientas devuelven datos estructurados
(tablas y gráficos) junto con las respuestas de texto para asegurar que
las respuestas sean auditables y verificables. Los usuarios valoran
esto mucho; es lo que hace que una respuesta pueda contrastarse con la
fuente.

**Mitigación en la interfaz.** La otra cara, reportada por varios
testers del piloto, es que las tablas y los gráficos a veces estaban
repetidos o eran demasiado verbosos. Por eso las salidas estructuradas
se muestran minimizadas por defecto en la interfaz: los registros
completos de la fuente quedan a un clic de distancia sin inundar el
flujo de la conversación.

Una mejor solución a futuro es detectar cuando la misma tabla o el
mismo gráfico se está dibujando por segunda vez y simplemente no
repetirlo. Esa deduplicación todavía no está construida; por ahora,
minimizar por defecto es la mitigación.
