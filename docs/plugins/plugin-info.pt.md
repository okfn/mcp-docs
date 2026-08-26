# Descrever seu plugin

Os clientes de chat mostram um cartão de apresentação por plugin: um
subtítulo e um conjunto de perguntas de exemplo clicáveis que
preenchem o campo do chat. Um plugin que se descreve bem é um plugin
que as pessoas realmente experimentam.

Chame `registry.set_plugin_info()` no início de `register_tools()`,
**antes** de declarar qualquer ferramenta, para que todas as
ferramentas recebam os metadados:

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

Os dois campos são opcionais:

- `description` vira o subtítulo do cartão do plugin.
- `sample_questions` viram os chips clicáveis. Escreva-as no idioma
  dos seus usuários, e escolha perguntas que suas ferramentas realmente
  consigam responder bem.

Os links do repositório (homepage, issues) são lidos da tabela
`[project.urls]` do seu `pyproject.toml`; não é preciso repeti-los
aqui.
