# Casos de uso

A plataforma inclui dois plugins de referência ativos em produção.
Cada um é mantido em seu próprio repositório, em seu idioma nativo, e
serve como modelo oficial para construir novos plugins de domínio.

## Uruguai: Balanço Energético Nacional

[mcp-datos-uruguay-ben](https://github.com/okfn/mcp-datos-uruguay-ben)

- **Dados de origem:** cifras do balanço energético de
  [catalogodatos.gub.uy](https://catalogodatos.gub.uy/) (espanhol).
- **Destaques técnicos:** ferramentas Python específicas do domínio,
  filtros de parâmetros personalizados e glossários de domínio
  injetados para a terminologia especializada de energia.
- **Melhor uso:** modelo para datasets complexos que exigem lógica
  Python personalizada e definições de termos.

## Brasil: emendas parlamentares

[mcp-dados-brasil](https://github.com/okfn/mcp-dados-brasil)

- **Dados de origem:** dados de alocação orçamentária de alta demanda
  de [dados.gov.br](https://dados.gov.br) (português).
- **Destaques técnicos:** consulta de registros financeiros de alta
  frequência e tratamento da terminologia informal dos usuários
  ("emendas pix") via mapeamentos de termos.
- **Melhor uso:** modelo para acompanhar alocações financeiras
  estruturadas e despesas públicas.

## Estado de desenvolvimento

As duas implementações estão atualmente em **Alpha**. Desenvolvedores
começando um novo plugin de país ou domínio devem fazer fork de um
desses repositórios como base de partida: veja
[construir plugins](../plugins/index.md).
