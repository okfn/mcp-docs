# Dois pilotos

A mesma arquitetura foi testada duas vezes, em dois países, com duas
instituições e dois datasets muito diferentes. Isso foi deliberado.

| | Brasil | Uruguai |
|---|---|---|
| **Parceiro** | Controladoria-Geral da União (CGU) | AGESIC |
| **Dataset central** | Emendas parlamentares, um dos datasets mais solicitados do portal nacional | Balanço Energético Nacional (BEN): importações de energia, geração, capacidade instalada |
| **Pergunta** | Os cidadãos podem perguntar em linguagem natural e obter respostas rastreáveis até os dados oficiais? | A mesma arquitetura se sustenta em outro país, contexto e ambiente de dados? |
| **Outros dados que exploramos** | Transferências do Bolsa Família por município, compras públicas federais, operadoras de planos de saúde | Compras públicas no formato [Open Contracting](https://standard.open-contracting.org/) (OCDS), estatísticas de crimes sexuais |

A linha de "outros dados" é trabalho que testamos mas não terminamos: as
ferramentas existem nos repos dos plugins, algumas desabilitadas ou em
rascunho, e não fizeram parte dos testes estruturados do piloto descritos
abaixo. Elas importam como evidência de que a mesma arquitetura se estende
a mais datasets, em particular os dados de compras públicas dos dois
lados.

## Por que dois

Um piloto prova que um protótipo pode ser construído. Dois pilotos começam
a mostrar se a abordagem é portável: se a mesma arquitetura baseada em
MCP sobrevive a datasets diferentes, instituições diferentes e
necessidades de usuários diferentes.

Essa portabilidade é todo o sentido de chamar isto de
[modelo aberto](../overview/open-model.md) em vez de produto. Se
só funcionasse com o balanço energético, seria uma ferramenta de energia.

## Como testamos

- **13 testadores** no total.
- Testadores de **dentro dos governos dos pilotos**, que conhecem os dados e
  o contexto institucional.
- Testadores de **organizações da sociedade civil**, atuando como
  validadores externos, sem o conhecimento interno que faz uma resposta
  parecer certa.
- Os testadores fizeram suas próprias perguntas e registraram o feedback em
  logs.
- Os logs foram então analisados em busca de precisão, padrões de
  problemas recorrentes e sinais de usabilidade.
- O piloto rodou em **etapas curtas**, mostrando progresso e incorporando
  feedback a cada passo. Um parceiro do piloto depois apontou esse ritmo como
  uma das coisas que funcionaram.

## O que nos propusemos a aprender

**Respostas precisas e verificáveis.** O sistema retorna respostas
corretas? Os usuários conseguem checá-las contra a fonte? Fica claro de
onde veio a informação?

**Comportamento em conversas mais longas.** A qualidade se mantém ao longo
de cinco a dez perguntas de acompanhamento, ou perda de contexto,
contradições e interpretações sem respaldo vão se infiltrando? Esta é uma
pergunta genuinamente aberta: a maioria dos testes acontece naturalmente
uma pergunta por vez, e a degradação em múltiplos turnos é mais difícil de
notar e mais difícil de medir. Ainda não temos uma resposta confiante.

**Usabilidade e adoção.** A interface é intuitiva para pessoas que
não são técnicas nem especialistas de domínio?

!!! note "A maior parte dos detalhes aqui vem do Uruguai"
    As páginas a seguir se baseiam principalmente no piloto do Uruguai, que
    produziu o feedback estruturado mais detalhado. O relatório
    consolidado entre pilotos ainda está sendo escrito, e esta seção vai
    crescer à medida que os achados do Brasil e as sessões de reflexão
    com os parceiros forem incorporados.
