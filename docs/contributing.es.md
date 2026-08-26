# Contribuir

## Contribuir al código

El desarrollo ocurre en abierto, un repo de GitHub por componente:
[mcp-server](https://github.com/okfn/mcp-server) y
[mcp-chat-gateway](https://github.com/okfn/mcp-chat-gateway). Los
issues y pull requests son bienvenidos en ambos.

El flujo de trabajo es el mismo en todos lados: clona, `uv sync`, haz
tu cambio y corre los tests con `uv run pytest` antes de abrir un PR.
Ten en cuenta que la plataforma está en una fase temprana de
investigación, así que abre primero un issue para cualquier cosa más
grande que un fix.

Si lo que quieres contribuir es un nuevo dataset o país, eso no es un
cambio a estos repos: escribe en cambio tu propio plugin en su propio
repo, empezando por [construir plugins](plugins/index.md).

## Contribuir a esta documentación

Este sitio es Markdown plano construido con
[MkDocs](https://www.mkdocs.org/) y el tema
[Material](https://squidfunk.github.io/mkdocs-material/), alojado en
GitHub Pages. Cada página tiene un ícono de edición (lápiz) que te
lleva directo al archivo en GitHub.

### Trabajar en local

```bash
git clone https://github.com/okfn/mcp-docs
cd mcp-docs
uv sync
uv run mkdocs serve    # live preview at http://127.0.0.1:8000
```

El sitio se reconstruye automáticamente al guardar. Hacer push a `main`
lo publica mediante un workflow de GitHub Actions.

### Reglas de la casa

- **Archivos chicos.** Un tema por página, páginas de una o dos
  pantallas. Si una página crece más que eso, divídela. Los archivos
  chicos también permiten que la gente edite en paralelo sin conflictos
  de merge.
- **Primero lo humano.** Esto es un manual, no una referencia de API.
  Explica el porqué antes del cómo; los bloques de código acompañan al
  texto, no al revés.
- **Puntuación simple.** Comillas rectas, guiones simples, tres puntos.
  Sin Unicode tipográfico, sin emojis decorativos.
- **Las capturas de pantalla** viven en `docs/assets/images/`.
  Comprímelas cuando puedas.
- Las páginas nuevas deben agregarse a la sección `nav` de
  `mkdocs.yml`, o se construirán pero no aparecerán en la navegación.
