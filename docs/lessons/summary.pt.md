# Pontos fortes e fracos

## A conclusão principal

O sistema é bastante **determinístico quando perguntado sobre algo muito
específico**, como "qual foi o valor X no ano Y?". À medida que as
perguntas ficam mais abertas, as respostas divergem mais. Os usuários
devem ter isso em mente o tempo todo: **perguntar de novo e verificar.**
Essas ferramentas devem ser usadas com cuidado.

## Pontos fortes

- **Preciso em consultas específicas.** Quando uma pergunta aponta para
  um valor que existe em um dataset, o comportamento é quase
  determinístico.
- **Honesto sobre os limites dos dados.** Em geral, diz claramente
  quando algo não está no dataset, em vez de inventar.
- **Recupera-se bem de correções.** Quando um usuário pergunta de novo
  ou aponta um erro, ele recalcula, admite e corrige a resposta.
- **O glossário ajuda.** As definições oficiais do dataset, tanto
  consultáveis quanto
  [injetadas no contexto das ferramentas](glossary.md), melhoram as
  respostas e ajudam os não especialistas.
- **Tabelas e gráficos de autoria humana** ao lado da resposta da IA são
  muito valorizados e são a garantia de precisão.
- **Utilidade real e concreta.** Os usuários o colocaram para trabalhar
  de verdade, por exemplo melhorando um artigo da Wikipédia.
- **Impulsiona os dados abertos.** O piloto revela quais datasets estão
  faltando e exige boa documentação.
- **Transfere capacidade.** Os técnicos dos parceiros aprenderam a
  abordagem bem o suficiente para construir seu próprio servidor MCP,
  sem que ninguém pedisse. Veja
  [o que ficou depois do piloto](ripple-effects.md).
- **Simples de operar.** Sem contas, sem banco de dados.

## Pontos fracos

- **Cálculos derivados não são garantidos.** Percentuais e variações ano
  a ano foram os únicos casos em que números errados foram apresentados
  como dados. Veja
  [confiabilidade dos cálculos](calculations.md).
- **Mistura conhecimento do modelo com dados do dataset** sem sinalizar.
  Mitigado por uma [mudança no system prompt](transparency.md), mas
  ainda precisa de verificação do usuário.
- **Tom confiante independentemente da evidência.** Soa igualmente
  seguro com ou sem dados.
- **Tabelas e gráficos repetidos ou desnecessários.** Mitigado
  [minimizando-os por padrão](presentation.md).
- **Sem conversas salvas ou compartilhadas** na ausência de contas, e
  sem download em um clique de uma resposta completa.
- **A cobertura depende dos datasets conectados.** Perguntas mais
  profundas ficam sem resposta até que mais
  [dados sejam abertos e conectados](data-quality.md).
- **Perguntas abertas divergem** e precisam de verificação do usuário.
