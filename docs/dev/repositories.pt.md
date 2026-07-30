# Repositórios

A plataforma é um espaço de trabalho de repos git pequenos e
independentes, em vez de um grande monorepo. Cada repo tem seus próprios
testes, seu próprio README e seu próprio ritmo de releases.

## Núcleo

| Repo | O que é |
|------|------------|
| [mcp-server](https://github.com/okfn/mcp-server) | O servidor MCP. Carrega ferramentas de módulos Python, plugins instalados e arquivos YAML, e as serve por stdio ou HTTP. |
| [mcp-chat-gateway](https://github.com/okfn/mcp-chat-gateway) | O chat web. Flask simples + HTML/JS, sem framework de frontend. Conecta um LLM ao servidor MCP e renderiza tabelas, gráficos e fontes. |

## Plugins de dados

| Repo | O que é |
|------|------------|
| [mcp-datos-uruguay-ben](https://github.com/okfn/mcp-datos-uruguay-ben) | Ferramentas sobre o balanço energético nacional do Uruguai (BEN), de catalogodatos.gub.uy. Em espanhol. |
| [mcp-dados-brasil](https://github.com/okfn/mcp-dados-brasil) | Datasets do portal de dados abertos do Brasil (dados.gov.br). Em português. |

!!! note "mcp-datos-uruguay foi aposentado"
    O repo original `mcp-datos-uruguay` tentou cobrir o portal inteiro
    do Uruguai e ficou geral demais. Ele não está mais em uso; o
    `mcp-datos-uruguay-ben`, mais focado, o substituiu. Veja [por que
    restringimos o escopo dos plugins](../lessons/scope.md).

## Peças opcionais

| Repo | O que é |
|------|------------|
| mcp-deployment | Configuração de Docker Compose + Caddy usada para rodar a instância pública em mcp.okfn.org. Repo privado: é a nossa própria infraestrutura, então não está disponível publicamente. Se você precisar de ajuda para implantar sua própria instância, entre em contato conosco. |
| [mcp-docs](https://github.com/okfn/mcp-docs) | Esta documentação. |

!!! tip "Qual repo eu mexo?"
    Adicionar um dataset para um país existente: o repo do plugin do país.
    Adicionar um país novo: um repo de plugin novo (veja [plugins](../plugins/index.md)).
    Mudar como as ferramentas funcionam para todo mundo: `mcp-server`.
