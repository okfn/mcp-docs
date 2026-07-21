# The idea

Governments and organizations publish enormous amounts of open data:
budgets, procurement, prices, health statistics. Very few people use it,
because using it requires downloading files, understanding schemas and
writing code.

At the same time, people already ask AI chatbots these questions, and
the chatbots answer from memory: outdated, unverifiable, sometimes
invented.

## Our answer

We put a layer between the AI and the user:

1. The user asks a question in their own language.
2. Instead of answering from memory, the AI is steered to call a
   **tool**: a small, named operation like "average price of a product
   by year" backed by a real dataset.
3. The tool computes the answer from the data and returns it together
   with the **source**: a link to the original dataset.
4. The chat shows the AI's written answer, plus tables, charts and the
   sources, so anyone can verify it.

!!! important "Tables and charts come from code, not from the AI"
    A tool returns two things: a short text for the AI to read, and a
    structured payload (tables, charts, sources) for the interface.
    Only the text ever reaches the model. **The tables and charts are
    built by human-written tool functions and rendered directly by the
    interface, bypassing the AI completely.** The AI writes the prose;
    the data speaks for itself beside it.

The verifiable tables and source links next to its words are not a nice
extra; they are the safeguard. See [lessons from the
pilots](../lessons/index.md).

The deeper reasoning for why a bare LLM is not enough is on
[the challenge](challenges.md) page.

## Principles

- **Accuracy and traceability.** Answers should be correct, computed
  from the data, and every answer should point to its source. The
  server [enforces this in
  code](../plugins/tool-results.md#how-it-is-enforced).
- **Plain code over a bespoke language.** Tools are mostly small Python
  functions. Really simple datasets can instead be declared in YAML with
  no code, but we keep that for the simple cases: see [the YAML
  trade-off](../lessons/yaml-tradeoff.md).
- **Free software, boring technology.** Python, CSV, SQLite, plain
  HTML and JS. Everything can run on a laptop.
- **Local ownership.** Each community or domain team maintains its own
  plugin repo, in its own language, at its own pace.

## The standard underneath

The AI-to-tools connection uses the
[Model Context Protocol](https://modelcontextprotocol.io/) (MCP), an
open standard. That means our server works not only with our chat
gateway but with any MCP-capable client (Claude Desktop, VS Code,
MCP Inspector, and others).
