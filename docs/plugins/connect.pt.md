# Conectar a um servidor

Há duas maneiras de levar as ferramentas de um plugin a um servidor em
execução.

## Opção 1: pip install (plugins em Python)

O servidor varre todos os pacotes Python instalados em busca de entry
points `mcp_server` na inicialização. Então conectar um plugin é
simplesmente instalá-lo no mesmo ambiente:

```bash
uv pip install "git+https://github.com/okfn/mcp-server"
uv pip install "git+https://github.com/okfn/mcp-exampleplugin"
uv run mcp-server
```

## Opção 2: tool sources (repos de YAML)

Para repos de datasets declarativos em YAML, liste-os no arquivo
`deploy/tool_sources.yaml` do servidor. O servidor os clona e carrega
os arquivos YAML a partir do caminho indicado:

```yaml
- name: mcp-dados-brasil
  repo: git@github.com:okfn/mcp-dados-brasil.git
  path: datasets     # folder inside the repo where the tools live
  ref: main
```

### Repos privados

Se o repo for privado, adicione uma deploy key somente leitura:

```yaml
  key: deploy/keys/mcp-dados-brasil-key
```

Gere o par de chaves, envie a metade pública para as deploy keys do
repo no GitHub (acesso de leitura é suficiente), e coloque o arquivo
privado no servidor com permissões `600`:

```bash
ssh-keygen -t ed25519 -f keys/mcp-dados-brasil-key -N "" -C "deploy@mcp-server"
```

## Depois de alterar um plugin

Faça push para o repo do plugin, e então busque as mudanças / reinicie
no servidor. As ferramentas são carregadas uma única vez, na
inicialização.
