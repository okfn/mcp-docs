# Conectar um plugin a um servidor

Conectar um plugin é simplesmente instalá-lo no ambiente do servidor.
Na inicialização o servidor varre todos os pacotes instalados e
registra suas ferramentas:

```bash
uv pip install "git+https://github.com/okfn/mcp-server"
uv pip install "git+https://github.com/okfn/mcp-exampleplugin"
uv run mcp-server
```

Os plugins em Python são descobertos através do seu entry point
`mcp_server`. Pacotes chamados `mcp_server_*` que carregam [datasets em
YAML](yaml-datasets.md) são descobertos por convenção de nome.

Para um repo de plugin privado, instale a partir de uma URL git que o
seu ambiente consiga alcançar, por exemplo via SSH com uma deploy key
somente leitura.

É assim também que funciona a [implantação em
produção](../operations/deployment.md): a imagem do servidor instala os
pacotes dos plugins na hora do build.

## Depois de alterar um plugin

Faça push para o repo do plugin, e então reinstale o pacote e reinicie
o servidor. As ferramentas são carregadas uma única vez, na
inicialização.
