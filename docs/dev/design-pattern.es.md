# Patrón de diseño: plugins modulares

**Acota los plugins por dominio, no por portal.**

Los plugins deben estar acotados a un solo dataset o dominio
específico, por ejemplo el repo del Balance Energético Nacional de
Uruguay,
[mcp-datos-uruguay-ben](https://github.com/okfn/mcp-datos-uruguay-ben),
en lugar de intentar cubrir todo un portal gubernamental de datos
abiertos en un solo repositorio.

Aprendimos esto por las malas. El repo original `mcp-datos-uruguay`
estaba pensado para cubrir todo el portal de datos abiertos de Uruguay,
y se volvió demasiado general: un solo repo que intenta hablar por cada
dataset de un portal termina siendo superficial en todo y autoridad en
nada. Se retiró en favor del repo enfocado en el balance energético.

## Fundamentos

Los plugins de portal completo se convierten en generalistas
superficiales. Acotar los límites del plugin a un solo dominio ofrece
ventajas técnicas clave:

- **Descripciones de herramientas más precisas.** Los prompts y los
  parámetros de las herramientas se escriben específicamente para los
  patrones de consulta reales del dataset, por alguien que sabe qué
  pregunta la gente realmente.
- **Glosarios manejables.** La terminología del dominio y los
  diccionarios de datos se mantienen precisos y viables de mantener
  cuando cubren un campo, no un portal entero.
- **Ciclo de vida independiente.** Los repositorios se mantienen
  pequeños, limpios y capaces de evolucionar a su propio ritmo sin
  romper herramientas de datasets no relacionados.

## La regla práctica

Prefiere un experto de dominio antes que un generalista del portal de
datos abiertos. Un plugin es mucho mejor cuando la persona detrás
entiende profundamente un área temática - los datos de energía, sus
términos, sus particularidades - que cuando alguien sabe un poco de
cada dataset que un portal publica.

Ante la duda, divide por dominio, no por portal ni por país.
