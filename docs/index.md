# OKFN MCP Platform

**Answer questions with open data, not with AI guesses.**

This is the documentation for the OKFN MCP platform: a small family of
free software projects that let people ask questions in plain language
(English, Spanish, Portuguese...) and get answers computed from official
open data sources, with every answer linking back to the original data.

It is built as part of the Open Knowledge Foundation's
[AI Learning Labs](https://okfn.org/en/projects/ai-learning-labs/mcp-open-government-data/),
which turn real-world pilots into open, replicable methods for
responsible AI. Two goals sit at the centre of the design:

- **Accuracy**: the answers should be correct, computed from the data.
- **Traceability**: every answer should link back to its source, so it
  can be verified.

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

## Why

!!! tagline "The core idea"
    Large language models are great at conversation and terrible at
    facts. Open data portals are great at facts and terrible at
    conversation.

This platform connects the two, and it aims for a clear goal: the AI
should answer from real datasets rather than its own memory, calling
tools that read the data and carrying the sources with every response.
Put simply: **we do not want the AI to know the answer, we want it to
retrieve, explain and cite the data for the answer.**

We have not fully reached that goal, but along the way we built
something genuinely useful, a tool worth using with care. What we
learned trying to get there is written up in
[lessons from the pilots](lessons/index.md).

## What is in the box

- An **MCP server** that turns open datasets (CSV files, databases) into
  tools an AI can call.
- A **chat gateway**, a simple web chat that connects any OpenAI-compatible
  LLM to the MCP server. It renders the tables, charts and source links
  straight from the data, without routing them through the AI, so those
  numbers are exactly what the tools computed.
- **Plugins** scoped to a focused data domain (Uruguay's energy balance,
  Brasil, and yours next) that describe datasets and the questions they
  can answer.

## Where to go next

- New here? Start with [the idea](overview/idea.md).
- Want to run it? Go to [getting started](getting-started/index.md).
- Want to add your country's data? Read [plugins](plugins/index.md).

!!! note "Early days"
    The whole platform is in an early research phase. Breaking changes
    are expected, and so is this documentation changing under your feet.
