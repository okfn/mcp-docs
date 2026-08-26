# Documentação Técnica MCP

Bem-vindo à Documentação Técnica MCP: um guia prático para conectar
dados públicos abertos a modelos de IA usando o Model Context Protocol
(MCP).

Este manual fornece as especificações de arquitetura, os padrões de
código e os templates de configuração necessários para construir
plugins, executar o servidor e implantar ferramentas de dados.

Tudo aqui é medido contra dois objetivos: **precisão** (respostas
calculadas a partir de dados oficiais, não lembradas do treinamento) e
**rastreabilidade** (cada resposta aponta de volta para sua fonte). O
[contexto do projeto](introduction/context.md) explica os dois e por
que eles importam para dados públicos.

**Procurando contexto não técnico ou a estratégia do projeto?**
Confira o *Field Guide to Connecting AI to Public Information* (guia de
campo para conectar a IA à informação pública). Ele cobre lições dos
nossos pilotos no Brasil e no Uruguai, orientações para trabalhar com
especialistas de domínio e feedback de usuários reais.

Para mais informações, visite a página oficial do projeto
"Traceable AI Answers for Public Data" no
[site da Open Knowledge Foundation (OKFN)](https://okfn.org/en/projects/ai-learning-labs/mcp-open-government-data/).

## Assista à palestra {#watch-the-talk}

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

## O que vem na caixa

- Um **servidor MCP** que transforma datasets abertos (arquivos CSV,
  bancos de dados) em ferramentas que uma IA pode chamar.
- Um **chat gateway**, um chat web simples que conecta qualquer LLM
  compatível com OpenAI ao servidor MCP e renderiza tabelas, gráficos e
  links para as fontes direto dos dados, [sem passá-los pela
  IA](dev/architecture.md).
- **Plugins** com escopo em um domínio de dados específico (o balanço
  energético do Uruguai, o Brasil, e o seu em seguida) que descrevem
  datasets e as perguntas que eles podem responder.

## Para onde ir agora

- Chegou agora? Comece pelo [contexto do projeto](introduction/context.md).
- Quer executar? Vá para [primeiros passos](getting-started/index.md).
- Quer adicionar os dados do seu país? Leia [plugins](plugins/index.md).

!!! note "Fase inicial"
    A plataforma inteira está em uma fase inicial de pesquisa. Mudanças
    incompatíveis são esperadas, assim como esta documentação mudar
    debaixo dos seus pés.
