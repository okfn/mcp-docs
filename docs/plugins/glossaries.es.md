# Implementar glosarios de dominio

Los datasets públicos suelen apoyarse en términos administrativos
específicos del dominio, taxonomía legal o unidades especializadas
(como las cifras del balance energético o los códigos presupuestales)
que los no expertos, y los LLM generales, pueden malinterpretar.

Para asegurar respuestas precisas, los plugins deberían incluir un
**glosario de dominio** que inyecte las definiciones oficiales de los
términos directamente en el contexto de las herramientas. En el piloto
de Uruguay, inyectar las definiciones oficiales del balance energético
(BEN) resultó ser esencial para los usuarios no expertos, y mejoró las
respuestas de forma medible.

## Cómo funciona la inyección del glosario

Las definiciones del glosario cumplen un doble propósito en la
arquitectura MCP:

1. **Inyección en el contexto del LLM.** Los términos y definiciones
   se incluyen en el system prompt o en la descripción de la
   herramienta. Cuando el LLM recibe resultados de datos, usa estas
   definiciones para interpretar las cifras crudas y escribir prosa
   precisa.
2. **Claridad para el usuario.** Los términos pueden exponerse
   directamente en la interfaz para que los usuarios consulten las
   definiciones oficiales junto a los resultados de su consulta.

## Pautas de implementación

- **Mapea los términos a herramientas específicas.** Evita volcar el
  diccionario entero de un portal en cada prompt. Cura manualmente y
  adjunta solo los términos relevantes a la herramienta específica que
  los usa. Esto conserva espacio en la ventana de contexto y evita
  confusiones en el prompt. El mapeo es manual y un poco tedioso, pero
  la recompensa, respuestas más claras y menos malentendidos, hace que
  el esfuerzo valga la pena.
- **Tiende un puente entre el lenguaje cotidiano y los términos
  burocráticos.** Incluye mapeos de alias en las descripciones de tus
  herramientas, por ejemplo mapeando términos informales de los
  usuarios como "pix" o "impuesto al combustible" a sus nombres de
  categoría administrativa oficiales en el dataset. Sin ese puente, la
  IA puede reportar que faltan datos simplemente porque el usuario no
  conocía la frase burocrática exacta.
- **Trata los glosarios como código.** Presupuesta tiempo de
  desarrollo para el mapeo del glosario durante la creación del
  plugin. Definir la terminología es un requisito técnico central para
  la precisión de las consultas, no un retoque de documentación
  posterior al lanzamiento.
