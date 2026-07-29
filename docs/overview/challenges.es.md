# El desafío

La pregunta que dio origen al proyecto:

> ¿Cómo podemos llevar la IA más reciente (los grandes modelos de
> lenguaje) a los portales de datos abiertos **sin comprometer la
> confianza en la información pública**?

Es más difícil de lo que suena, porque usar un LLM por sí solo choca
con varios problemas a la vez.

## Los LLM no están construidos para decir la verdad

Su salida es una estimación. Los sesgos, los vacíos en los datos de
entrenamiento y los límites de la arquitectura hacen que una respuesta
fluida no sea necesariamente una respuesta correcta. La precisión no es
algo que venga gratis.

## No puedes ver por qué responden lo que responden

Incluso cuando un modelo muestra su "razonamiento", eso no resuelve el
problema: solo le pasa al ciudadano el trabajo de verificar la verdad.
Y como los modelos son no deterministas, la misma pregunta puede
producir una cadena de razonamiento distinta cada vez.

## Son poco confiables en las partes mecánicas

Los LLM no son buenos escribiendo SQL correcto contra bases de datos
reales y, en general, no son la "inteligencia" que sugiere el
marketing. Nuestro diseño se apoya en este hecho en lugar de pelear
contra él: el modelo nunca escribe la consulta. Elige entre
[herramientas](../plugins/index.md) predefinidas que ejecutan consultas
verificadas, así que el trabajo con los datos lo hace el código, no lo
adivina el modelo.

## No van a decir "no lo sé"

Algunos modelos son agresivamente serviciales: ante una pregunta,
torturan los datos que tengan a mano hasta que arrojen una respuesta
que parezca satisfacerla. No saber decir "no tengo eso" es en sí mismo
una fuente de respuestas incorrectas.

## Nuestra respuesta

No intentamos hacer que el LLM sea confiable por sí solo. Lo ponemos
detrás de una capa de herramientas sobre datos reales, apuntando a dos
cosas que el modelo no puede garantizar solo: [precisión y
trazabilidad](open-model.md). El modelo se encarga del lenguaje; los
datos se encargan de los hechos.
