# Tablas y gráficos

Las herramientas MCP están construidas para mostrar siempre tablas y
gráficos junto a la respuesta. Los usuarios valoran esto mucho, es lo
que hace que una respuesta sea verificable, pero varios testers
reportaron la otra cara: las tablas y los gráficos a veces estaban
**repetidos o eran demasiado verbosos**.

## Qué cambiamos

A partir de ese feedback, las tablas y los gráficos ahora se muestran
**minimizados por defecto**. La información sigue ahí, a un clic de
distancia, pero ya no inunda la conversación.

## Qué sigue abierto

Una mejor solución a futuro es detectar cuando la misma tabla o el mismo
gráfico se está dibujando por segunda vez y simplemente no repetirlo.
Esa deduplicación todavía no está construida; por ahora, minimizar por
defecto es la mitigación.
