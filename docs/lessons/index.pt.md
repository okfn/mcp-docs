# Lições dos pilotos

Testamos a mesma arquitetura em **dois pilotos governamentais**, no Brasil
e no Uruguai: veja [dois pilotos](two-pilots.md) para saber quem, como e o que
nos propusemos a aprender. O piloto do Uruguai, que rodou publicamente em
[mcp-uruguay.okfn.org](https://mcp-uruguay.okfn.org/), produziu o feedback
mais detalhado, então a maioria dos exemplos concretos vem de lá.

Esta seção foi escrita para qualquer pessoa construindo ou operando uma
implantação similar: o que funcionou, o que não funcionou e o que mudamos ao
longo do caminho.

!!! note "Leia isto como notas de campo, não como um veredicto"
    O feedback chegou enquanto ainda estávamos implantando versões novas,
    então não é estritamente feedback sobre um produto acabado. Vários dos
    problemas descritos aqui já estavam corrigidos por mudanças publicadas
    durante o piloto. Quando esse é o caso, a página diz isso.

## A versão curta

A experiência geral foi positiva. Quando perguntamos aos parceiros
o que diriam a outro governo considerando uma abordagem similar,
a resposta deles começou, literalmente, com "Façam!". O padrão que os usuários
mais valorizaram foi
a combinação de **tabelas e gráficos de autoria humana injetados ao lado da
resposta final da IA**: a prosa vem do modelo, mas os números
e suas fontes vêm direto dos dados. Quanto mais especialista o usuário
e quanto melhor conhecia os datasets, mais pequenas coisas encontrava
para melhorar, que é exatamente o tipo de feedback que queríamos.

Um exemplo concreto de impacto: wikimedistas usaram a ferramenta para melhorar
o artigo da Wikipédia sobre energia solar no Uruguai. É um ótimo caso de uso,
e um lembrete de que uma ferramenta tão fluente também poderia ser mal usada
com a melhor das intenções, então a verificação importa.

## O que aprendemos, por tema

- [Dois pilotos](two-pilots.md): com quem testamos, como, e
  o que nos propusemos a aprender.
- [Conectar os dados é a parte fácil](meaning.md): acesso não é
  compreensão, e o significado é onde está o trabalho.
- [Plugins com escopo restrito](scope.md): por que dividimos o amplo
  repo do Uruguai em um repo focado, específico de um domínio.
- [Especialistas de domínio desde o primeiro dia](partners.md): quando os
  donos dos dados precisam chegar, e como escolher a equipe parceira.
- [Comece com um dataset simples](start-simple.md): estabeleça a
  abordagem em dados fáceis antes de subir para dados complexos.
- [O trade-off do YAML](yaml-tradeoff.md): por que declarar datasets em YAML
  é uma boa ideia só para casos realmente simples.
- [Confiabilidade dos cálculos](calculations.md): por onde números
  errados podem se infiltrar, e como prevenir isso.
- [Transparência e confiança](transparency.md): o modelo misturando seu próprio
  conhecimento com os dados, e por que você deveria sempre perguntar de novo.
- [Qualidade e abertura dos dados](data-quality.md): o piloto como
  incentivo para abrir dados bem documentados.
- [Ferramentas novas, problemas antigos](data-access.md): as perguntas de
  governança de dados que conectar IA não deixa você pular.
- [Testar não é simples](testing.md): por que checar respostas leva tempo
  e conhecimento de domínio.
- [Um glossário de domínio](glossary.md): definições oficiais, injetadas no
  contexto das ferramentas.
- [Recursos de dados abertos](resources.md): apontar os usuários para os
  dados brutos além da nossa ferramenta.
- [Tabelas e gráficos](presentation.md): demais, e o que fizemos a
  respeito.
- [Sem contas, sem banco de dados](no-database.md): o custo e o benefício de
  se manter simples.
- [O que ficou depois do piloto](ripple-effects.md): as capacidades
  que o piloto deixou no governo parceiro.
- [Pontos fortes e fracos](summary.md): o balanço
  consolidado.
