# Especialistas de domínio desde o primeiro dia

Rodar a mesma arquitetura duas vezes nos deu uma comparação limpa. Em um
piloto, os especialistas da equipe dona dos dados estiveram envolvidos
desde o comecinho. No outro, entraram mais tarde, e tudo demorou mais.
Mesma arquitetura, mesmo processo, escalação inicial diferente, e a
diferença foi visível.

A lição, nas palavras do próprio parceiro: ter o especialista de domínio
disponível e envolvido **desde o início**. Os donos dos dados não podem
chegar no final.

[Plugins com escopo restrito](scope.md) argumenta *quem* deveria estar por
trás de um plugin: alguém que entende profundamente um domínio. Esta página
é sobre *quando*. Essa pessoa precisa estar na sala antes de a primeira
ferramenta ser escrita, porque a maior parte do trabalho é [explicar os
dados para a máquina](meaning.md) e [checar as respostas](testing.md), e
as duas coisas precisam do especialista, não do programador.

## Escolhendo a equipe parceira

Escolher qual instituição e qual equipe hospeda um piloto é uma decisão, não
um padrão automático. O que a experiência do piloto sugere:

- **Escolha a melhor equipe, não a mais próxima.** A qualidade do
  plugin tem como teto o quanto a equipe por trás dos dados os conhece.
- **Escolha uma equipe que tenha tempo.** Um parceiro sem tempo pode deixar
  o piloto pendurado no meio do caminho, sem ninguém disponível para validar
  respostas ou melhorar descrições.
- **Apoio da alta gestão importa.** O tempo só se materializa quando
  a liderança da equipe trata o piloto como trabalho de verdade, não como
  um favor.

Só comece quando o tempo e o apoio institucional estiverem
realmente lá. Se não estiverem, espere ou escolha outro parceiro; um piloto
que trava meio validado é pior do que um que começa mais tarde.

O apoio não é necessário só para começar. Continuar depois do piloto
significa que o trabalho precisa conquistar um lugar no backlog de
desenvolvimento da própria organização, e isso exige construir apoio entre
as outras equipes internas de dados, não só a que hospedou o piloto.

## A equipe técnica interna também

Especialistas de domínio não são as únicas pessoas a trazer cedo. Os
técnicos de um dos pilotos trabalharam com a mão na massa desde o início,
lendo os repos e rodando o servidor eles mesmos, e depois do piloto foram
[construir seu próprio servidor MCP](ripple-effects.md). A outra equipe, em
retrospecto, teria envolvido sua equipe técnica interna mais
ativamente: trabalhando ao lado da equipe do projeto e replicando partes do
processo com as mesmas ferramentas e metodologia.

As duas experiências apontam para a mesma lição. A documentação apoia a
replicação futura, mas o envolvimento prático é o que transfere
conhecimento e constrói apropriação interna. Uma equipe que só lê sobre
o piloto herda um relatório; uma equipe que trabalha dentro dele herda uma
capacidade.

## A carga de trabalho é real, e vale a pena

Seja honesto com o parceiro desde o começo: hospedar um piloto é trabalho
extra para a equipe dona dos dados, em cima das suas tarefas normais.
Validação e polimento, não encanamento, é para onde vai a maior parte desse
tempo.

Compensa. Ao final do piloto a equipe dona dos dados estava motivada por
ver seus dados usados dessa forma, e considerou o resultado digno do
esforço: uma ferramenta nova e própria para continuar polindo e
eventualmente publicar, com avisos claros sobre suas limitações.
