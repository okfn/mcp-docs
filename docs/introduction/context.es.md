# Contexto del proyecto

**Conectar la IA a los datos públicos abiertos.**

Los datos públicos abiertos son esenciales para la transparencia, la
rendición de cuentas y la toma de decisiones informada. Sin embargo,
extraer respuestas de los portales oficiales a menudo requiere navegar
interfaces complejas, escribir consultas técnicas y dedicar bastante
tiempo a interpretar archivos crudos.

Integrar la IA permite a los usuarios consultar los datos usando
lenguaje natural, pero los modelos de IA estándar también introducen un
riesgo importante: alucinaciones, cifras mal calculadas y errores de
apariencia plausible que socavan la confianza en la información
oficial.

Para resolver esto, los
[AI Learning Labs](https://okfn.org/en/projects/ai-learning-labs/mcp-open-government-data/)
de la Open Knowledge Foundation construyeron un puente técnico abierto
usando el Model Context Protocol (MCP). Probamos este enfoque sobre dos
datasets públicos en vivo:

- **Brasil**: enmiendas parlamentarias (seguimiento de fondos
  públicos).
- **Uruguay**: Balance Energético Nacional (monitoreo de la transición
  energética).

## Principios técnicos centrales

- **Precisión y trazabilidad.** Las respuestas deben basarse
  estrictamente en datasets oficiales, y cada respuesta debe enlazar a
  su fuente. El servidor hace cumplir esta regla en el código.
- **Código simple antes que lenguajes a medida.** Las herramientas se
  escriben como pequeñas funciones estándar de Python. Los datasets
  simples pueden declararse en YAML sin escribir código.
- **Stack tecnológico simple y probado.** Construido sobre tecnologías
  de código abierto, estándar y confiables (Python, CSV, SQLite,
  HTML/JS planos). El sistema completo puede correr localmente en una
  laptop sin infraestructura compleja.
- **Propiedad local.** Cada equipo mantiene su propio repositorio de
  plugin de forma independiente, en su idioma preferido y con su propio
  ritmo de releases.
