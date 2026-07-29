# Transparencia y confianza

Varios testers, de forma independiente, reportaron lo mismo: el modelo mezcla
su **conocimiento general** con los **datos duros** de los datasets,
sin decir qué es qué. Fue el patrón negativo más repetido.

## Qué cambiamos

Actualizamos el system prompt para pedirle al modelo que siempre distinga lo
que viene de los datasets de lo que viene de su conocimiento general o de sus
propias deducciones. Esto mitiga el problema pero no elimina la necesidad
de que el usuario verifique.

## Qué decirles a los usuarios

El hábito más útil es repreguntar:

> "¿Todo lo que me acabas de decir está respaldado por los datos que leíste, o
> por tu entrenamiento?"

En general la IA es honesta aquí. Diferencia mejor sus fuentes
cuando se le pregunta directamente, y a menudo se retracta cuando se da cuenta
de que mezcló un hecho general en una respuesta de datos y se equivocó en
algo.

## La trazabilidad es necesaria, pero no suficiente

Un enlace a la fuente le permite al usuario verificar un número. No impide que
el sistema envuelva ese número en una interpretación que la fuente nunca
respaldó.

En un ejemplo de los pilotos, el sistema explicó un cambio refiriéndose a
**"factores climáticos"**, aunque el dataset no contenía ningún dato
climático. El número era correcto y el enlace era correcto. La explicación
alrededor era inventada, y sonaba completamente plausible.

El enlace prueba de dónde vinieron los *datos*. No dice nada sobre de dónde
vino el *razonamiento*. El lector todavía tiene que notar cuando una respuesta
afirma una causa que ningún dataset conectado podría conocer.

## La confianza no sigue a la evidencia

El **tono de confianza del modelo no cambia con la calidad de
su evidencia**. Responde con la misma seguridad tenga o no
realmente los datos. Los usuarios no pueden usar la confianza como señal de
confiabilidad, que es exactamente por lo que repreguntar y verificar
importan.
