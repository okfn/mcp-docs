# Brasil

**Repo:** [okfn/mcp-dados-brasil](https://github.com/okfn/mcp-dados-brasil)
&middot; **Portal:** [dados.gov.br](https://dados.gov.br)
&middot; **Idioma:** português

Definições de datasets para o portal nacional de dados abertos do
Brasil. Cada arquivo `.yaml` em `datasets/` declara um dataset e suas
ferramentas; o repo também contém ferramentas em Python para os casos
mais elaborados.

## Direto do campo

Este catálogo sustentou um piloto com a Controladoria-Geral da União,
focado nas **emendas parlamentares**, um dos datasets mais requisitados
do portal. O objetivo era testar se os cidadãos podiam perguntar em
linguagem natural e obter respostas rastreáveis até os dados oficiais.
Veja [lições dos pilotos](../lessons/index.md).

## Adicionando um dataset

Siga o guia geral de [datasets em YAML](../plugins/yaml-datasets.md):
um novo arquivo `.yaml` em `datasets/`, push, e refazer o fetch no
servidor. As descrições, os parâmetros e as perguntas de exemplo estão
escritos em português, de acordo com o público.
