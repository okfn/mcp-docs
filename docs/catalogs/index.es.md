# Casos de uso

La plataforma incluye dos plugins de referencia vivos en producción.
Cada uno se mantiene en su propio repositorio, en su idioma nativo, y
sirve como modelo oficial para construir nuevos plugins de dominio.

## Uruguay: Balance Energético Nacional

[mcp-datos-uruguay-ben](https://github.com/okfn/mcp-datos-uruguay-ben)

- **Datos de origen:** cifras del balance energético de
  [catalogodatos.gub.uy](https://catalogodatos.gub.uy/) (español).
- **Aspectos técnicos destacados:** herramientas en Python específicas
  del dominio, filtros de parámetros a medida, y glosarios de dominio
  inyectados para la terminología energética especializada.
- **Mejor uso:** plantilla para datasets complejos que requieren
  lógica Python a medida y definiciones de términos.

## Brasil: enmiendas parlamentarias

[mcp-dados-brasil](https://github.com/okfn/mcp-dados-brasil)

- **Datos de origen:** datos de asignación presupuestal de alta
  demanda de [dados.gov.br](https://dados.gov.br) (portugués).
- **Aspectos técnicos destacados:** consultas sobre registros
  financieros de alta frecuencia y manejo de terminología informal de
  los usuarios ("emendas pix") mediante mapeos de términos.
- **Mejor uso:** plantilla para seguir asignaciones financieras
  estructuradas y gasto público.

## Estado de desarrollo

Ambas implementaciones están actualmente en **Alpha**. Quienes
comiencen un nuevo plugin de país o de dominio deberían hacer un fork
de uno de estos repositorios como base de partida: mira [construir
plugins](../plugins/index.md).
