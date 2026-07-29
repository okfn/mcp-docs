# O trade-off do YAML

Declarar datasets em YAML em vez de escrever Python parece uma ótima
ideia: nada de código, só um arquivo arrumado por dataset. Funciona, e para um
dataset genuinamente simples é rápido e agradável. Mas é uma boa ideia para
usar com cuidado, e acabamos usando muito menos YAML do que esperávamos.

## Por que

Um formato YAML declarativo é, no fim das contas, uma **nova linguagem de
consulta**. Para expressar uma pergunta real você precisa de engines, filtros,
formatadores, templates de resposta e regras de como eles se combinam. Cada
capacidade que um dataset real pede (um novo tipo de filtro, um join, uma
coluna calculada, um formato especial) tem que ser adicionada a essa linguagem
e depois aprendida por quem escreve o YAML.

Então a aparente simplicidade se move em vez de desaparecer. Em vez de
escrever umas poucas linhas de Python que qualquer desenvolvedor Python
consegue ler, você escreve YAML em um dialeto sob medida que só este projeto
entende, e quando ele não estica o suficiente você fica travado.

## Nossa regra prática

- Um **dataset realmente simples**, um CSV puro com perguntas óbvias de
  agregação ou top-N? YAML está bem e é rápido.
- **Qualquer coisa além disso?** Vá de [ferramenta
  Python](../plugins/python-tools.md). É mais clara, mais poderosa e
  usa uma linguagem que as pessoas já conhecem em vez de uma que inventamos.

Nada disso torna o YAML errado. Torna-o uma ferramenta afiada para um
trabalho estreito. Use-o para os casos simples, e não tente fazê-lo crescer
até virar uma linguagem de consulta geral, porque essa é uma linguagem que
você teria então que manter.
