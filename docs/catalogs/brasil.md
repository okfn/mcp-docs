# Brasil

**Repo:** [okfn/mcp-dados-brasil](https://github.com/okfn/mcp-dados-brasil)
&middot; **Portal:** [dados.gov.br](https://dados.gov.br)
&middot; **Language:** Portuguese

Dataset definitions for Brasil's national open data portal. Each
`.yaml` file under `datasets/` declares a dataset and its tools; the
repo also contains Python tools for more elaborate cases.

## From the field

This catalog backed a pilot with Brasil's Office of the Comptroller
General, focused on **parliamentary amendments**, one of the most
requested datasets on the portal. The goal was to test whether citizens
could ask in natural language and get answers traceable back to official
data. See [lessons from the pilots](../lessons/index.md).

## Adding a dataset

Follow the general [YAML datasets](../plugins/yaml-datasets.md) guide:
one new `.yaml` file in `datasets/`, push, and re-fetch on the server.
Descriptions, parameters and sample questions are written in
Portuguese, matching the audience.
