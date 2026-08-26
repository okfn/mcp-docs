# Por que MCP? Um modelo aberto para dados públicos

O [Model Context Protocol](https://modelcontextprotocol.io/) (MCP) é
um padrão aberto, introduzido pela Anthropic no final de 2024 e desde
então adotado em toda a indústria de IA, que define como aplicações de
IA se conectam a dados e ferramentas externos. Um **cliente** MCP (uma
interface de chat, uma IDE, um assistente de desktop) fala com um
**servidor** MCP, que expõe **ferramentas** que o modelo pode invocar,
**recursos** que o cliente pode ler e **prompts**, por dois
transportes padrão: stdio (local) e HTTP (rede). A especificação e os
SDKs são mantidos abertamente em
[modelcontextprotocol.io](https://modelcontextprotocol.io/).

Esta plataforma é uma aplicação direta do padrão: os datasets são
expostos como ferramentas e recursos MCP, o servidor fala os dois
transportes, e qualquer cliente compatível com MCP (Claude Desktop,
VS Code, MCP Inspector, nosso chat gateway) pode se conectar a ela sem
mudanças. Veja a página de [arquitetura](../dev/architecture.md) para
entender como as chamadas do protocolo se encaixam no ciclo de
execução e onde somos mais rigorosos que o padrão (o contrato de
fontes).

## Por que o escolhemos

- **Padronização e design plug-and-play.** As boas práticas estão
  embutidas na arquitetura do servidor; novas fontes de dados se
  conectam a partir de templates sem reconstruir a interface de IA.
- **Framework aberto e replicável.** Totalmente código aberto,
  protocolo incluído: sem dependência de fornecedor, sem
  "caixa-preta".
- **Autonomia local comprovada.** Durante os pilotos, técnicos dos
  parceiros construíram um servidor MCP sobre uma nova fonte de dados
  sem que ninguém pedisse.
- **Um kit de ferramentas reutilizável em crescimento.** Um novo
  assistente de dados começa de um template em vez de do zero, mais
  fácil de adotar por equipes técnicas menos experientes.
