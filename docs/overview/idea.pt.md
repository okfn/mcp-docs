# A ideia

Governos e organizações publicam quantidades enormes de dados abertos:
orçamentos, compras públicas, preços, estatísticas de saúde.
Pouquíssimas pessoas os usam, porque usá-los exige baixar arquivos,
entender esquemas e escrever código.

Ao mesmo tempo, as pessoas já fazem essas perguntas a chatbots de IA, e
os chatbots respondem de memória: desatualizados, não verificáveis, às
vezes inventados.

## Nossa resposta

Colocamos uma camada entre a IA e o usuário:

1. O usuário faz uma pergunta no seu próprio idioma.
2. Em vez de responder de memória, a IA é direcionada a chamar uma
   **ferramenta**: uma operação pequena e nomeada, como "preço médio de
   um produto por ano", apoiada em um dataset real.
3. A ferramenta calcula a resposta a partir dos dados e a devolve junto
   com a **fonte**: um link para o dataset original.
4. O chat mostra a resposta escrita pela IA, mais tabelas, gráficos e
   as fontes, para que qualquer pessoa possa verificá-la.

!!! important "Tabelas e gráficos vêm do código, não da IA"
    Uma ferramenta devolve duas coisas: um texto curto para a IA ler e
    um payload estruturado (tabelas, gráficos, fontes) para a
    interface. Só o texto chega ao modelo. **As tabelas e os gráficos
    são construídos por funções de ferramenta escritas por humanos e
    renderizados diretamente pela interface, sem passar pela IA em
    momento algum.** A IA escreve a prosa; os dados falam por si ao
    lado dela.

As tabelas verificáveis e os links das fontes ao lado das palavras dela
não são um extra agradável; são a salvaguarda. Veja [lições dos
pilotos](../lessons/index.md).

O raciocínio mais profundo sobre por que um LLM sozinho não basta está
na página [o desafio](challenges.md).

## Princípios

- **Precisão e rastreabilidade.** As respostas devem ser corretas,
  calculadas a partir dos dados, e cada resposta deve apontar para sua
  fonte. O servidor [garante isso no
  código](../plugins/tool-results.md#como-isso-e-garantido).
- **Código simples em vez de uma linguagem sob medida.** As
  ferramentas são, na maior parte, pequenas funções Python. Datasets
  realmente simples podem, em vez disso, ser declarados em YAML sem
  código, mas reservamos isso para os casos simples: veja [o trade-off
  do YAML](../lessons/yaml-tradeoff.md).
- **Software livre, tecnologia entediante.** Python, CSV, SQLite, HTML
  e JS puros. Tudo pode rodar em um laptop.
- **Propriedade local.** Cada comunidade ou equipe de domínio mantém
  seu próprio repositório de plugin, no seu próprio idioma, no seu
  próprio ritmo.

## O padrão por baixo

A conexão entre a IA e as ferramentas usa o
[Model Context Protocol](https://modelcontextprotocol.io/) (MCP), um
padrão aberto. Isso significa que nosso servidor funciona não só com
nosso chat gateway, mas com qualquer cliente compatível com MCP (Claude
Desktop, VS Code, MCP Inspector e outros).
