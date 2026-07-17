# Contributing to these docs

This site is plain Markdown built with
[MkDocs](https://www.mkdocs.org/) and the
[Material](https://squidfunk.github.io/mkdocs-material/) theme, hosted
on GitHub Pages. Every page has an edit (pencil) icon that takes you
straight to the file on GitHub.

## Working locally

```bash
git clone https://github.com/okfn/mcp-docs
cd mcp-docs
uv sync
uv run mkdocs serve    # live preview at http://127.0.0.1:8000
```

The site rebuilds automatically as you save. Pushing to `main`
publishes it through a GitHub Actions workflow.

## House rules

- **Small files.** One topic per page, pages of a screen or two. If a
  page grows past that, split it. Small files also mean people can
  edit in parallel without merge conflicts.
- **Human first.** This is a manual, not API reference. Explain the
  why before the how; code blocks support the text, not the other way
  around.
- **Plain punctuation.** Straight quotes, plain hyphens, three dots.
  No typographic Unicode, no decorative emoji.
- **Screenshots** live in `docs/assets/images/`. Compress them when
  you can.
- New pages must be added to the `nav` section of `mkdocs.yml`, or
  they will build but not appear in the navigation.
