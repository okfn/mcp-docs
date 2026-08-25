# Implementing domain glossaries

Public datasets often rely on domain-specific administrative terms,
legal taxonomy or specialized units (such as energy balance figures or
budget codes) that non-experts, and general LLMs, may misinterpret.

To ensure accurate responses, plugins should include a **domain
glossary** that injects official term definitions directly into the
tool context. In the Uruguay pilot, injecting the official energy
balance (BEN) definitions turned out to be essential for non-expert
users, and it measurably improved the answers.

## How glossary injection works

Glossary definitions serve a dual purpose in the MCP architecture:

1. **LLM context injection.** Terms and definitions are included in the
   tool's system prompt or description. When the LLM receives data
   results, it uses these definitions to interpret raw figures and
   write accurate prose.
2. **User clarity.** Terms can be exposed directly in the interface so
   users can consult official definitions alongside their query
   results.

## Implementation guidelines

- **Map terms to specific tools.** Avoid dumping an entire portal
  dictionary into every prompt. Manually curate and attach only the
  relevant terms to the specific tool that uses them. This conserves
  context window space and prevents prompt confusion. The mapping is
  manual and a little tedious, but the payoff, clearer answers and
  fewer misunderstandings, makes it worth the effort.
- **Bridge everyday language and bureaucratic terms.** Include alias
  mappings in your tool descriptions, for example mapping informal user
  terms like "pix" or "fuel tax" to their official administrative
  category names in the dataset. Without this bridge, the AI can report
  that data is missing simply because the user did not know the exact
  bureaucratic phrase.
- **Treat glossaries as code.** Budget development time for glossary
  mapping during plugin creation. Defining terminology is a core
  technical requirement for retrieval accuracy, not post-launch
  documentation polish.
