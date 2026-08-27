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
