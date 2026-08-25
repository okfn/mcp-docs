# Use cases

The platform includes two live reference plugins in production. Each is
maintained in its own repository, in its native language, and serves as
an official blueprint for building new domain plugins.

## Uruguay: National Energy Balance

[mcp-datos-uruguay-ben](https://github.com/okfn/mcp-datos-uruguay-ben)

- **Source data:** energy balance figures from
  [catalogodatos.gub.uy](https://catalogodatos.gub.uy/) (Spanish).
- **Technical highlights:** domain-specific Python tools, custom
  parameter filters, and injected domain glossaries for specialized
  energy terminology.
- **Best used as:** template for complex datasets requiring custom
  Python logic and term definitions.

## Brazil: parliamentary amendments

[mcp-dados-brasil](https://github.com/okfn/mcp-dados-brasil)

- **Source data:** high-demand budget allocation data from
  [dados.gov.br](https://dados.gov.br) (Portuguese).
- **Technical highlights:** querying high-frequency financial records
  and handling informal user terminology ("emendas pix") via term
  mappings.
- **Best used as:** template for tracking structured financial
  allocations and public expenditure.

## Development status

Both implementations are currently in **Alpha**. Developers starting a
new country or domain plugin should fork one of these repositories as a
starting baseline: see [building plugins](../plugins/index.md).
