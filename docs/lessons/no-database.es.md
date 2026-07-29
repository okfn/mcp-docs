# Sin cuentas, sin base de datos

El piloto corre sin cuentas de usuario y sin base de datos. Los usuarios
no se registran, así que no podemos guardar ni compartir conversaciones
completas. Lo que sí se puede es descargar piezas individuales: una
tabla, un gráfico, o una de las respuestas de la IA.

## El compromiso

Esta es una decisión de diseño deliberada, y corta en ambos sentidos.

- **El beneficio:** el sistema se mantiene muy simple y muy fácil de
  instalar. No hay base de datos que operar, respaldar o asegurar, ni
  datos personales que custodiar.
- **El costo:** las conversaciones no se pueden guardar ni compartir, y
  no puedes descargar una respuesta completa (texto más tablas más
  gráficos) de una sola vez, solo las piezas.

Para un piloto, ganó la simplicidad, pero el lado del costo fue la queja
de producto más repetida en el feedback. Los testers comparan el chat
con las herramientas que usan todos los días, ChatGPT o Gemini, y contra
esa referencia la falta de historial y de compartir se siente de
inmediato.

Dos cosas para tener en cuenta al ponderar esa queja. Ser un producto de
chat completo nunca estuvo en el alcance del piloto. Y el chat gateway
es solo un cliente: el servidor MCP habla el protocolo estándar, así que
puede enchufarse a otros clientes de chat que ya ofrecen cuentas,
historial y compartir. Si un despliegue futuro necesita esas
funcionalidades en este gateway, ese es el punto en el que agregar
almacenamiento valdría su peso extra.
