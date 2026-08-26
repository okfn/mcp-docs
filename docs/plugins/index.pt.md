# Construir plugins e datasets

Um plugin é um repo git que ensina ao servidor MCP sobre um conjunto de
datasets. Limitamos cada plugin a um **domínio de dados focado** (por
exemplo o balanço energético do Uruguai) em vez de a um portal de dados
abertos inteiro, que tende a ficar genérico demais. Os catálogos de
energia do Uruguai e do Brasil são plugins; o seu também pode ser.

Um plugin pode descrever suas ferramentas de duas maneiras, e misturar
as duas livremente:

- [**Ferramentas em Python**](python-tools.md): funções Python comuns.
  Este é o caminho principal, e o que usamos na prática: dá conta de
  tudo, de uma consulta simples a bancos de dados, APIs e cálculos, e
  continua claro à medida que um dataset cresce.
- [**Datasets em YAML**](yaml-datasets.md): declare uma consulta em um
  pequeno arquivo `.yaml`, sem precisar programar. Só para datasets
  realmente simples: veja [quando usar YAML vs.
  Python](yaml-datasets.md#when-to-use-yaml-vs-python).

Preferimos funções Python como ferramentas para começar.
Seja qual for o estilo, toda ferramenta deve seguir o mesmo
[contrato de resultados](tool-results.md): uma resposta em texto para a
IA mais dados estruturados (fontes, tabelas, gráficos) para a UI.

## O caminho até o seu próprio plugin

1. Comece pelos catálogos existentes como modelos:
   [o plugin de energia do Uruguai](../catalogs/uruguay.md) (Python).
2. Escreva sua primeira ferramenta como uma [função
   Python](python-tools.md).
3. Teste localmente com o [MCP Inspector](../getting-started/inspector.md).
4. [Dê ao seu plugin uma descrição e perguntas de
   exemplo](plugin-info.md) para que o chat mostre um belo cartão de
   apresentação.
5. [Conecte-o a um servidor](connect.md).

!!! tip "Duas lições dos pilotos"
    Duas práticas se mostraram especialmente valiosas na hora de
    construir um plugin: [pré-calcular os valores derivados em vez de
    pedir à
    IA](python-tools.md#precompute-derived-values-do-not-ask-the-ai-to),
    e [dar à IA um glossário de domínio](glossaries.md) injetando
    definições oficiais no contexto das suas ferramentas.
