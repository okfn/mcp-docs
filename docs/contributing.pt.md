# Contribuir

## Contribuindo com o código

O desenvolvimento acontece em aberto, um repo do GitHub por
componente: [mcp-server](https://github.com/okfn/mcp-server) e
[mcp-chat-gateway](https://github.com/okfn/mcp-chat-gateway). Issues e
pull requests são bem-vindos nos dois.

O fluxo de trabalho é o mesmo em todo lugar: clone, `uv sync`, faça
sua mudança e rode os testes com `uv run pytest` antes de abrir um PR.
Tenha em mente que a plataforma está em uma fase inicial de pesquisa,
então abra uma issue primeiro para qualquer coisa maior que uma
correção.

Se o que você quer contribuir é um novo dataset ou país, isso não é
uma mudança nesses repos: escreva seu próprio plugin no seu próprio
repo, começando por [construindo plugins](plugins/index.md).

## Contribuindo com esta documentação

Este site é Markdown puro construído com
[MkDocs](https://www.mkdocs.org/) e o tema
[Material](https://squidfunk.github.io/mkdocs-material/), hospedado no
GitHub Pages. Cada página tem um ícone de edição (lápis) que leva você
direto ao arquivo no GitHub.

### Trabalhando localmente

```bash
git clone https://github.com/okfn/mcp-docs
cd mcp-docs
uv sync
uv run mkdocs serve    # live preview at http://127.0.0.1:8000
```

O site é reconstruído automaticamente quando você salva. Fazer push
para `main` publica o site por meio de um workflow do GitHub Actions.

### Regras da casa

- **Arquivos pequenos.** Um tópico por página, páginas de uma ou duas
  telas. Se uma página crescer além disso, divida-a. Arquivos pequenos
  também permitem que as pessoas editem em paralelo sem conflitos de
  merge.
- **Humano primeiro.** Isto é um manual, não uma referência de API.
  Explique o porquê antes do como; os blocos de código apoiam o texto,
  não o contrário.
- **Pontuação simples.** Aspas retas, hífens simples, três pontos. Sem
  Unicode tipográfico, sem emojis decorativos.
- **As capturas de tela** ficam em `docs/assets/images/`. Comprima-as
  quando puder.
- Páginas novas precisam ser adicionadas à seção `nav` do
  `mkdocs.yml`, ou serão construídas mas não aparecerão na navegação.
