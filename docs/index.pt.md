# Plataforma MCP da OKFN

**Responder perguntas com dados abertos, não com palpites da IA.**

Esta é a documentação da plataforma MCP da OKFN: uma pequena família de
projetos de software livre que permite que as pessoas façam perguntas em
linguagem comum (inglês, espanhol, português...) e recebam respostas
calculadas a partir de fontes oficiais de dados abertos, com cada
resposta apontando de volta para os dados originais.

Essa frase contém os dois objetivos do projeto: respostas calculadas a
partir dos dados, o que chamamos de **precisão**, e respostas que
apontam para sua fonte, o que chamamos de **rastreabilidade**.
[O modelo aberto](overview/open-model.md) explica os dois.

Ela é construída como parte dos
[AI Learning Labs](https://okfn.org/en/projects/ai-learning-labs/mcp-open-government-data/)
da Open Knowledge Foundation.

## Assista à palestra

Apresentamos este trabalho como *IA Trazable para datos publicos: un
modelo abierto para America Latina* (IA rastreável para dados públicos:
um modelo aberto para a América Latina) no UN Big Data Regional Hub no
Brasil, organizado pela CEPAL, em junho de 2026, por Patricio Del Boca
(líder técnico) e Andres Vazquez (desenvolvedor sênior).

<div class="video">
  <iframe src="https://www.youtube-nocookie.com/embed/9QBr7kWAcdI"
          title="IA Trazable para datos publicos: un modelo abierto para America Latina"
          style="width: 100%; aspect-ratio: 16 / 9; border: 0;"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
          allowfullscreen></iframe>
</div>

A palestra cobre o desafio central (por que não dá para confiar apenas
nos LLMs com dados públicos), o modelo aberto por trás da nossa
resposta, uma demo ao vivo do caso do Uruguai e o que aprendemos. Esta
documentação é a versão escrita e estendida dessa mesma visão.

A [página do evento da CEPAL](https://rtc-cea.cepal.org/es/evento/videoconferencia-sobre-ia-trazable-para-datos-publicos-un-modelo-abierto-para-america-latina)
traz mais sobre a sessão, incluindo um PDF com os slides da
apresentação.

## Por quê

!!! tagline "A ideia central"
    Grandes modelos de linguagem são ótimos em conversar e péssimos com
    fatos. Portais de dados abertos são ótimos com fatos e péssimos em
    conversar.

Esta plataforma conecta os dois. **Não queremos que a IA saiba a
resposta, queremos que ela recupere, explique e cite os dados para a
resposta.**

Ainda não alcançamos totalmente esse objetivo, mas no caminho
construímos algo genuinamente útil, uma ferramenta que vale a pena usar
com cuidado. O que aprendemos tentando chegar lá está escrito em
[lições dos pilotos](lessons/index.md).

## O que vem na caixa

- Um **servidor MCP** que transforma datasets abertos (arquivos CSV,
  bancos de dados) em ferramentas que uma IA pode chamar.
- Um **chat gateway**, um chat web simples que conecta qualquer LLM
  compatível com OpenAI ao servidor MCP e renderiza tabelas, gráficos e
  links para as fontes direto dos dados, [sem passá-los pela
  IA](overview/idea.md).
- **Plugins** com escopo em um domínio de dados específico (o balanço
  energético do Uruguai, o Brasil, e o seu em seguida) que descrevem
  datasets e as perguntas que eles podem responder.

## Para onde ir agora

- Chegou agora? Comece por [a ideia](overview/idea.md).
- Quer executar? Vá para [primeiros passos](getting-started/index.md).
- Quer adicionar os dados do seu país? Leia [plugins](plugins/index.md).

!!! note "Fase inicial"
    A plataforma inteira está em uma fase inicial de pesquisa. Mudanças
    incompatíveis são esperadas, assim como esta documentação mudar
    debaixo dos seus pés.
