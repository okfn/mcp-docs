# Describe your plugin

Chat clients show a landing card per plugin: a subtitle and a set of
clickable sample questions that pre-fill the chat input. A plugin that
describes itself well is a plugin people actually try.

Call `registry.set_plugin_info()` at the top of `register_tools()`,
**before** declaring any tool, so every tool picks up the metadata:

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

Both fields are optional:

- `description` becomes the plugin card subtitle.
- `sample_questions` become the clickable chips. Write them in the
  language of your users, and pick questions your tools can genuinely
  answer well.

Repository links (homepage, issues) are read from the `[project.urls]`
table of your `pyproject.toml`; no need to repeat them here.
