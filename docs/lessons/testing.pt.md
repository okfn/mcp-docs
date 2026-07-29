# Testar não é simples

Garantir que as respostas estejam realmente corretas acabou sendo uma
das partes mais difíceis do trabalho, e é fácil subestimá-la.

Verificar a qualidade da informação exige **tempo** e **conhecimento do
domínio**. Você não consegue conferir se uma resposta sobre a matriz
energética está certa sem entender a matriz energética. Isso coloca o
peso sobre especialistas de domínio escassos, não sobre quem por acaso
estiver construindo o software.

Também nem sempre é fácil dar feedback manualmente. Um testador percebe
que algo parece errado, mas identificar exatamente qual ferramenta, qual
dataset e qual suposição produziu o número errado exige um trabalho
paciente. Respostas rastreáveis ajudam aqui: um testador pode seguir um
número até a sua fonte em vez de adivinhar.

## A revisão humana não é uma fase, é um requisito

Os pilotos não revelaram uma forma de contornar isso. **Pessoas que
entendem os dados são necessárias para detectar afirmações plausíveis
mas sem sustentação**, e essa necessidade não desaparece à medida que o
sistema melhora. As falhas que importam não são as óbvias; são as
respostas que parecem certas para todos, exceto para a pessoa que
conhece o dataset.

Planeje uma revisão humana contínua, não um marco de revisão que se
cumpre uma única vez. Isso só é realista se os especialistas de domínio
estiverem [a bordo desde o primeiro dia](partners.md); em um dos
pilotos, validar e polir as respostas foi a parte do trabalho que mais
tempo consumiu.

## Perguntas reais de usuários vencem as inventadas

Os testes mais úteis vieram de perguntas que as pessoas realmente fazem.
Os parceiros do piloto nos entregaram suas perguntas frequentes, e elas
viraram casos de teste diretamente.

Isso funcionou melhor do que os casos de teste que nós mesmos
escrevemos, de duas maneiras: as perguntas reais expuseram onde as
**descrições das ferramentas** estavam pouco claras ou enganosas, e
mostraram onde o sistema precisava de **limites mais fortes**, lugares
em que respondia quando deveria ter recusado.

Se você for rodar um piloto, peça à instituição parceira o FAQ dela
antes de escrever um único teste.

## Quem testa importa

Misturar testadores de dentro do governo parceiro com testadores da
sociedade civil foi útil exatamente porque eles falham de formas
diferentes. Os de dentro pegam números errados. Os de fora pegam
respostas tecnicamente corretas mas incompreensíveis, ou que assumem em
silêncio um conhecimento que eles não têm. Veja
[dois pilotos](two-pilots.md).

Reserve tempo real e conhecimento real para os testes. Não é uma
formalidade que dá para apressar no final. Uma equipe de piloto disse
exatamente isso em retrospecto: dada a importância dos testes e a
[complexidade do seu dataset](start-simple.md), teria alocado mais tempo
para essa etapa.
