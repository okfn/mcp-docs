# Herramientas nuevas, problemas viejos

Conectar una IA a un portal de datos abiertos es una herramienta nueva y
brillante, pero arrastra un conjunto de preguntas muy viejas sobre
gobernanza de datos. Ninguna tiene que ver con la IA; todas deciden si
se puede confiar en las respuestas.

- **¿Acceso directo o una copia de lectura?** ¿Las herramientas leen los
  datos abiertos directamente del portal, o una copia separada de solo
  lectura? Cada opción tiene consecuencias para la frescura de los datos
  y para la carga sobre el portal.
- **¿Los datos, o una vista de ellos?** ¿Estamos sirviendo el dataset
  crudo o alguna vista transformada, y esa transformación está
  documentada?
- **¿Es la última versión?** Un dataset cacheado o copiado puede quedar
  silenciosamente desactualizado respecto de la fuente. Una respuesta
  basada en datos viejos sigue siendo incorrecta.
- **¿Estamos inflando las estadísticas del portal?** Si cada consulta
  golpea el endpoint de datos abiertos, podemos estar distorsionando las
  métricas de uso del propio portal solo por leer datos para responder
  preguntas.
- **¿Qué reglas de negocio están incrustadas en los datos?** Los
  datasets se producen con supuestos y reglas embebidos. Esas reglas
  muchas veces hay que explicárselas al usuario, o el número se presta a
  malas lecturas.

La lección no es resolver todo esto de una vez, sino decidir cada punto
deliberadamente para tu despliegue, y dejar la decisión por escrito. Las
herramientas nuevas no te eximen de las preguntas viejas.
