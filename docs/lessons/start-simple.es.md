# Empezar con un dataset simple

El consejo más claro que un equipo del piloto ofreció en su sesión de
reflexión: si lo hicieran de nuevo, empezarían con un dataset más
simple.

Uno de los pilotos corrió sobre un dataset particularmente desafiante. El
enfoque se sostuvo bien bajo esas condiciones, y fue una prueba de estrés
valiosa: mostró que la arquitectura no depende de que los datos sean
fáciles. Pero el precio fue real. Producir respuestas confiables requirió
considerablemente más adaptación, ajuste fino y herramientas de apoyo de lo
esperado, se apoyó fuertemente en el [aporte de expertos](partners.md), y la
complejidad de los datos multiplicó el costo de
[las pruebas y la validación](testing.md).

## El consejo

Establece el enfoque sobre datos simples primero, y después escala.

- **Primer dataset: simple.** Haz funcionar todo el método de punta a punta
  sobre datos que sean fáciles de explicar: las herramientas, las
  descripciones, el [glosario](glossary.md), el ciclo de pruebas. Cada
  problema que encuentres será un problema del método, no de los datos.
- **El dataset difícil, segundo.** Una vez establecido el método, un dataset
  complejo se convierte en una prueba de estrés que eliges, no en un riesgo
  que descubres a mitad del piloto.

Esto se combina con [plugins de alcance acotado](scope.md): un dominio
acotado y un primer dataset simple son el mismo instinto aplicado dos veces.
Reduce lo que debes explicarle a la máquina hasta que puedas explicarlo bien.
