# Implementación de Uruguay

**Repo:** [okfn/mcp-datos-uruguay-ben](https://github.com/okfn/mcp-datos-uruguay-ben)
&middot; **Portal:** [catalogodatos.gub.uy](https://catalogodatos.gub.uy/)
&middot; **Idioma:** español

Herramientas MCP sobre el *Balance Energetico Nacional* (BEN, el
balance energético nacional) de Uruguay, publicado por el Ministerio de
Industria, Energía y Minería (MIEM) en el portal nacional de datos
abiertos.

![El catálogo de energía de Uruguay respondiendo preguntas en el chat](../assets/images/datos-uruguay.png)

## Lo más destacado

El plugin expone herramientas sobre la matriz eléctrica, la potencia
instalada, el factor de emisión de la red, el consumo final, el
abastecimiento primario, las importaciones de petróleo y gas, el
intercambio de electricidad y las emisiones de CO2 por sector, además
de un [glosario del BEN](../plugins/glossaries.md) con definiciones
oficiales.

## Acotado a propósito

Este repo reemplazó al anterior `mcp-datos-uruguay`, más amplio, que
intentaba cubrir todo el portal y se volvió demasiado general. Acotar
el plugin a un solo dominio bien entendido (energía) es una decisión
deliberada: ver [por qué acotamos los
plugins](../dev/design-pattern.md).

## Instalación

Es un paquete de Python instalable con pip. Instálalo en el entorno del
servidor MCP y reinicia el servidor. Las descripciones, los parámetros
y las preguntas de ejemplo están escritas en español, acorde a la
audiencia.

## Desde el terreno

Este catálogo impulsó un piloto público sobre los datos de energía de
Uruguay en julio de 2026. Todo lo que aprendimos al operarlo, las
fortalezas, los modos de falla y los cambios que publicamos, está
escrito en la *Field Guide to Connecting AI to Public Information*
(guía de campo para conectar la IA a la información pública).
