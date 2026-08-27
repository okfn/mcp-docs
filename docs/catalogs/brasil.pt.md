# Implementação do Brasil

**Repo:** [okfn/mcp-dados-brasil](https://github.com/okfn/mcp-dados-brasil)
&middot; **Fonte:** [portaldatransparencia.gov.br](https://portaldatransparencia.gov.br)
&middot; **Idioma:** português

Ferramentas MCP sobre as *emendas parlamentares* do Brasil, publicadas
pela Controladoria-Geral da União (CGU) no Portal da Transparência.
Todas as ferramentas são
[ferramentas em Python](../plugins/python-tools.md); o plugin não
declara datasets em YAML.

## Destaques

O plugin expõe ferramentas para consultar emendas por localidade,
autor, função e subfunção de governo, ação orçamentária e tipo de
emenda, além de rankings dos principais favorecidos e dos principais
autores, e um [glossário](../plugins/glossaries.md) com as definições
oficiais do dicionário de dados do portal (para que o modelo nunca
confunda os valores *empenhado*, *liquidado* e *pago*).

## Como funciona

O pacote inclui o dataset de emendas (arquivos CSV do serviço de
download do Portal da Transparência) e um script `load-emendas-db` que
os carrega em um banco SQLite local. Cada ferramenta executa uma
consulta SQL sobre esse banco com pandas e devolve tabelas e gráficos
seguindo o contrato padrão de
[resultados das ferramentas](../plugins/tool-results.md).

## Instalação

É um pacote Python instalável com pip, registrado através do entry
point `mcp_server`. Instale-o no ambiente do servidor MCP, execute
`load-emendas-db` uma vez para construir o banco local e reinicie o
servidor. As descrições, os parâmetros e as perguntas de exemplo são
escritos em português, de acordo com o público.

## Do campo

Este catálogo apoiou um piloto com a Controladoria-Geral da União do
Brasil, focado nas **emendas parlamentares**, um dos datasets mais
solicitados do portal. O objetivo era testar se os cidadãos podiam
perguntar em linguagem natural e obter respostas rastreáveis até os
dados oficiais. As conclusões estão documentadas no *Field Guide to
Connecting AI to Public Information*.
