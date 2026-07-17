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
    This is a defining choice of the project. A tool returns two things:
    a short text for the AI to read, and a structured payload (tables,
    charts, sources) for the interface. Only the text ever reaches the
    model. **The tables and charts are built by human-written tool
    functions and rendered directly by the interface, bypassing the AI
    completely.** So the numbers you see in a table are exactly what the
    tool computed from the data, never something the model formatted,
    rounded or invented. The AI writes the prose; the data speaks for
    itself in the tables and charts beside it.

This is the intended flow, and it is what the design pushes toward. In
practice the model can still slip its own knowledge into the prose, so
the mix of a verifiable table next to the AI's words, plus the source
links, is not a nice extra but the safeguard that makes the whole thing
trustworthy. See [lessons from the pilot](../lessons/index.md).

The deeper reasoning for why a bare LLM is not enough is on
[the challenge](challenges.md) page.

## Principles

- **Accuracy and traceability.** The two goals everything is measured
  against: answers should be correct (computed from the data) and every
  answer should point to its source. A tool that cannot cite a source
  does not get registered. See [the open model](open-model.md).
- **Declarative where possible.** Most datasets can be described in a
  small YAML file: no programming needed to add a new dataset.
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

!!! note "These principles were tested in the field"
    A July 2026 pilot over Uruguay's energy data put all of this to the
    test with real users. One finding stands out and is worth carrying
    into every answer: the model sounds equally confident whether or not
    it has the data to back it up, so the traceability above is not a
    nicety, it is what lets users verify instead of trust the tone. See
    [lessons from the pilot](../lessons/index.md).
