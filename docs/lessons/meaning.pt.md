# Conectar os dados é a parte fácil

A lição principal dos dois pilotos: **dar ao modelo acesso a
dados oficiais não foi a parte difícil.**

A camada MCP faz esse trabalho, e faz de forma confiável. Aponte o servidor
para um dataset, descreva as ferramentas, e o modelo pode ler números reais
em vez de lembrá-los.

Mas acesso não é compreensão. Um modelo que pode ler uma coluna de
números ainda não sabe:

- O que os termos realmente significam, no sentido oficial.
- Em que unidades estão os valores.
- Que período de tempo uma cifra cobre, e se os períodos são comparáveis.
- O que o dataset deixa de fora deliberadamente.
- Que suposições foram feitas quando os dados foram compilados.

Esses não são detalhes de apoio que você pode adicionar depois para dar
acabamento. **Eles decidem se uma resposta está correta.** Um número certo
sob um rótulo errado é uma resposta errada.

## O que isso significa na prática

A maior parte do trabalho real de construir um plugin não é encanamento, é
explicar os dados para a máquina:

- Escrever um [glossário de domínio](glossary.md) e injetar as definições
  oficiais no contexto das ferramentas, para que o modelo as tenha ao
  compor cada resposta.
- Escrever descrições de ferramentas e parâmetros que declarem unidades e
  períodos explicitamente, em vez de assumir que são óbvios.
- Ser explícito sobre os limites de um dataset, para que o modelo possa dizer
  "não está nos dados" em vez de forçar uma resposta.
- Manter os plugins [com escopo restrito a um domínio que alguém realmente
  entende](scope.md), porque ninguém consegue escrever boas descrições para
  um portal com o qual não trabalhou.

É também por isso que [a qualidade dos metadados importa tanto quanto a
qualidade dos dados](data-quality.md). Reserve orçamento para o significado,
não só para a conexão.
