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
domain experts, and real-world user feedback. Until the Field Guide is
published, see [lessons from the pilots](lessons/index.md).

For more information, please visit the official project page
"Traceable AI Answers for Public Data" at the
[Open Knowledge Foundation (OKFN) website](https://okfn.org/en/projects/ai-learning-labs/mcp-open-government-data/).

## Watch the talk

We presented this work as *IA Trazable para datos publicos: un modelo
abierto para America Latina* (Traceable AI for public data: an open
model for Latin America) at the UN Big Data Regional Hub in Brazil,
hosted by CEPAL, in June 2026, by Patricio Del Boca (technical lead)
and Andres Vazquez (senior developer).

<div class="video">
  <iframe src="https://www.youtube-nocookie.com/embed/9QBr7kWAcdI"
          title="IA Trazable para datos publicos: un modelo abierto para America Latina"
          style="width: 100%; aspect-ratio: 16 / 9; border: 0;"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
          allowfullscreen></iframe>
</div>

The talk covers the core challenge (why LLMs alone cannot be trusted
with public data), the open model behind our answer, a live demo of the
Uruguay case, and what we learned. This documentation is the written,
extended version of that same view.

The [CEPAL event page](https://rtc-cea.cepal.org/es/evento/videoconferencia-sobre-ia-trazable-para-datos-publicos-un-modelo-abierto-para-america-latina)
has more about the session, including a PDF of the presentation slides.

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
