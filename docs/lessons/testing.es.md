# Probar no es simple

Asegurarse de que las respuestas sean realmente correctas resultó ser
una de las partes más difíciles del trabajo, y es fácil subestimarla.

Verificar la calidad de la información requiere **tiempo** y
**conocimiento del dominio**. No puedes comprobar si una respuesta sobre
la matriz energética es correcta si no entiendes la matriz energética.
Eso pone la carga sobre expertos de dominio escasos, no sobre quien
casualmente esté construyendo el software.

Tampoco es siempre fácil dar feedback de forma manual. Un tester nota
que algo no cierra, pero identificar exactamente qué herramienta, qué
dataset y qué supuesto produjo el número incorrecto lleva un trabajo
paciente. Las respuestas trazables ayudan aquí: un tester puede seguir
un número hasta su fuente en lugar de adivinar.

## La revisión humana no es una fase, es un requisito

Los pilotos no revelaron una forma de evitar esto. **Se necesitan
personas que entiendan los datos para detectar afirmaciones plausibles
pero sin sustento**, y esa necesidad no desaparece a medida que el
sistema mejora. Los fallos que importan no son los obvios; son las
respuestas que parecen correctas para todos excepto para la persona que
conoce el dataset.

Planifica una revisión humana continua, no un hito de revisión que se
pasa una sola vez. Eso solo es realista si los expertos de dominio están
[a bordo desde el primer día](partners.md); en uno de los pilotos,
validar y pulir las respuestas fue la parte del trabajo que más tiempo
consumió.

## Las preguntas reales de los usuarios le ganan a las inventadas

Las pruebas más útiles vinieron de preguntas que la gente realmente
hace. Los socios del piloto nos entregaron sus preguntas frecuentes, y
esas se convirtieron directamente en casos de prueba.

Esto funcionó mejor que los casos de prueba que escribimos nosotros
mismos, en dos sentidos: las preguntas reales expusieron dónde las
**descripciones de las herramientas** eran confusas o engañosas, y
mostraron dónde el sistema necesitaba **límites más firmes**, lugares
donde respondía cuando debería haberse negado.

Si vas a correr un piloto, pídele a tu institución socia su FAQ antes de
escribir una sola prueba.

## Quién prueba importa

Mezclar testers de adentro del gobierno socio con testers de la sociedad
civil fue útil precisamente porque fallan de manera distinta. Los de
adentro detectan cifras incorrectas. Los de afuera detectan respuestas
que son técnicamente correctas pero incomprensibles, o que asumen en
silencio conocimiento que ellos no tienen. Ver
[dos pilotos](two-pilots.md).

Presupuesta tiempo real y experiencia real para las pruebas. No es una
formalidad que se pueda apurar al final. Un equipo de piloto dijo
exactamente esto en retrospectiva: dada la importancia de las pruebas y
la [complejidad de su dataset](start-simple.md), habrían asignado más
tiempo a esta etapa.
