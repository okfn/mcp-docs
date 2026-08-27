# MCP Technical Documentation

Welcome to the MCP Technical Documentation: a practical guide to
connecting open public data to AI models using the Model Context
Protocol (MCP).

This manual provides the architecture specifications, code patterns and
configuration templates needed to build plugins, run the server and
deploy data tools.

Everything here is measured against two goals: **accuracy** (answers
computed from official data, not recalled from training) and
**traceability** (every answer links back to its source). The
[project context](introduction/context.md) explains both and why they
matter for public data.

**Looking for non-technical context or project strategy?** Check out
the *Field Guide to Connecting AI to Public Information*. It covers
lessons from our Brazil and Uruguay pilots, guidance on working with
domain experts, and real-world user feedback.

For more information, please visit the official project page
"Traceable AI Answers for Public Data" at the
[Open Knowledge Foundation (OKFN) website](https://okfn.org/en/projects/ai-learning-labs/mcp-open-government-data/).

## What is in the box

- An **MCP server** that turns open datasets (CSV files, databases) into
  tools an AI can call.
- A **chat gateway**, a simple web chat that connects any OpenAI-compatible
  LLM to the MCP server and renders tables, charts and source links
  straight from the data, [without routing them through the
  AI](dev/architecture.md).
- **Plugins** scoped to a focused data domain (Uruguay's energy balance,
  Brasil, and yours next) that describe datasets and the questions they
  can answer.

## Where to go next

- New here? Start with the [project context](introduction/context.md).
- Want to run it? Go to [getting started](getting-started/index.md).
- Want to add your country's data? Read [plugins](plugins/index.md).

!!! note "Early days"
    The whole platform is in an early research phase. Breaking changes
    are expected, and so is this documentation changing under your feet.
