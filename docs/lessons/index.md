# Lessons from the pilots

We tested the same architecture in **two government pilots**, in Brasil
and in Uruguay: see [two pilots](two-pilots.md) for who, how, and what
we set out to learn. The Uruguay pilot, which ran publicly at
[mcp-uruguay.okfn.org](https://mcp-uruguay.okfn.org/), produced the most
detailed feedback, so most concrete examples come from there.

This section is written for anyone building or running a similar
deployment: what worked, what did not, and what we changed along the
way.

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

- [Two pilots](two-pilots.md): who we tested with, how, and
  what we set out to learn.
- [Connecting the data is the easy part](meaning.md): access is not
  understanding, and meaning is where the work is.
- [Scope plugins narrowly](scope.md): why we split the broad Uruguay
  repo into a focused, domain-specific one.
- [The YAML trade-off](yaml-tradeoff.md): why declaring datasets in YAML
  is a good idea only for really simple cases.
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
