# Project context

**Connecting AI to public open data.**

Public open data is essential for transparency, accountability and
informed decision-making. However, extracting answers from official
portals often requires navigating complex interfaces, writing technical
queries and spending significant time interpreting raw files.

Integrating AI allows users to query data using natural language, but
standard AI models also introduce a major risk: hallucinations,
miscalculated figures and plausible-sounding errors that undermine
trust in official information.

To solve this, the Open Knowledge Foundation's
[AI Learning Labs](https://okfn.org/en/projects/ai-learning-labs/mcp-open-government-data/)
built an open technical bridge using the Model Context Protocol (MCP).
We tested this approach across two live public datasets:

- **Brazil**: parliamentary amendments (tracking public funds).
- **Uruguay**: National Energy Balance (monitoring the energy
  transition).

## Core technical principles

- **Accuracy and traceability.** Answers must be grounded strictly in
  official datasets, and every response must link to its source. The
  server enforces this rule in code.
- **Plain code over custom languages.** Tools are written as small,
  standard Python functions. Simple datasets can be declared in YAML
  without writing code.
- **Simple and proven tech stack.** Built on open-source, standard,
  reliable technologies (Python, CSV, SQLite, plain HTML/JS). The
  entire system can run locally on a laptop without complex
  infrastructure.
- **Local ownership.** Each team maintains its own plugin repository
  independently, using their preferred language and release schedule.
