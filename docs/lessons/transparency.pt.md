# Transparência e confiança

Vários testadores, de forma independente, relataram a mesma coisa: o modelo
mistura seu **conhecimento geral** com os **dados concretos** dos datasets,
sem dizer o que é o quê. Foi o padrão negativo mais repetido.

## O que mudamos

Atualizamos o system prompt para pedir ao modelo que sempre distinga o que
vem dos datasets do que vem do seu conhecimento geral ou das suas
próprias deduções. Isso mitiga o problema mas não elimina a necessidade
de o usuário checar.

## O que dizer aos usuários

O hábito mais útil é perguntar de novo:

> "Tudo o que você acabou de me dizer está respaldado pelos dados que você
> leu, ou pelo seu treinamento?"

Em geral a IA é honesta aqui. Ela diferencia melhor suas fontes
quando perguntada diretamente, e muitas vezes se retrata quando percebe
que misturou um fato geral em uma resposta de dados e errou em alguma
coisa.

## Rastreabilidade é necessária, mas não suficiente

Um link para a fonte permite ao usuário verificar um número. Ele não impede
o sistema de embrulhar esse número em uma interpretação que a fonte nunca
sustentou.

Em um exemplo dos pilotos, o sistema explicou uma mudança se referindo a
**"fatores climáticos"**, embora o dataset não contivesse nenhum dado
climático. O número estava certo e o link estava certo. A explicação
em volta era inventada, e soava totalmente plausível.

O link prova de onde vieram os *dados*. Ele não diz nada sobre de onde
veio o *raciocínio*. O leitor ainda precisa perceber quando uma resposta
afirma uma causa que nenhum dataset conectado poderia conhecer.

## Confiança não acompanha evidência

O **tom de confiança do modelo não muda com a qualidade da
sua evidência**. Ele responde com a mesma segurança tendo ou não
de fato os dados. Os usuários não podem usar a confiança como sinal de
confiabilidade, e é exatamente por isso que perguntar de novo e verificar
importam.
