# Lessons from the pilot

In July 2026 we ran a public pilot of the platform over Uruguay's energy
data, at [mcp-uruguay.okfn.org](https://mcp-uruguay.okfn.org/). The data
came from Uruguay's *Balance Energetico Nacional* (BEN, the national
energy balance), and real users, including domain experts, tested it and
sent structured feedback.

This section consolidates what we learned. It is written for anyone
building or running a similar deployment: the things that worked, the
things that did not, and what we changed along the way.

!!! note "Read this as field notes, not a verdict"
    The feedback arrived while we were still deploying new versions, so
    it is not strictly feedback about a finished product. Several of the
    problems described here were already fixed by changes shipped during
    the pilot. Where that is the case, the page says so.

## The short version

The overall experience was positive. The pattern users valued most was
the combination of **human-authored tables and charts injected next to
the AI's final answer**: the prose comes from the model, but the numbers
and their sources come straight from the data. The more expert the user
and the better they knew the datasets, the more small things they found
to improve, which is exactly the kind of feedback we wanted.

A concrete example of impact: Wikimedians used the tool to improve the
Wikipedia article on solar energy in Uruguay. It is a great use case,
and a reminder that a tool this fluent could also be misused with the
best of intentions, so verification matters.

## What we learned, by topic

- [Scope plugins narrowly](scope.md): why we split the broad Uruguay
  repo into a focused, domain-specific one.
- [Reliability of calculations](calculations.md): where wrong numbers
  can slip in, and how to prevent it.
- [Transparency and trust](transparency.md): the model mixing its own
  knowledge with the data, and why you should always re-ask.
- [Data quality and openness](data-quality.md): the pilot as an
  incentive to open well-documented data.
- [New tools, old problems](data-access.md): the data-governance
  questions that connecting AI does not let you skip.
- [Testing is not simple](testing.md): why checking answers takes time
  and domain knowledge.
- [A domain glossary](glossary.md): official definitions, injected into
  the tools' context.
- [Open data resources](resources.md): pointing users to the raw data
  beyond our tool.
- [Tables and charts](presentation.md): too many, and what we did about
  it.
- [No accounts, no database](no-database.md): the cost and benefit of
  staying simple.
- [Strengths and weaknesses](summary.md): the consolidated balance
  sheet.
