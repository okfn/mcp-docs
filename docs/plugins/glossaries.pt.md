# Implementar glossários de domínio

Datasets públicos muitas vezes dependem de termos administrativos
específicos do domínio, taxonomia legal ou unidades especializadas
(como as cifras do balanço energético ou códigos orçamentários) que
não especialistas, e LLMs genéricos, podem interpretar mal.

Para garantir respostas precisas, os plugins devem incluir um
**glossário de domínio** que injete as definições oficiais dos termos
diretamente no contexto das ferramentas. No piloto do Uruguai, injetar
as definições oficiais do balanço energético (BEN) se mostrou
essencial para os usuários não especialistas, e melhorou as respostas
de forma mensurável.

## Como funciona a injeção do glossário

As definições do glossário cumprem um propósito duplo na arquitetura
MCP:

1. **Injeção no contexto do LLM.** Os termos e definições são
   incluídos no system prompt ou na descrição da ferramenta. Quando o
   LLM recebe os resultados dos dados, ele usa essas definições para
   interpretar as cifras brutas e escrever uma prosa precisa.
2. **Clareza para o usuário.** Os termos podem ser expostos
   diretamente na interface para que os usuários consultem as
   definições oficiais junto com os resultados da sua consulta.

## Diretrizes de implementação

- **Mapeie os termos para ferramentas específicas.** Evite despejar o
  dicionário inteiro de um portal em todos os prompts. Faça uma
  curadoria manual e anexe apenas os termos relevantes à ferramenta
  específica que os usa. Isso economiza espaço na janela de contexto e
  evita confusão no prompt. O mapeamento é manual e um pouco tedioso,
  mas a recompensa, respostas mais claras e menos mal-entendidos, faz
  o esforço valer a pena.
- **Faça a ponte entre a linguagem cotidiana e os termos
  burocráticos.** Inclua mapeamentos de sinônimos nas descrições das
  suas ferramentas, por exemplo mapeando termos informais dos usuários
  como "pix" ou "imposto sobre combustíveis" para os nomes oficiais
  das categorias administrativas no dataset. Sem essa ponte, a IA pode
  reportar que os dados não existem simplesmente porque o usuário não
  conhecia a expressão burocrática exata.
- **Trate os glossários como código.** Reserve tempo de
  desenvolvimento para o mapeamento do glossário durante a criação do
  plugin. Definir a terminologia é um requisito técnico central para a
  precisão da recuperação, não um polimento de documentação
  pós-lançamento.
