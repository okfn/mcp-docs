# O desafio

A pergunta que deu origem ao projeto:

> Como podemos levar a IA mais recente (os grandes modelos de
> linguagem) aos portais de dados abertos **sem comprometer a confiança
> na informação pública**?

É mais difícil do que parece, porque usar um LLM sozinho esbarra em
vários problemas ao mesmo tempo.

## LLMs não são feitos para dizer a verdade

A saída deles é uma estimativa. Vieses, lacunas nos dados de
treinamento e limites de arquitetura fazem com que uma resposta fluente
não seja necessariamente uma resposta correta. Precisão não é algo que
vem de graça.

## Você não consegue ver por que eles respondem o que respondem

Mesmo quando um modelo mostra seu "raciocínio", isso não resolve o
problema: apenas passa para o cidadão o trabalho de checar a verdade. E
como os modelos são não determinísticos, a mesma pergunta pode produzir
uma cadeia de raciocínio diferente a cada vez.

## Eles são pouco confiáveis nas partes mecânicas

LLMs não são bons em escrever SQL correto contra bancos de dados reais
e, de modo geral, não são a "inteligência" que o marketing sugere.
Nosso design se apoia nesse fato em vez de lutar contra ele: o modelo
nunca escreve a consulta. Ele escolhe entre
[ferramentas](../plugins/index.md) predefinidas que executam consultas
verificadas, então o trabalho com os dados é feito por código, não
adivinhado pelo modelo.

## Eles não vão dizer "não sei"

Alguns modelos são agressivamente prestativos: diante de uma pergunta,
torturam os dados que estiverem à mão até que rendam uma resposta que
pareça satisfazê-la. Não saber dizer "não tenho isso" é, por si só, uma
fonte de respostas erradas.

## Nossa resposta

Não tentamos tornar o LLM confiável por conta própria. Nós o colocamos
atrás de uma camada de ferramentas sobre dados reais, mirando duas
coisas que o modelo não pode garantir sozinho: [precisão e
rastreabilidade](open-model.md). O modelo cuida da linguagem; os dados
cuidam dos fatos.
