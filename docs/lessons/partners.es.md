# Expertos de dominio desde el primer día

Correr la misma arquitectura dos veces nos dio una comparación limpia. En un
piloto, los expertos del equipo dueño de los datos estuvieron involucrados
desde el principio. En el otro, se sumaron más tarde, y todo llevó más
tiempo. Misma arquitectura, mismo proceso, distinta alineación inicial, y la
diferencia fue visible.

La lección, en palabras del propio socio: tener al experto de dominio
disponible e involucrado **desde el principio**. Los dueños de los datos no
pueden llegar al final.

[Plugins de alcance acotado](scope.md) argumenta *quién* debería estar detrás
de un plugin: alguien que entiende profundamente un dominio. Esta página trata
de *cuándo*. Esa persona tiene que estar en la sala antes de que se escriba la
primera herramienta, porque la mayor parte del trabajo es [explicarle los
datos a la máquina](meaning.md) y [verificar las respuestas](testing.md), y
ambas cosas necesitan al experto, no al programador.

## Elegir el equipo socio

Elegir qué institución y qué equipo aloja un piloto es una decisión, no un
valor por defecto. Lo que sugiere la experiencia del piloto:

- **Elige el mejor equipo, no el más cercano.** La calidad del
  plugin tiene como techo qué tan bien el equipo detrás de los datos los
  conoce.
- **Elige un equipo que tenga tiempo.** Un socio apretado de tiempo puede
  dejar el piloto colgado a mitad de camino, sin nadie disponible para validar
  respuestas o mejorar descripciones.
- **El apoyo de la alta dirección importa.** El tiempo solo se materializa
  cuando el liderazgo del equipo trata el piloto como trabajo real, no como
  un favor.

Empieza solo cuando el tiempo y el apoyo institucional estén
realmente ahí. Si no lo están, espera o elige otro socio; un piloto
que se estanca a medio validar es peor que uno que empieza más tarde.

El apoyo no se necesita solo para empezar. Continuar después del piloto
implica que el trabajo tiene que ganarse un lugar en el backlog de desarrollo
propio de la organización, y eso requiere construir apoyo entre los otros
equipos internos de datos, no solo el que alojó el piloto.

## El equipo técnico interno también

Los expertos de dominio no son las únicas personas a incorporar temprano. Los
técnicos de uno de los pilotos trabajaron con las manos en la masa desde el
inicio, leyendo los repos y ejecutando el servidor ellos mismos, y después
del piloto pasaron a
[construir su propio servidor MCP](ripple-effects.md). El otro equipo, en
retrospectiva, habría involucrado a su personal técnico interno más
activamente: trabajando junto al equipo del proyecto y replicando partes del
proceso con las mismas herramientas y metodología.

Ambas experiencias apuntan a la misma lección. La documentación apoya la
replicación futura, pero el involucramiento práctico es lo que transfiere
conocimiento y construye apropiación interna. Un equipo que solo lee sobre
el piloto hereda un informe; un equipo que trabaja dentro de él hereda una
capacidad.

## La carga de trabajo es real, y vale la pena

Sé honesto con el socio desde el inicio: alojar un piloto es trabajo extra
para el equipo dueño de los datos, encima de sus tareas normales. La
validación y el pulido, no la plomería, es donde se va la mayor parte de ese
tiempo.

Se recupera. Al final del piloto el equipo dueño de los datos estaba motivado
por ver sus datos usados de esta manera, y consideró que el resultado valió
el esfuerzo: una herramienta nueva y propia para seguir puliendo y
eventualmente publicar, con advertencias claras sobre sus limitaciones.
