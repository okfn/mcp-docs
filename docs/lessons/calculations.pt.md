# Confiabilidade dos cálculos

Esta é a única área onde os testadores relataram respostas
**numericamente erradas mas apresentadas como dados**. Consultas
diretas ("qual foi o valor X no ano Y?") foram confiáveis. Cálculos
derivados não.

A pergunta arriscada parece simples: "me dê uma tabela com os percentuais
de X". O problema é que X pode ir de um número simples até algo que
agrega vários outros números, e o modelo não tem nenhuma garantia de
acertar a aritmética.

## Como mitigar

A correção confiável é não pedir para o modelo fazer as contas. Pré-calcule
o valor derivado com [Python e pandas](../plugins/python-tools.md) para que
ele vire uma coluna real do dataset, e documente essa coluna. Então a
ferramenta só a lê.

- **Casos simples** (um percentual direto de um dataset): adicione o
  percentual como uma coluna nova com pandas. Documente o que significa.
- **Casos complexos** (um percentual que cruza várias colunas ou
  datasets): pré-calcule, de novo com pandas, o percentual que as pessoas
  realmente costumam perguntar, por exemplo "qual parcela foi renovável no
  ano X?".
- **Casos difíceis e muito específicos** ("quanto X cresceu entre o ano Y1
  e o ano Y2?"): específicos demais para pré-calcular para cada par. Uma
  ferramenta que atue como uma pequena calculadora pode ajudar aqui.
  Ainda não testamos isso.

## A conclusão

Trate qualquer percentual ou variação ano a ano calculada na hora como
suspeita até que uma ferramenta a compute a partir de uma coluna
documentada. Se um número importa, ele deve vir dos dados, não da cabeça
do modelo.
