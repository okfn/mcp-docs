# Describir tu plugin

Los clientes de chat muestran una tarjeta de presentación por plugin:
un subtítulo y un conjunto de preguntas de ejemplo clicables que
pre-completan el campo de chat. Un plugin que se describe bien es un
plugin que la gente realmente prueba.

Llama a `registry.set_plugin_info()` al principio de
`register_tools()`, **antes** de declarar cualquier herramienta, para
que todas las herramientas tomen los metadatos:

```python
def register_tools(registry):

    registry.set_plugin_info(
        description=(
            "Tools over Example Org's open data. "
            "Public procurement, budgets, and beneficiary lists."
        ),
        sample_questions=[
            "Which companies sell medicine to the government?",
            "Top 10 recipients of parliamentary amendments",
        ],
    )

    @registry.tool()
    def my_first_tool() -> DataToolOutput:
        ...
```

Ambos campos son opcionales:

- `description` se convierte en el subtítulo de la tarjeta del plugin.
- `sample_questions` se convierten en los chips clicables. Escríbelas
  en el idioma de tus usuarios, y elige preguntas que tus herramientas
  realmente puedan responder bien.

Los enlaces del repositorio (homepage, issues) se leen de la tabla
`[project.urls]` de tu `pyproject.toml`; no hace falta repetirlos aquí.
