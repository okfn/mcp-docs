# Comece com um dataset simples

O conselho mais claro que uma equipe do piloto ofereceu na sua sessão de
reflexão: se fizessem de novo, começariam com um dataset mais
simples.

Um dos pilotos rodou sobre um dataset particularmente desafiador. A
abordagem se sustentou bem nessas condições, e isso foi um teste de estresse
valioso: mostrou que a arquitetura não depende de os dados serem
fáceis. Mas o preço foi real. Produzir respostas confiáveis exigiu
consideravelmente mais adaptação, ajuste fino e ferramentas de apoio do que
o esperado, dependeu fortemente da [contribuição dos
especialistas](partners.md), e a complexidade dos dados multiplicou o custo
de [testes e validação](testing.md).

## O conselho

Estabeleça a abordagem em dados simples primeiro, depois suba.

- **Primeiro dataset: simples.** Faça o método inteiro funcionar de ponta a
  ponta em dados fáceis de explicar: as ferramentas, as descrições, o
  [glossário](glossary.md), o ciclo de testes. Cada problema que você
  encontrar será um problema do método, não dos dados.
- **Dataset difícil em segundo.** Uma vez estabelecido o método, um dataset
  complexo vira um teste de estresse que você escolhe, não um risco que
  você descobre no meio do piloto.

Isso se combina com [plugins com escopo restrito](scope.md): um domínio
restrito e um primeiro dataset simples são o mesmo instinto aplicado duas
vezes. Reduza o que você precisa explicar para a máquina até conseguir
explicar bem.
